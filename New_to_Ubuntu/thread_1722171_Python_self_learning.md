---
title: "Python self learning"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by hdanap on 2011-04-05
Hi people,

in my self study im doing, not assignment fro school but and exercise in a pyhton book, the question are.


[LIST=1]
[*]Copy catch.py to pong1.py and change the ball into a paddle by using Box instead of the Circle. You can look at Appendix A for more information on Box. Make the adjustments needed to keep the paddle on the screen.
[*]Copy pong1.py to pong2.py. Replace the distance function with a boolean function hit(bx, by, r, px, py, h) that returns True when the vertical coordinate of the ball (by) is between the bottom and top of the paddle, and the horizontal location of the ball (bx) is less than or equal to the radius (r) away from the front of the paddle. Use hit to determine when the ball hits the paddle, and make the ball bounce back in the opposite horizontal direction when hit returns True. Your completed function should pass these doctests:
 def hit(bx, by, r, px, py, h):
    """
      >>> hit(760, 100, 10, 780, 100, 100)
      False
      >>> hit(770, 100, 10, 780, 100, 100)
      True
      >>> hit(770, 200, 10, 780, 100, 100)
      True
      >>> hit(770, 210, 10, 780, 100, 100)
      False
    """

 
 3. Finally, change the scoring logic to give the player a point when the ball goes off the screen on the left.
[/LIST]
======================================

I have figured out everything but i kinda think i cheated in the code i wrote up for the 1st question, the part that instructs keeping the paddle on the screen, mayb im right but i feel there should be a better way to keep the paddle on screen

This is my code for the exercise:

```


from gasp import *

COMPUTER_WINS = 1
PLAYER_WINS = 0
QUIT = -1

def distance(x1, y1, x2, y2):
    return ((x2 - x1)**2 + (y2 - y1)**2)**0.5
    
    
def hit(bx, by, r, px, py, h):
    """
    >>> hit(760, 100, 10, 780, 100, 100)
    False
    >>> hit(770, 100, 10, 780, 100, 100)
    True
    >>> hit(770, 200, 10, 780, 100, 100)
    True
    >>> hit(770, 210, 10, 780, 100, 100)
    False
    """
    if px - bx <= r and by >= py and by <= (py + h):
        return True
    else:
        return False
        
        
        

    
    
def play_round():
    # the ball
    ball_x = 10
    ball_y = 300
    ball = Circle((ball_x, ball_y), 10, filled=True, color=color.BLACK)
    dx = 4
    dy = random_between(-5, 5)
    
    #paddle
    mitt_x = 780
    mitt_y = random_between(20, 290)
    r = 20
    h = 100
    #paddle
    mitt = Box((mitt_x, mitt_y), r, h)  
    
    
    
    
    while True:
        if ball_y > 590 or ball_y < 10:
            dy *= -1
        ball_y += dy
        if ball_x > 810:
            remove_from_screen(ball)
            remove_from_screen(mitt)
            return COMPUTER_WINS
        ball_x += dx
        
        move_to(ball, (ball_x, ball_y))
                
        if key_pressed('k') and mitt_y <= 580:
            mitt_y += 5
        elif key_pressed('j') and mitt_y >= 20:
            mitt_y += -5
        else:
            if key_pressed('o'):
                return QUIT
            
        move_to(mitt, (mitt_x, mitt_y))
            
                   
        # makes the ball bounce back    
        if hit(ball_x, ball_y, r, mitt_x, mitt_y, h):
            dx *= -1
        
        # new scoring logic    
        if ball_x < 10:
            remove_from_screen(ball)
            remove_from_screen(mitt)
            return PLAYER_WINS
                
        update_when('next_tick')
        

def play_game():
    player_score = 0
    computer_score = 0
    
    while True:
        pmsg = Text('Player: %d Points' % player_score, (10, 570), size = 24)
        cmsg = Text('Computer: %d Points' % computer_score, (640, 570), size = 24)
        
        # this is the part i think i cheated, keeping the paddle on screen
        # I think, i should be keeping the paddle on screen in function play_round at the
        # top, but cant seem to do that, is the code right? or is ther something im missing

        mitt_x = 780
        mitt_y = random_between(20, 290)
        r = 20
        h = 100
        #paddle
        mitt = Box((mitt_x, mitt_y), r, h)  
        move_to(mitt, (mitt_x, mitt_y))
        sleep(3)
        remove_from_screen(pmsg)
        remove_from_screen(cmsg)
        remove_from_screen(mitt)
        
        
        result = play_round()
        
        if result == PLAYER_WINS:
            player_score +=1
        elif result == COMPUTER_WINS:
            computer_score += 1
        else:
            return QUIT
            
        if player_score == 5:
            return PLAYER_WINS
        elif computer_score == 5:
            return COMPUTER_WINS
            
            
begin_graphics(800, 600, title='Catch', background=color.YELLOW)

result = play_game()

if result == PLAYER_WINS:
    Text('Player Wins!', (390, 290), size = 24)
else:
    Text('Computer Wins!', (390, 290), size = 24)
    
sleep(5)
end_graphics()    
            

    
    
            
if __name__ == '__main__':
    import doctest
    doctest.testmod()




```

---

### Post by Vaphell on 2011-04-05
when you post snippets of code, put it in [code] tags because python requires precise indentation which is not preserved when pasting code into the message body directly.

---

### Post by hdanap on 2011-04-05
> **Vaphell said:**
> when you post snippets of code, put it in [code] tags because python requires precise indentation which is not preserved when pasting code into the message body directly.


Hi, i always wondered how i could make it look correct, pls can u dirrect me on how to use code tags, not familiar with it

thanks

---

### Post by juancarlospaco on 2011-04-05
[code ]
import antigravity
print ('Bazinga!')
[/code ]

---

