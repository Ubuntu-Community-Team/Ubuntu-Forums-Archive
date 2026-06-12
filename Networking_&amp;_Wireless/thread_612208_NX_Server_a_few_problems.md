---
title: "NX Server a few problems"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by Inxsible on 2007-11-13
I installed NX server using the following two guides.

[http://ubuntuforums.org/showthread.php?t=493983&highlight=free+nx+server](http://ubuntuforums.org/showthread.php?t=493983&highlight=free+nx+server)

[http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/](http://stuffem.wordpress.com/2007/03/13/geek-gal-setting-up-nx-terminal-server-on-ubuntu/)

Now, this is the scenario:

1) I use my work XP laptop to connect to my work ISP.
2) My Ubuntu box is connected to my home ISP
3) I use a router

[COLOR=Red] When I use the local address(192.168.x.x) to connect[/COLOR] to my ubuntu box from my XP machine (connected to the work ISP so the IP address is different), I can see my Ubuntu box with these problems
      a) My Ubuntu box is 1440x900 and is configured as twinview with another 17 inch monitor, but my XP laptop only has 1280x1024 res. When it connects, everything from my ubuntu box is squished to fit, and I can hardly read anything. 

b) Also, I do NOT get scroll bars so that I can scroll and do something else. Because my top panel and my AWN also do not show in that small resolution :(

c) I cannot even maximize the screen any further :(

d) If I connect in Shadow mode, and I open a menu or do anything, I can see that it affects the ubuntu box, but I cannot see it on my XP machine. for eg. if i open a terminal window (from the XP machine), it will open in ubuntu, but it won't show in my XP machine. (This makes is useless, since I never know if an app was opened unless I am sitting right in front of my ubuntu box)
It seems that I only get the "print-screen" (for lack of a better word) of the ubuntu box when I first connect.

[COLOR=Red] If I use the host-name that i created @ no-ip.com, it simply doesn't connect[/COLOR]. It gives me the following error:```
NX> 203 NXSSH running with pid: 5740
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host mybox.no-ip.biz port 555: Connection timed out

```Can someone please help ?

---

### Post by Inxsible on 2007-11-14
bumping for some answer :(

---

### Post by Inxsible on 2007-11-15
bumping for the people on the eastern part of the earth to see and help me out :D

---

### Post by Inxsible on 2007-11-15
bump it up

---

### Post by Inxsible on 2007-11-16
no one uses NX Server at all ? :(

---

### Post by mikeliuk on 2008-01-08
Old thread, I know but I'll post for completeness. Just thought I'd mention two work arounds.

It may be possible to work around problem a). Click "Configure .." on the nxclient login window and under the "General" tab (displayed by default), "Desktop" pane, select "Unix" on the first drop-down and "custom" on the second drop-down menu. Pressing "Settings..." should show "Run the console" and "Floating window" selected. Logging in should then give you a small xterm window rather than filling the screen with a squashed desktop.

I have the same hostname problem with a no-ip.com address. It works fine using the Windows XP client but I have to work around the problem with both Ubuntu and Gentoo. (There's likely a solution somewhere online ... ) I work around by ssh-ing to the address ("ssh myhost.no-ip.com") which usually tells me

The authenticity of host '***.no-ip.com (ip-number)' can't be established.

and I simply use the given ip number to connect.

---

