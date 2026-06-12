---
title: "Linux newbie needs help!"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by lipscomj on 2010-11-24
I am a relatively new and very inexperienced Ubuntu (1o.o4 I think)  user and recently installed the recommended updates as usual only to find that when I logged in again the gui was frozen.
It allowed me to enter my password then after a brief pause displayed the desktop image with no icons or taskbar. The mouse pointer moved as normal but there was nothing to click on.
I managed to get to the command prompt by pressing random combinations on my key board (I think Ctrl+Alt+F2) and could see that all my files were in order and that it was connected to my wireless network. This was confirmed when I managed to figure out (via numerous google searches) how to ftp the files I needed to a laptop on my network so that my wife could get on with her work so it is clear that nothing has been lost and that the networking is ok.
I tried to start firefox but it that didn't work, I tried evolution  too with the same results.
Where do I start to fix this or should I ftp all my files over and format the drive and start again?

Thanks :D

---

### Post by anewguy on 2010-11-24
If you hold down ctrl/alt and press F1, do you get a terminal screen with a login? 

Dave ;)

BTW - I thought I was the Linux idiot, then I realized I'm the COMPLETE Linux idiot, so you're ok!  ;)

---

### Post by lipscomj on 2010-11-24
Thanks Dave, I shall try that when I get home later.
Please could you explain what the terminal screen is as opposed to the command prompt.
If it;s the same thing then yes I can get it.
You will have to forgive my ignorance of the terminology; I grew up in a microsoft windows world where lines of text behind a gui are something that only the strange boys who never came out of their bedrooms could understand!

Cheers

---

### Post by ironic.demise on 2010-11-24
Open a terminal with ctrl+alt+t
Open a "run" command with ctrl+alt+f2
 
In either of those type "gnome-panel"
 
[http://ubuntuforums.org/showthread.php?t=1626339](http://ubuntuforums.org/showthread.php?t=1626339)
 
Terminal, yeah it's like cmd.exe or the command line.
 
If you have any trouble, let us know

---

### Post by kesman on 2010-11-24
So you got to the terminal, that's good. The thing that your internet connection works there too is even better.

You could try to update, maybe there was a bug in some previous update you did and it's now fixed. To do this in the terminal, enter the following commands. It asks for your password, and when you type it, it won't show. Don't worry, just keep writing and press enter.

[s]Here's the command for update **_[COLOR="Red"][SIZE="5"](WHICH WILL NOT UPDATE YOUR SYSTEM VERSION!)[/SIZE][/COLOR]_**:
```
sudo apt-get update && sudo apt-get dist-upgrade
```[/s]

hope this helps!

Mod Note: That way to update to the next version is not supported. Do not use it or tell others to use it.  Thank you.

---

### Post by mastablasta on 2010-11-24
wouldn't that also upgrade the distribution to 10.10? what if the user  want's to stay with 10.04?

---

### Post by ironic.demise on 2010-11-24
> **mastablasta said:**
> wouldn't that also upgrade the distribution to 10.10? what if the user want's to stay with 10.04?
 yes it would I suggest  JUST sudo apt-get upgrade

---

### Post by lipscomj on 2010-11-24
Thanks for your help guys, I shall try the upgrade to 10.10 as I did try an update (sudo apt-get update without success).
Is there any reason why I wouldn't wish to upgrade to 10.10? Presuambley it is an improvemnet overthe previous version....or is that too simplistic?

Cheers

---

### Post by kesman on 2010-11-24
> **mastablasta said:**
> wouldn't that also upgrade the distribution to 10.10? what if the user  want's to stay with 10.04?

No it wouldn't update the system version. There's a special command for that. Dist-Upgrade is the same as Upgrade, except that it updates dependecies as well and can remove unnecessary packages.

---

### Post by mastablasta on 2010-11-24
> **lipscomj said:**
> Thanks for your help guys, I shall try the upgrade to 10.10 as I did try an update (sudo apt-get update without success).
Is there any reason why I wouldn't wish to upgrade to 10.10? Presuambley it is an improvemnet overthe previous version....or is that too simplistic?
 Cheers
 
It appears i was wrong and you should use the whole command you were given.
 
the reason might be because 10.04 is LTS release which is supported for 3 years, while 10.10 is a newer (normal version). it's also a good choice especially if something doesn't work in 10.04, then maybe in 10.10 it will.
 
I decided to use 10.04 as long as possible (3 year) and only then upgrade. unless a new version really shows me some advantage (such as fixing all my sound issues).

---

### Post by lipscomj on 2010-11-24
I have tried the upgrade and update commands with no success. The GUI still won't work. I am also unable to run Firefox from the command line (Error: no display specified); I don't know  if this is related or not.

Thanks:confused:

---

### Post by kesman on 2010-11-24
Ok, then you can either install 10.10 from scratch with a cd or USB-stick, or keep trying to fix the problem.

You could try to find out the cause of the problem with:
```
cat /var/log/Xorg.0.log
``` and paste the output here, or use pastebin.

---

### Post by lipscomj on 2010-11-24
[CENTER][LEFT]I ran that command and have an endless stream of numbers several pages long  that I could never hope to understand so I think it would be best to start from scratch. 
If I download 10.10 onto a memory stick, can you talk me through it please?

Many thanks

Jim
[/LEFT]

[/CENTER]

---

### Post by kesman on 2010-11-24
Well all you need is a program called unetbootin (no typo there) from here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to write the ubuntu 10.10 desktop image on to your usb-stick.
Then you edit your bios settings so that you can boot from the stick, and the rest is too simple to explain.

---

### Post by lipscomj on 2010-11-25
I shall try that this morning, thanks for your help.

---

