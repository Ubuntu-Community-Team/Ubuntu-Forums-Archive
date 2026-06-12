---
title: "cannot access machine on home network"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by jgw on 2014-10-08
I am running 14.04  I have a small home network which has 3 ubuntu machines and 1 windows machine.  I am currently working on one of the ubuntu machines.  I cannot access this machine from any other machine although I can access all other machines from this machine.  When I choose to browse the network, from files, on this machine all machines are listed, including a folder for the windows.  In windows all other machines are also listed.  The type column, for all machines is "unknown", in windows the type, for all machines, is "folder", otherwise all machine types are also unknown.  I should also mention that, when I double click on this machine, in browse network, I am asked for a password which I do not know and which I don't remember ever entering.  When trying to access this machine, from any other, I also get this password request.  This confuses me.  I can, obviously, access this machine, all directories and files yet, under networks, I cannot access it.  

This gets more confusing.  There is the passwd command which will work.  What I do not know is which password it references.  I have two passwords that I do know.  The first is my system password (the one I use for sudo, gksu), my super user password (referred to as my system passwords), and then the one for my user account.  I know and use the system and super user passwords (system passwords) with no problems.  I have figured out that my problem is with the user account and the user account has nothing to do with my system passwords.  I am basing this on the fact that my system password does not work as described in the first paragraph and that there is one more asterisk for the user account than there is for what I am calling the system passwords.

What I now need to know is how to deal with the user account password without knowing what that password is.  Oh, I also checked the history of being logged into the user account and its set at auto and I seem to do that a lot (auto, however, does not seem to deal well with nautilus).

Anyway, any thoughts would be welcome.

Thank you.............

---

### Post by bashiergui on 2014-10-11
Focusing on your first problem, you have to do some things to make everything on the network accessible to everything else. Have a look here on how to get started.

[http://www.howtogeek.com/191116/how-to-share-files-between-windows-mac-and-linux-pcs-on-a-network/](http://www.howtogeek.com/191116/how-to-share-files-between-windows-mac-and-linux-pcs-on-a-network/)

---

### Post by jgw on 2014-10-11
Thanks for the reply.

---

### Post by SeijiSensei on 2014-10-12
It's likely a name resolution problem if you're using Samba.  Try connecting to the machine by IP address rather than name.

---

### Post by jgw on 2014-10-12
Thanks for the reply.

I am not sure howto connect by ip.  I can, however, ping the address of the offending machine with no problem.

---

### Post by bashiergui on 2014-10-12
Provide more details about which sharing service you're using and how you set it up. Are you using samba?

---

### Post by jgw on 2014-10-12
Thanks again.....

As far as I know I am using samba.  I setup my shares my left clicking on what I want to share, a box pops up, I fill in the info - that's it.  I am also the only user on this machine or samba.  I did notice that the two machines if have immediate access to may be of interest.  One, this one, is using eth1 and the other is using eth0.

vi /etc/network/interfaces gives me (found this on the net):
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
~

---

### Post by SeijiSensei on 2014-10-13
> **jgw said:**
> I am not sure howto connect by ip.  I can, however, ping the address of the offending machine with no problem.

On Windows, enter an address like \\ip.of.the.server\share.  On Linux it may depend on what flavor you are running.  I use Kubuntu, which supports smb:// URLs in file managers like dolphin.  From those machines, I would type smb://ip.of.the.server/share in the address box.  I believe Nautilus also supports smb:// URLs, but I haven't used it in a long time, so I can't promise it will work for you.

---

### Post by jgw on 2014-10-13
thank you.........

I am failing on the smb:// thing.  I am trying from my ubuntu 14.04 machine.  I have tried it in firefox and in nautilus to no avail.  Its becoming pretty obvious to me that I am probably wasting your time and I should do some more study on this whole thing before I truly screw things up.

Thanks again...........

---

