# dictionary.py
def new_game():
    guesses = []
    correct_guess_count = 0
    question_num = 1

    for key in questions:
        print("-------------------------")
        print(key)

        guess = input("Enter (T/F/t/f): ")
        guess = guess.upper()
        guesses.append(guess)

        correct_guess_count += verify_answer(questions.get(key), guess)
  #      question_num += 1

    display_score(correct_guess_count, guesses)


def verify_answer(answer, guess):
    if answer == guess:
        print("You guessed correct!")
        return 1
    else:
        print("You guessed wrong...")
        return 0


def display_score(correct_guess_count, guesses):
# function to display score
    print("-------------------------")
    print("RESULTS")
    print("-------------------------")

    print("Answers: ", end="")
    for i in questions:
        print(questions.get(i), end=" ")
    print()

    print("Guesses: ", end="")
    for i in guesses:
        print(i, end=" ")
    print()

    score = int((correct_guess_count/len(questions))*100)
    print("Your score is: "+str(score)+"%")


def play_again():
# if user wants to play again, return True
    response = input("Do you want to play again? (yes or no): ")
    response = response.upper()

    if response == "YES":
        return True
    else:
        return False

# Dictionary for questions
questions = {
    "2 + 2 = 17": "F",
    "Cars have four wheels ": "T",
    "India became independent in 2020 ": "F",
    "The Earth is flat ": "F",
    "Sharks are mammals": "F",
    "India is the largest democracy in the world": "T",
    "The national sport of India is Cricket": "F",
    "Python uses a compiler to run": "F",
    "China has the largest coastline": "F",
    "Ants carry 1000 times their own weight": "F",
}


new_game()
while play_again():  # if play_again() returns true, execute this
    new_game()
print("Thank you for playing!")
