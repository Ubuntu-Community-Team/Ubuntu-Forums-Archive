---
title: "downloading game to ubuntu"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by dougil on 2011-04-23
I'm having trouble downloading backgammonmasters off of the internet.  I didnt have a problem with windows.  How can I get the game to download off of ubuntu?

---

### Post by migs73 on 2011-04-23
The download is a .exe file for running in windows.
It will not work natively in Linux.There is a program called Wine in the Ubuntu Software Centre (Applications-> Ubuntu software Centre) that provides a compatabilty layer in Linux to allow some Windows programs to run.
Check at their website to see if it is supported (If new to this I wouldn't try anything less than Gold rated)

[http://www.winehq.org/](http://www.winehq.org/)

If all that seems a bit too much there is a Backgammon Game in the USC you could try instead!

Regards

Mike

---

### Post by Jgke on 2011-04-23
Backgammonmasters seems to be a Windows program, so you have to use Wine for it.
Open a terminal window and input the following line:
```
sudo apt-get install wine1.2
```
(it asks your password)
Then, download the file to your desktop.
On the terminal window, say
```
cd /home/yourusername/Desktop
wine backgammonmasters.exe
```
Then the installation should start.

---

