---
title: "Sound from remote gnome-session"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by apollothethird on 2010-11-06
Can someone tell me how to enable sound on my Laptop for the remote Ubuntu gnome-session that is running?

I have a Desktop computer in my computer room running Ubuntu with all my main applications and utilities.  I have my Laptop in my living room with me also running Ubuntu (both 10.10).  I have very specific requirements for the sound prompts and alarms from my Desktop.  I realize that I can run speaker wire from my Desktop to my Laptop and probably get the sound that way.  But am hoping to resolve the issue in such that I can’ receive the sound to my Laptop along with the other visual components of my remote gnome-session.

There was a time when running the applications that produced sound I the sound would be output to the Desktop speakers.  However, after some experiments in trying to get sound I’m now not getting sound anywhere from my remote gnome-session.  The sound preferences only show “Dummy Output” for the sound device.

The applications still work perfectly well from the Desktop.

Thanks in advance for any suggestions or comments.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by P4man on 2010-11-08
I dont know how to fix it for remote desktop specifically (I think it should just work?) But perhaps a better solution for you is to redirect all sound to a remote machine (even if you dont have a remote desktop session running). 

Thats fairly easy to do with pulseaudio, so if that is something that would be useful to you, let me know and ill explain

---

### Post by apollothethird on 2010-11-10
> **P4man said:**
> I dont know how to fix it for remote desktop specifically (I think it should just work?) But perhaps a better solution for you is to redirect all sound to a remote machine (even if you dont have a remote desktop session running). 

Thats fairly easy to do with pulseaudio, so if that is something that would be useful to you, let me know and ill explain

Thanks.  Having a separate sound server under Pulse works well.  I see a lot of potential with it and will be utilizing this in many ways.

I have a number of computers in my network.  I'll be replacing the current wiring for sound with sound servers.

Now if only I can find a clean way to start X without a Windows Manager.  Starting X, then logging into a remote machine and running the gnome-session works, but looking at all the error messages is like listening to the system crying wolf.  It gives me the impression that I'm doing so much wrong.

Also, logging out, or closing the session leaves a lot of residue.  I almost have to reboot both machines to get everything back smooth.

One of the differences between Windows and Linux is that you don't have to reboot Linux every time you make a simple change.  the frequent rebooting is reminding me of Windows.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by P4man on 2010-11-10
You have a ton of ways to remotely connect. It really depends what you want to do which is best, but the built in "remote desktop" is both slow and rather limited (but easy to set up). Have a look at running X over ssh and freenx:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

OH and BTW, pulseaudio also works wonderful under windows. I just tried it a while ago, at least as soundserver (sink). Havent figured out yet how to use it as sound source on windows.

---

### Post by apollothethird on 2010-11-10
> **P4man said:**
> You have a ton of ways to remotely connect. It really depends what you want to do which is best, but the built in "remote desktop" is both slow and rather limited (but easy to set up). Have a look at running X over ssh and freenx:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

OH and BTW, pulseaudio also works wonderful under windows. I just tried it a while ago, at least as soundserver (sink). Havent figured out yet how to use it as sound source on windows.

Thanks, P4man.  I already have Ubuntu 10.10 installed on the Laptop, the desktop version.  I have the desktop version installed on one of my Desktop computers and Ubuntu 10.10 Server version installed on one of the other desktop computers.

I'm able to run the gnome-session manager on the Laptop and the performance is great.  I'm just looking for a way to properly start X on the Ubuntu 10.10 desktop edition on the Laptop without a Windows Manager.  Running X actually works, but I believe there's something missing in that particular step... maybe not.  If there is the only way, to type "X" in a console login, then going to a different console login, setting the DISPLAY to that X server, then ssh to the desired host and running the gnome-session is the only way, I have it down.

I wouldn't want to trade the Ubuntu installation on the Laptop for the other Nix's since I also do work natively on the Laptop and would miss the Ubuntu familiarity I'm getting used to.

By the way, speaking of Windows (as a sound server) I have another computer running Windows 7 which I tested the Pulseaudio sound server.  It works, but not very well.  I run Cygwin on it and call up the X server and also run the gnome-sessions on it also.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

