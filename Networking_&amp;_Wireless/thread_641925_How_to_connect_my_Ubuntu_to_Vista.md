---
title: "How to connect my Ubuntu to Vista"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by the_wayman on 2007-12-16
[SIZE="4"]I have a desktop running Windows Vista ultimate (192.168.12.175)  and laptop running Linux Ubuntu 7.10(192.168.12.121).
Both have internet access though a wireless router(192.168.12.12).
I can ping them Both from both the system.
I have samba Installed.

Problem.

Cant Configure samba...
                            to access my Ubuntu from my Vista
                            to access my Vista from my Ubuntu.

Does not appear on the "network" on either of the system.

Urgently need you your help i have look thought all the other forums with out any success. ](*,)
:KS Please i don't want to go back xp[-X on my laptop.
I am a new linus user so please keep it simple. Thanks a lot for you help in advanced.
[/SIZE]

---

### Post by wjp.reg on 2007-12-16
what have you done to configure a network on windows?  Have you assigned a workgroup name?

Have you installed samba and related files (smbfs, smbclient)?

---

### Post by yeaitsdark on 2007-12-16
I found reading this helped me a lot.

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id318178](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id318178)

It might seem like a lot more information than you might need, but it's always good to know what's really going on in your configuration file.

Recall to edit the file type: 
sudo gedit /etc/samba/smb.conf

Also, do you have NetBios enabled on your windows system? Check also if your firewall is on.
Start > Run:
firewall.cpl

I always turn that stuff off when I configure network stuff. I have Vista and Ubuntu working nicely together via Samba.

---

