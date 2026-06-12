---
title: "Help!!!"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by XKCD64 on 2009-10-24
I have a netbook, and it's my only computer.  I installed Ubuntu Netbook Remix, changed it to normal gnome and today both panels are gone.  I can't get on the internet or anything!!  Help!  I can't re install, and I have no other computer (I'm at the library right now).  Please help me.

---

### Post by NCLI on 2009-10-24
> **XKCD64 said:**
> I have a netbook, and it's my only computer.  I installed Ubuntu Netbook Remix, changed it to normal gnome and today both panels are gone.  I can't get on the internet or anything!!  Help!  I can't re install, and I have no other computer (I'm at the library right now).  Please help me.
Try pressing alt-f2, then write "nautilus", without the quotes, and press enter.

If that doesn't work, try reading [this thread]("http://ubuntuforums.org/showthread.php?t=1135471").

---

### Post by XKCD64 on 2009-10-24
I tried both and it wont let me create a launcher.  
 
Does anyone else know another way to fix this?  :confused:

---

### Post by NCLI on 2009-10-24
Well, there is a way, of course. Try pressing ctrl+alt+F1. You will be at a black screen asking you to log in so do it. 
Then type "nautilus", and press ctrl+alt+F7.

---

### Post by NinjaNumberNine on 2009-10-24
...rather descriptive title..
________:lolflag:____

---

### Post by NCLI on 2009-10-24
Indeed xD

I would have commented on it if not for the urgency of the problem :p

---

### Post by XKCD64 on 2009-10-24
thanks, but it didn't do anything for me...
 
And sorry about the title. I'm just freaking out. Sorry.
 
 
 
Edit:  When I type nautilus it comes back and says Cannot open display

---

### Post by NCLI on 2009-10-24
[COLOR=Silver]Ok, it sounds like your netbook is not just having a problem loading the desktop, but is completely frozen. 

Try holding ctrl+alt and typing REISUB. Your PC should reboot. If not, we have a kernel crash, which is quite a bit more serious than your system having a problem loading the desktop.
[/COLOR]

EDIT: Strike that, something does happen then? I'd forgotten that you can't launch a graphical app from the CLI... Hmmm, let me think for a moment. I take it that you have tried rebooting?

---

### Post by XKCD64 on 2009-10-24
rebooting doesn't help unfortunatly....
 
 
Uhm... I also have moblin on my flash drive and it's right here with me.  I booted into that but wifi doesn't work.  If there's a quick, easy fix for that I could always use moblin... but I really need my netbook to work.
 
 
Sorry for all the trouble.

---

### Post by XKCD64 on 2009-10-24
Me:  Ctrl+alt+F1,  log in, and type nautilus.
 
The computer then says... Cannot open display

---

### Post by fooman on 2009-10-24
might want to try this...press alt-ctrl-f1 to drop to a shell.  once there,  type this command and then press enter:

```
sudo apt-get install nautilus-open-terminal
```after it installs,  reboot with this command:

```
sudo reboot
```when you get back to the desktop,  right-click anywhere and from the drop-down menu, choose: "open in terminal"

when the terminal opens,  type this:

```
gnome-panel &
```press enter and see if the panels come back.

hope that helps.

---

### Post by NCLI on 2009-10-24
If that works, you're a genius, though I'm afraid gnome has totally crashed for him...

---

### Post by XKCD64 on 2009-10-24
nope.  It didn't work....

---

### Post by NCLI on 2009-10-24
Ok, I think rescuing your old account is hopeless, let's try something else.

Do ctrl+alt+F1 again, log in again, if you aren't already,then do:     
 ```
sudo useradd -m **username**
sudo passwd **username**
```Replace **username** with something you come up with yourself, and enter a new password when prompted to do so. Reboot, and login with your new account, then post here again.

EDIT: Try the below first, just for the hell of it.

---

### Post by fooman on 2009-10-24
do you get the option for "open in terminal" when you right-click on the desktop?

if yes,  try typing this:

```
desktop-switcher
```press enter,  then choose **Ubuntu Netbook Desktop** and **Apply**
 ...see if that gets you back to the remix desktop.

---

### Post by lisati on 2009-10-24
> **XKCD64 said:**
> Cannot open display
This says to me that there's possibly some kind of configuration problem. Doesn't the recovery mode available through grub at startup have an option to help with this?

---

### Post by NCLI on 2009-10-24
> **lisati said:**
> This says to me that there's possibly some kind of configuration problem. Doesn't the recovery mode available through grub at startup have an option to help with this?
Are you sure that's not perfectly normal when in another TTY than the one the graphical desktop is currently running in?

---

### Post by twright on 2009-10-24
Hello,
It seems that somehow your configuration is messed up and (as you can see) that prevents you from using the system.

First thing is DON'T PANIC, we should be able to easily help you fix your system and get you up and running again in no time.

Next step is to press Ctrl+Alt+f1 and login as others have suggested, this will allow you to go in and manually fix it. Now just type in this command (be sure to get it exactly as shown) which will delete all of your corrupted configuration files (you may want to backup first) so when you restart it should work as new again:
```
rm -R .*
```

Good luck :-)

---

### Post by fooman on 2009-10-24
> **lisati said:**
> This says to me that there's possibly some kind of configuration problem. Doesn't the recovery mode available through grub at startup have an option to help with this?

lisati,  if you drop to a shell (ctrl-alt-f1), log in and then type "nautilus"...i believe you will also get "cannot open display".

---

### Post by NCLI on 2009-10-25
I wonder what happened to him :(

---

