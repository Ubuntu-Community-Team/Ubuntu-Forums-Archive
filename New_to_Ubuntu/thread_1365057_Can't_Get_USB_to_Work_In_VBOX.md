---
title: "Can't Get USB to Work In VBOX"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by nakama85 on 2009-12-26
Hey guys I am running ubuntu 9.10 and i have xp  in virtual box. I made sure I did not download and install vbox ose. I am seeing my flash usb drive in vbox settings but when i try to activate it in the session it is grayed out. Any thoughts.

I am running 64bit version

---

### Post by yeats on 2009-12-26
Did you install the guest additions (Devices -> Install Guest Additions)?  It's a shell script that must be run as root... Open a terminal, navigate to the "CD ROM" that appears (will be mounted in the /media/cdrom*X* directory - X being the number assigned to the drive - probably 0) and do this:

```
sudo ./VBoxLinuxAdditions-amd64.run
```

You'll have to restart your VM for the changes to take effect.

EDIT: Sorry, didn't read carefully! :-)

It's the same method though, except in WinXP, you will double click VBoxWindowsAdditions-amd64.exe.

---

### Post by tom.swartz07 on 2009-12-26
> **nakama85 said:**
> Hey guys I am running ... install vbox ose. 

There's your problem there. I did the same thing my first run around with VB.

The OSE version from the software center doesnt have USB support.
Head on over to [http://www.virtualbox.org/](http://www.virtualbox.org/) and get the full version there.

You could still use the disc image for that version too, just write down where you have it saved and load it from there.

Hope this helps!

---

### Post by nakama85 on 2009-12-26
> **chrissharp123 said:**
> Did you install the guest additions (Devices -> Install Guest Additions)?  It's a shell script that must be run as root... Open a terminal, navigate to the "CD ROM" that appears (will be mounted in the /media/cdrom*X* directory - X being the number assigned to the drive - probably 0) and do this:

```
sudo ./VBoxLinuxAdditions-amd64.run
```

You'll have to restart your VM for the changes to take effect.

EDIT: Sorry, didn't read carefully! :-)

It's the same method though, except in WinXP, you will double click VBoxWindowsAdditions-amd64.exe.

I am a little confused about this but I tried as described above and it returned this error sudo: ./VBoxLinuxAdditions-amd64.run: command not found

---

### Post by nakama85 on 2009-12-26
ok I discovered running the guest os but the flash drive is still grayed out. Please help

---

### Post by HappyFeet on 2009-12-26
Uninstall the virtualbox you have, and then go [here]("http://www.virtualbox.org/wiki/Linux_Downloads/") and download the appropriate version of vbox. The one you are using (from the repos) does not have USB support.

---

### Post by halitech on 2009-12-26
did you create the USB filter in Vbox?

---

### Post by halitech on 2009-12-26
> **nakama85 said:**
> Hey guys I am running ubuntu 9.10 and i have xp  in virtual box. I made sure I did not download and install vbox ose. I am seeing my flash usb drive in vbox settings but when i try to activate it in the session it is grayed out. Any thoughts.

I am running 64bit version

Can no one read? they stated they did **NOT** download and install the OSE version

---

### Post by nakama85 on 2009-12-26
> **halitech said:**
> did you create the USB filter in Vbox?

filter was created and activated but still no luck

---

### Post by HappyFeet on 2009-12-26
> **halitech said:**
> Can no one read? they stated they did **NOT** download and install the OSE version

Please save the attitude for the community cafe. People make mistakes, and you could have made your point without being rude.

---

### Post by halitech on 2009-12-26
> **nakama85 said:**
> filter was created and activated but still no luck

are you in the Vbox user group? Run
```
groups
``` in a terminal and see if you are. I have vbox and vboxusers in the list of mine. Not sure of box are necessary or not. I'm also thinking there is something to be done with fstab to allow it to work but I can never remember exactly what I did. the line I added is this 
> none	/proc/bus/usb	usbfs	rw,user,devgid=120,devmode=	0	0
devgid needs to be changed but I don't remember where I got the 120. I'll see if I can find the thread on it.

---

### Post by yeats on 2009-12-26
@nakama85: Sorry about the confusion...

In WinXP, when you click Devices -> Install Guest Additions, WinXP will act as if it has a CD in its drive.  Go to Start -> My Computer and see if it's there.  Then open the CD and double click on the Windows Additions for AMD64 icon.  Everything should "just work" from there.

---

### Post by nakama85 on 2009-12-26
> **halitech said:**
> are you in the Vbox user group? Run
```
groups
``` in a terminal and see if you are. I have vbox and vboxusers in the list of mine.

bingo!!! thank you so much. that was the problem. VBox was no listed!!!

Your awesome... Thanks again!!!!:guitar:

---

### Post by halitech on 2009-12-26
glad to hear you got it working :)

---

### Post by HighCommander540 on 2009-12-26
> **HappyFeet said:**
> Please save the attitude for the community cafe. People make mistakes, and you could have made your point without being rude.

Except sometimes attitude is needed to wake people up. Multiple people said the same thing, when you have a herd of stupidity you need to take drastic measures to eliminate it.

---

