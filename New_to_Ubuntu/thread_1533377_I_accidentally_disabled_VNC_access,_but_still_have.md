---
title: "I accidentally disabled VNC access, but still have SSH access..."
date: 2010-07-17
forum: New to Ubuntu
---

### Post by diablo75 on 2010-07-17
So I was fiddling around with my remote desktop settings (because I was telling someone over the phone what to click on to disable it on their computer) and when I told them, "Just uncheck that box at the top" my brain went "Okay, will do!"  Now I'm locked out of my own computer (VNC wise).

I have SSH access though.  And I'm away from home right now running windows.  How can I VNC in via SSH from Windows?  Alternatively, is there a text file I can edit remotely to re-enable remote desktop?

---

### Post by YesWeCan on 2010-07-17
That'll learn you for helping someone else with their computer problems. :P
So you can SSH from Windows (putty I presume). Once you've got a foothold with SSH the world is your oyster. I suppose you want to re-enable remote access in vino from the command line: [http://ubuntuforums.org/archive/index.php/t-266981.html](http://ubuntuforums.org/archive/index.php/t-266981.html)
Alternatively, you might consider installing/running tightvncserver and getting a port 5901 desktop that way.

---

### Post by bodhi.zazen on 2010-07-17
> **diablo75 said:**
> So I was fiddling around with my remote desktop settings (because I was telling someone over the phone what to click on to disable it on their computer) and when I told them, "Just uncheck that box at the top" my brain went "Okay, will do!"  Now I'm locked out of my own computer (VNC wise).

I have SSH access though.  And I'm away from home right now running windows.  How can I VNC in via SSH from Windows?  Alternatively, is there a text file I can edit remotely to re-enable remote desktop?

Not a big deal really, tunnel your VNC

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Or better forward X applications with ssh -X

If you are on windows, use Xming. XMing and putty both run from a flash drive.

Did I mention, VNC over the internet is insecure, you should leave it disabled and use tunnelling (over ssh).

---

### Post by diablo75 on 2010-07-17
Well crap.  I don't know what's wrong with this thing but I entered this command:

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

via SSH.  I then opened /home/<userhomedir>/.gconf/desktop/gnome/remote_access/%gconf.xml with nano but nothing looked interesting so I closed the SSH session without making any changes to the file.  I reconnected via SSH and then restarted the computer.

I couldn't connect via SSH or VNC after restart.  My girlfriend just got home a few minutes ago and she reset the computer for me a second time.  Same problem.  I'm giving up on it for tonight as aggravating as it is to not investigate this problem but I hate working over the phone.  Who knows what's wrong :(

---

### Post by YesWeCan on 2010-07-17
VNC by Vino probably won't work after a reboot unless you have auto-login set up because you have to be logged in at the PC itself. Note that tightvncserver does not require you to be logged in at the PC.

---

### Post by diablo75 on 2010-07-17
The PC is auto-login enabled.

I just tried a couple other tests.  Over the phone with my girlfriend, I confirmed that the local IP address is still what it's supposed to be.  It's just not accepting ANY incoming connections.  She is no longer able to SSH into the computer from her laptop via a shortcut I created for her to use to access files.  Guess I'm locked out till I get home from work.

In the meantime, can someone tell me what exactly this command does:

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

---

### Post by YesWeCan on 2010-07-18
It just tells gnome desktop to allow remote access. This should not break your SSH. When you rebooted perhaps the SSH server was not restarted or perhaps the firewall port-forward setting for SSH was lost. How did you set up SSH?

---

### Post by bodhi.zazen on 2010-07-18
My guess is a firewall, blocking new connections, and the previous ssh session was established.

---

