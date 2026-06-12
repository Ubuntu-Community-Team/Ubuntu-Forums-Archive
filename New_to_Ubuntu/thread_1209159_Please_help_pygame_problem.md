---
title: "Please help pygame problem"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by farhanshahid2009 on 2009-07-10
when i load the following lines of code  from  a.py file   

import pygame,sys,os
from pygame.locals import *
dir(pygame)
pygame.init()
window=pygame.display.set_mode((640,480))
pygame.display.set_caption('game')
screen=pygame.display.get_surface()
file1=os.path.join('Desktop','1.gif')
pygame.image.load(file1)
screen.blit=(file1,(0,0)) 
pygame.display.flip() 

the following error message is generated :

open /dev/sequencer: No such file or directory
Traceback (most recent call last):
  File "/home/farhan/Desktop/game.py", line 11, in ?
    screen.blit=(file1,(0,0))
AttributeError: 'pygame.Surface' object attribute 'blit' is read-only

So what do i do PLEASE HELP

---

### Post by lisati on 2009-07-11
[http://ubuntuforums.org/showthread.php?t=1209150](http://ubuntuforums.org/showthread.php?t=1209150)

---

