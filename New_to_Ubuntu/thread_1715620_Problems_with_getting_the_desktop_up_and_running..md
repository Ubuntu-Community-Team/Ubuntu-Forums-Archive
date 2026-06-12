---
title: "Problems with getting the desktop up and running."
date: 2011-03-27
forum: New to Ubuntu
---

### Post by TruePurple on 2011-03-27
Using unetbootin and netinstall option, 10.10 64bit, I installed ubuntu. 

During the installation process it asked what programs I wanted to install, I choose ubuntu desktop upon advice in the ubuntu IRC channel (or at least I thought I did) and it did some downloading and installing stuff. 

Then I restarted my PC, after logging in with my password, it takes me to a command prompt. I was like, where is the desktop? I read something about "0desktop" in the text it showed and typed that. It gave me a command line to type to install "0desktop". I typed that command line and it started to install, whatever. But then someone in IRC said not to install this unknown program, but to try startx. So I used ctrl C(after someone told me of this command) and canceled that installation. Perhaps that interruption of installation caused some bugs?

So I typed startx, it gave me a command list to type, to install xstart. I typed that command and it installed something.  

So now when I type xstart I get a black screen with a white square in the top right corner, and within that white square is a super tiny black prompt. I can not type anything at this command prompt or do anything at this screen or even escape this screen.

"[Go to System/Administration/**Login Screen**, like I suggested above, and you'll find an option for disabling automatic login.]("http://ubuntuforums.org/showthread.php?t=1701507&highlight=disabling+password")"

I wish to enable automatic login. How do I get to this screen or directory branch? Do I need a desktop to do that?

---

### Post by fooman on 2011-03-27
if you can get back to the command prompt.....try typing startx (not xstart),  press enter and see what happens.

---

### Post by TruePurple on 2011-03-27
That was a typo, I did use startx. 

I have tried some other things at instruction from treebee in chat, all failed so far. I will write up what s/he had me do and what happened in a bit. Perhaps after I try another thing.

How do i uninstall failed programs like the startx one? And does interrupting a install with ctrl c mess things up? Or is ubuntu/linux pretty good at clearing out such garbage?

---

### Post by Dutch70 on 2011-03-27
What are you typing startx in front of? It should be something like this... Truepurple@ubuntu $ 

If it says login, then type in your user name & hit enter, then password & enter and try 
```
sudo startx
```

If you don't get the Truepurple@ubuntu, try hitting (Alt + F7)

If that works, then run this in a terminal... 
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by TruePurple on 2011-03-27
I got the gui installed, but I still could use a answer on enabling automatic login.

---

### Post by fooman on 2011-03-27
at the gnome desktop,  in the top panel,  click on: system > administration > users and groups

when that window opens,  look on the right side where it says "password: asked on login"  ....to the right of that,  click on where it says "change"

another window will open....look at the bottom and click on "don't ask for password on login".  you will then be prompted for your password.  type it in and click "authenticate",  then "ok" to close the remaining window(s).

reboot and you should be good to go.  hope that helps.

---

### Post by TruePurple on 2011-04-01
It no longer asks for my password, but I still get a login screen each time asking me to choose from my ID and "other".

How do I set it so it automatically logs me in each time?

---

### Post by fooman on 2011-04-01
oops,  sorry....what you want is in: system > administration > login screen

click "unlock", type your password when prompted...then put a check in the box next to "log in as <your username> automatically"

---

