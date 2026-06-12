---
title: "how to exit terminal"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-18
hi.. i want to know how to exit the terminal after issuing certain commands..
for example, i wanted to enable apport so i wrote the followimg line in terminal
sudo nano /etc/default/apport

now, i want to change the value from 0 to 1 to enable the same..

 i did the same.. after this step.. i am not finding a way to save and exit the terminal.. please help.. thank you

---

### Post by 73ckn797 on 2009-01-18
> **chethankrish said:**
> hi.. i want to know how to exit the terminal after issuing certain commands..
for example, i wanted to enable apport so i wrote the followimg line in terminal
sudo nano /etc/default/apport

now, i want to change the value from 0 to 1 to enable the same..

 i did the same.. after this step.. i am not finding a way to save and exit the terminal.. please help.. thank you


Either just close it or type exit.

To make the change you desire, cursor to that point and make change then "control + X" then answer yes or no to saving changes.

---

### Post by chethankrish on 2009-01-18
i did the same.. when i close, the value is not getting updated.. its still 0..

when i type exit.. nothing happens.. terminal window stays open..

---

### Post by roshanjose on 2009-01-18
hey when you open something from a terminal....for example an editor....

and when you close the terminal...the pplication you opened through the terminal gets closed along with the terminal...

---

### Post by chethankrish on 2009-01-18
thats wright, but the value is not getting updated.. i typed in 

sudo nano /etc/default/apport

i get the screen as below.. now when i change 0 to 1 next to enabled and close the terminal window..and i open the terminal next time and type "sudo nano /etc/default/apport" ,, the value next to enabled is still 0..
======================================================================================
# set this to 0 to disable apport, or to 1 to enable it
enabled=0

# set maximum core dump file size (default: 209715200 bytes == 200 MB)
maxsize=209715200














                                [ Read 5 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by CLomax on 2009-01-18
CTRL + O. (That's the letter O) to 'writeout' or save the file.

---

### Post by chethankrish on 2009-01-18
hey thanx a lot.. i finally got it...

---

### Post by sisco311 on 2009-01-18
nano is a text editor. you can save the file with Ctrl+o, Enter and exit with Ctrl+x.

or you can use a GUI text editor to edit the file:
```
gksu gedit /etc/default/apport
```

---

### Post by 73ckn797 on 2009-01-18
> **chethankrish said:**
> i did the same.. when i close, the value is not getting updated.. its still 0..

when i type exit.. nothing happens.. terminal window stays open..

When in the apport file, cursor to the place to change 0 to 1, then press "control+X" you will then be able to save changes.
 You will be exited out to terminal and then type exit to exit terminal

See screeshot

---

### Post by mcduck on 2009-01-18
You don't want to exit the terminal after making the changes, you want to exit the **text editor** (nano, in this case). :D

Press Ctrl-X, it will ask you if you wish to save the changes you have made. Press "y", and then it asks where to save the changes. The default is the file you opened in the first place so you can just hit enter. 

Now the changes are saved, and you can close the terminal.

---

### Post by chethankrish on 2009-01-18
thanx a lot for your help.. thank you all... i love ubuntu...

---

