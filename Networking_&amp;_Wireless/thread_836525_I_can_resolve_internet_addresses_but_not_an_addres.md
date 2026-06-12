---
title: "I can resolve internet addresses but not an address on my LAN"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by tubegeek on 2008-06-21
Sorry to ask a seemingly basic question but I haven't seen anything in searching that (so far as I can tell) relates to this particular problem.

Context: a mixed network behind a router, with two Linux Ubuntu 8.04 boxes, labrador and maltese, and two Macs that access shares on them and control them by VNC sometimes.

I have assigned each of the Linux boxes (and 1 Mac) static IP addresses, and created Samba shares on the linux boxes. I can see them OK in the Macs' Finder. I can ping their static IP addresses but I cannot ping the host names on either Linux box. Clue? I dunno.

I see "remote desktop on labrador" and "remote desktop on maltese" in the Mac's Finder and I can VNC and share desktop with labrador but not maltese. I can click "share screen" on the mac and it is unable to connect to the VNC server properly, it times out.

Initially I had a problem seeing the Samba shares on maltese too. I copied my file /etc/samba/smb.conf from labrador to maltese and that got the shares visible on maltese. Still no luck on the VNC connection.

Where are the logs and configuration files pertaining to vnc? I would expect that I could learn something from looking at them and comparing them from the two computers but I don;t know where to find them.

Thanks in advance for any help!

-j

---

### Post by arvevans on 2008-06-21
Pull up a CLI (Command Line Interface) or terminal screen so you can enter text commands.  Now enter "man hosts" followed by ENTER.

[INDENT]Browse up and down the manual page by using the arrows on your keyboard.
Use "q" to exit the man page when you are done.
[/INDENT]

The manual page for /etc/hosts will tell you how to add local hostname-to-IP_Address mappings.

Good luck,
Arv
_._

---

### Post by tubegeek on 2008-06-21
arv, thanks for the pointer.

This is what I did:
added two lines to /etc/hosts on the Mac client:
192.168.08 maltese
192.168.0.63 labrador

and rebooted.

I can now ping maltese and labrador by name- yay!

However: still no VNC into maltese.

Should I edit the /etc/hosts on maltese to include itself?

Any further suggestions? Man pages are great, just don't know which ones to check sometimes. 

Thanks!

---

### Post by arvevans on 2008-06-22
Glad to hear that you are now pinging by Network Name instead of IP Address.

I'm not going to be much help to you regarding VNC into a locally networked computer.  While I have used TightVNC before, my use always was via a dedicated IP_Address number, and that over the Internet.

However, I just now looked at the man page for "xvncviewer" and found that it indicates it should be able to access machines via their Network Name as well as their IP Address.
[INDENT][I]SYNOPSIS
       vncviewer [options] [host][:display#]
       vncviewer [options] -listen [port]

DESCRIPTION
       vncviewer  is  a  viewer  (client) for Virtual Network Computing.  This
       manual page documents version 4 for the X window system.

       If you run the viewer with no arguments it will prompt you  for  a  VNC
       server  to  connect  to.   Alternatively,  specify the VNC server as an
       argument, e.g.:

              vncviewer snoopy:2

       where ’snoopy’ is the name of the machine, and ’2’ is the display  num&#8208;
       ber of the VNC server on that machine.  Either the machine name or dis&#8208;
       play number can be omitted.  So for example ":1" means display number 1
       on  the  same  machine, and "snoopy" means "snoopy:0" i.e. display 0 on
       machine "snoopy".

       If the VNC server is successfully contacted, you will be prompted for a
       password  to  authenticate  you.   If the password is correct, a window
       will appear showing the desktop of the VNC server.[/I]
[/INDENT]

You will obviously need to have the Network Name and associated IP Address in /etc/hosts on the machine which is running the VNC Viewer or VNC Client program.

Beyond that I am at a loss.  Maybe someone else on the forum can take this a bit further?

Arv
_._

---

### Post by arvevans on 2008-06-22
Tubegeek

One quick thought...check the man page for "hosts.allow".  It may be that you are not allowing remote access to the machine you want to use as a VNC server?

Or, it could be some other firewall issue.

Arv - K7HKL
_._

---

### Post by jetsam on 2008-06-22
> 192.168.08 maltese
...is it maybe just a typo in the hosts file entry?  

Did you mean this?
```
192.168.0.8 maltese
```

---

