---
title: "Rosetta stone solution I don't know how to do"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by DuckDodgers on 2009-02-07
I am having trouble running rosetta stone with wine.  I found the problem I'm haveing along with a solution that seemed to work for everyone here 

[http://ubuntuforums.org/showthread.php?t=736405](http://ubuntuforums.org/showthread.php?t=736405)

Unfortunatly I don't know how to do this


"ok, to get a successful install of version 3.2 run this script

http://www.kegel.com/wine/winetricks" 

I wen't to the above website and couldn't make heads or tails from it.  I tried just copying and pastine the whole thing in terminal, but that didn't seem to do anything.

---

### Post by Partyboi2 on 2009-02-07
Copy and paste the script from [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) into a text editor like gedit. Then save the file as 'filename.sh' you can change 'filename' to what ever you want to call it.
Then open a terminal and navigate to where you saved the filename.sh script  [FONT=monospace]eg. if filename.sh saved to Desktop
[/FONT]```
 cd ~/Desktop 
```[FONT=monospace] Then change the permissions for the file so you can excute it.
[/FONT]```
chmod +x filename.sh
```then excute
```
./filename.sh
```

---

### Post by DuckDodgers on 2009-02-21
Thank you that seemed to do the trick

---

### Post by barbapapa1 on 2009-03-13
Hi, I have been trying to get RS to run, and ran the script, but now Firefox crashes instantly when I try to launch it(even before I try to run RS.  I have the output from the terminal window from when I ran the script.  Is there anyone still around that can give me a hand.  I didn't just want to post the error log right here.  Also,as a note I am really a beginner at Ubuntu.  Thanks in advance.

---

### Post by BobSongs on 2009-03-18
Here's my Rosetta Stone experience so far.

Installing it fails with the Wine installation.

Then I install WineDoors and add MSXML4. This can also be done with WineTricks.

Then I can install Rosetta Stone and the Language Packs. It can also be activated.

However, the problem arises when I install the update. Then the RS simply will no longer run. It throws an error and then that's the last I see of it.

Seeing this is software that requires dreaded "Activation" the problem is that you cannot keep wiping out your .wine folder and try new tricks every 10 minutes. Though it is legitimate testing, Rosetta may take a dim view of constant phonecalls to reset their software. They may begin to think that a lot of pirating is going on.

The reason I wanted to install the update is because I kept my daughter's database file. She's done a lot of long, tedious work to get to where she is. However, the original version of RS does not recognize the database file (tracking.db3).

If anyone has managed to get the most recent version of Rosetta Stone working correctly in Wine, I for one would like to hear about it.

Thanks.

---

