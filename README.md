# Shut-the-box

import random as rand 

def roll():
    total = 0
    for i in range(2):
        total += rand.randint(1,6)
    return total

def maxi_choice(n, set):
    for i in range(len(set)):
        for j in range(i):
            if set[i] + set[j] == n:
                return [set[i], set[j]]
        
def shutthebox():
    set = [1,2,3,4,5,6,7,8,9,10]
    seen = []
    print('Welcome to shut the box')
    print(set)
    
    while sum(set) < 56:
        print(input("Press enter to roll the dice"))
        temp = roll()
        print('You rolled a', temp)
        seen.append(temp)
        
        if temp in set:
            set.remove(temp)
            print(set)
        else:
            temp = maxi_choice(temp, set)
            if temp == None:
                print('END')
                print(set)
                print('Your score is: ', sum(set))
                break
            else:
                set.remove(temp[0])
                set.remove(temp[1])
                print(set)
            
        if seen.count(temp) > 1:
            temp = maxi_choice(temp, set)
            if temp == None:
                print(set)
                print('Your score is: ', sum(set))
                print('END')
                break
                    
                    
        
                
        if set == []:
            print('YOU WIN')
            
        
shutthebox()
