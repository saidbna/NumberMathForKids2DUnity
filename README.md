import random

def main():
    # إنشاء لوحة اللعبة
    board = [[0 for i in range(3)] for j in range(3)]

    # تحديد اللاعب الأول واللاعب الثاني
    player1 = "X"
    player2 = "O"

    # تبديل اللاعبين
    current_player = player1

    # تشغيل اللعبة
    while True:
        # عرض لوحة اللعبة
        print_board(board)

        # طلب حركة من اللاعب الحالي
        move = get_move(current_player)

        # وضع علامة اللاعب الحالي على اللوحة
        board[move[0]][move[1]] = current_player

        # التحقق من الفائز
        winner = check_winner(board)
        if winner is not None:
            print(f"اللاعب {winner} فاز!")
            break

        # تبديل اللاعبين
        current_player = player1 if current_player == player2 else player2

def print_board(board):
    for row in board:
        print(" ".join(row))

def get_move(player):
    while True:
        move = input(f"لاعب {player} ، ادخل حركتك (1-9): ")
        move = int(move) - 1
        if move >= 0 and move < 9 and board[move // 3][move % 3] == 0:
            return move

def check_winner(board):
    # تحقق من صفوف الأعمدة والمربعات
    for i in range(3):
        if board[i][0] == board[i][1] == board[i][2] != 0:
            return board[i][0]
        if board[0][i] == board[1][i] == board[2][i] != 0:
            return board[0][i]
        if board[i][0] == board[1][1] == board[2][2] != 0:
            return board[i][0]
        if board[2][0] == board[1][1] == board[0][2] != 0:
            return board[2][0]

    return None

if __name__ == "__main__":
    main()

