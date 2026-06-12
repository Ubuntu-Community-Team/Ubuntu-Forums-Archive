---
title: "Networking - Locked myself out"
date: 2015-09-05
forum: Networking &amp; Wireless
---

### Post by jimbostrong on 2015-09-05
[COLOR=#111111][FONT=Ubuntu]Im after some help desperately![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I currently have a server running ubuntu 14.04. I access it using a macbook pro and chicken VNC.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]All was fine until a few days ago i decided to increase security and install UFW.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When i installed it, i followed the tutorial and made sure i opened SSH.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Since then i am now unable to access the server using chicken VNC. The server also cannot be accessed by Plex. (I'm assuming that the firewall is doing what it is supposed to and blocking all incoming connections!)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So, im a bit stuck, i can't access the server to turn off the firewall.

I have just tried to access the sever using SSH from my macbook pro but i get the error message 'SSH: Connect to Hot 192.168.0.4 port 22: connection refused'[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have tried plugging it into my TV to directly access the server and it says 'Mode not supported' (i believe this is a samsung HDTV thing) so i cant use that to get into it. I believe this is due to it having the incorrect resolution. [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any help really appreciated!!!!![/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-09-05
It sounds like you have physical access to the machine.  If so, choose "Advanced" from the initial boot menu, then choose "recovery mode" for the default kernel.  When the next menu appears, choose "root shell."  (If you don't have a boot menu, hold down the Shift key while booting.)

Now enable access to the root filesystem with the command:
```
mount -o remount,rw /
```
(Note there is no space after the comma.)  You should be able to disable the firewall.  Be careful, though, since you're working as the root user.

If this a remote machine with no physical access, things are a lot more difficult.

---

### Post by jimbostrong on 2015-09-05
hi,
i do have physical access to the machine, but the tv i plug it into comes up with 'mode not supported'.

I don't think i can get into ubuntu at all (i believe as soon as it changes the resolution my tv gives me the error above).

---

### Post by SeijiSensei on 2015-09-05
Recovery mode uses plain old VGA text-mode without graphics.  Have you tried it yet?  Do the computer and TV have VGA ports as well as HDMI?  If so, try those.

---

### Post by jimbostrong on 2015-09-05
that will have to be my next attack, il try and get into the recovery mode.

The TV has VGA and the Computer has VGA.  Il try it now.  Is it HOLD DOWN SHIFT?

If i can't get into it that way, whats the next option?

---

### Post by SeijiSensei on 2015-09-05
If you usually see a boot menu when the machine starts up, then just follow the steps I presented.  If the machine boots directly into Ubuntu at startup, hold down Shift during boot to get the menu.

It's pretty unlikely you won't be able to boot into recovery mode.  Still if that eludes you, you can boot from an installation disk and use Try Ubuntu.  That's more complex though as you'll have to mount the Linux filesystem on the hard drive before doing anything.

---

### Post by jimbostrong on 2015-09-05
okay, so as soon as it boots into ubuntu i get mode not supported.

i don't seem to be able to get into a boatmen using shift.

Is there a way i can use a ubuntu livecd and try and boot into that to get into the system?

---

### Post by SeijiSensei on 2015-09-05
Yes, but read this first: [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

I'd also look at the settings on the TV to make sure there isn't some mode you can set that is supported.  I've connected machines to a Samsung TV with both HDMI and VGA and haven't encountered your problem.

---

### Post by jimbostrong on 2015-09-05
thanks,
nope it doesn't work, its obviously the tv!!  (which i find strange!)

i suppose the next thing is to find a way remotely into the server......??

(feel like i need to take a hacking course)

---

