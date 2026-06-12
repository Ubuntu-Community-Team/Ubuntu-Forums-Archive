---
title: "zip file of game wont play"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by shadowreaper65 on 2011-02-01
i am new to ubuntu and i downloaded a game i normally play from a zip file but now the game will not open as a program to play it im not sure what to do i have it set as open as program but i keep getting an error message do i need any plug ins? the execute as program box does not stay checked either so i dont know how 2 run it as a program.


heres the game is a small download is a 2d game. please let me know if u know what i need to fix this so i can play. Thank you.
[http://www.bones-underground.org/](http://www.bones-underground.org/)

---

### Post by kroq-gar78 on 2011-02-01
Is the game a windows game? If so, install the program "wine" by running a this in a Terminal (Applications -> Accessories -> Terminal):
```
sudo apt-get install wine
```
And then extract everything from the zip file. Right click on the .exe (the file ends in ".exe") and say "Open with WINE" (or something related to WINE)

If you need more help, just post back.
Hope it helps!

---

### Post by shadowreaper65 on 2011-02-01
yes it does thank you so much i dident know i needed extra things to run things. thanks =]

---

