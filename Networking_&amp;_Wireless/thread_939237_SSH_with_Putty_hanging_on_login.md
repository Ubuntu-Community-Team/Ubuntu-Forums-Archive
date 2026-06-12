---
title: "SSH with Putty hanging on login"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by jotul on 2008-10-05
I'm new to linux so apologies if this turns out to be a no-brainer! It's another SSH and Putty question I'm afraid as I couldn't see any other threads covering my problem. I can SSH OK from my Windows XP machine into my Ubuntu Linux machine across my my local network but not from the internet. I'm using port 22 and it's open on my ADSL router and I can see it with canyouseeme.org. It's also open on Firestarter and I've tried with that disabled too.    

When trying from the internet I only get this far in the Putty window:

[I]login as: xxx
[email]xxx@yyy.yyy.yyy.yyy[/email]'s password[/I]

but when I enter the password nothing else happens and I have to close the Putty window to exit.  

Looking at the var/log/auth.log file on the destination server I see this for the internet connection attempt: 

[I]Oct  5 16:32:02 localhost sshd[7700]: Accepted password for xxx from 84.12.73.144 port 1411 ssh2
Oct  5 16:32:02 localhost sshd[7702]: (pam_unix) session opened for user xxx by (uid=0)[/I]

and I get this when I connect locally

[I]Oct  5 16:35:28 localhost sshd[7709]: Accepted password for xxx from 192.168.0.4 port 1446 ssh2
Oct  5 16:35:29 localhost sshd[7713]: (pam_unix) session opened for user xxx by (uid=0)[/I]

I presume from this I am actually logging in OK? 

The Putty log on the XP machine shows this for the internet connection 

[I]Event Log: Sent password
Incoming packet type 52 / 0x34 (SSH2_MSG_USERAUTH_SUCCESS)
Event Log: Access granted[/I]

but then nothing else.

For the local connection the Putty log shows this:

[I]Event Log: Sent password
Incoming packet type 52 / 0x34 (SSH2_MSG_USERAUTH_SUCCESS)
Event Log: Access granted
Outgoing packet type 90 / 0x5a (SSH2_MSG_CHANNEL_OPEN)
  00000000  00 00 00 07 73 65 73 73 69 6f 6e 00 00 01 00 00  ....session.....
  00000010  00 40 00 00 00 40 00                             .@...@.
Incoming packet type 91 / 0x5b (SSH2_MSG_CHANNEL_OPEN_CONFIRMATION)
  00000000  00 00 01 00 00 00 00 00 00 00 00 00 00 00 80 00  ................
Event Log: Opened channel for session
Outgoing packet type 98 / 0x62 (SSH2_MSG_CHANNEL_REQUEST)
  00000000  00 00 00 00 00 00 00 07 70 74 79 2d 72 65 71 01  ........pty-req.
  00000010  00 00 00 05 78 74 65 72 6d 00 00 00 50 00 00 00  ....xterm...P...
  00000020  18 00 00 00 00 00 00 00 00 00 00 00 10 03 00 00  ................
  00000030  00 7f 80 00 00 96 00 81 00 00 96 00 00           .............[/I]

plus lots more that gets to the prompt.

So it looks to me as if both machines consider the login process to be OK across the internet but the Putty session doesn't carry on after that with SSH2_MSG_CHANNEL_OPEN packet etc. Can anyone point me in the right direction please?

---

### Post by kevdog on 2008-10-05
Were your ssh keys created with putty or openssh.  You can convert openssh keys to the putty format -- however you need to do this explicitly.  Openssh does not understand the putty format.

---

### Post by jotul on 2008-10-06
Thanks for your reply Kevdog.

I recall that when I initially tried to connect usng Putty there was a screen that appeared which mentioned the keys but I can't remember exactly what is was. Something along the lines of "there is no key on the server - do you want to create one?" I think.

---

### Post by choochus on 2009-01-10
I have a similar problem.

I get a long (30 - 45 second) delay when I connect from Windows Putty to my Intrepid server. I'm using keys for password-less login and it always works, just long delay before I get my shell.

I had another delay problem before that was fixed by [this thread]("http://ubuntuforums.org/showthread.php?t=630623") (fixed by removing DNS Lookup from ssh).

Here is where it hangs in my Putty log - the delay is right after "Access Granted":

2009-01-10 18:14:08	Offered public key
2009-01-10 18:14:09	Offer of public key accepted
2009-01-10 18:14:09	Access granted
2009-01-10 18:14:34	Opened channel for session
2009-01-10 18:14:34	Requesting X11 forwarding
2009-01-10 18:14:34	X11 forwarding enabled
2009-01-10 18:14:34	Allocated pty (ospeed 38400bps, ispeed 38400bps)
2009-01-10 18:14:34	Started a shell/command


I'm not sure where to check on the server side. There isn't anything about ssh in auth.log or daemon.log or messages.

thanks!
 Chooch

---

