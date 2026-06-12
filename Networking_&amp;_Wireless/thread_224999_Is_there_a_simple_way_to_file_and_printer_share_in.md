---
title: "Is there a simple way to file and printer share in Ubuntu Dapper?"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by Washington Irving on 2006-07-28
Computers:
My AMD64 computer running Ubuntu 6.06 LTS 64-bit
My Dad's X86 running Ubuntu 6.06 LTS for X86
My Brothers X86 running Ubuntu 6.06 LTS for X86
My Sister's laptop running Windows XP

Mine and my father's computer connect to a Belkin wireless router via ethernet cables whereas my brother's and sister's connect wirelessly (through a USB adaptor and a PC card respectively).

I have tried to set up cupsys and samba but failed predictably, spectacularly and...er...grammatically. Ahem. I found the methods of configuration to be quite user-unfriendly and a little archaic. Is there an easy way of doing this? a guide? a HOWTO? a gui? I used some web thing called SWAT but that just made me angry, confused, frustrated, innundated, rebated, infiltrated...

I stayed up too late, sorry.

---

### Post by Smandola on 2006-07-29
Washington, 

There are a couple of ways of setting up file sharing on your Ubuntu machines.  One is to go into each of the SMB.CONF files in /etc/samba, on each machine and add in what you want to share from each machine.  There are a number of posts regarding Samba configuration.  You may have already read this.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+config](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+config)


Another GUI method is to use Webmin (which by the way has a SWAT - Samba Web Administration Tool like GUI).  
Ubuntu Webmin How-To can be found here
[http://ubuntuforums.org/showthread.php?t=195093&highlight=webmin](http://ubuntuforums.org/showthread.php?t=195093&highlight=webmin)

Either way, Editting the SMB.CONF file or running Webmin for Samba configuration (GUI for SMB.CONF editting), you should be able to accomplish the same thing.  If there is only files from one machine that you want to share, then all you need to do is configure Samba on the one machine.  However if you want to share files on all 4 of your machines, you are going to need to configure Samba on your Ubuntu machines, and then turn on file sharing in Windows.  Only do this if you are behind a router.  Otherwise you risk exposing your files to the internet.

Don't know if this matters, but are all the machines within the same subnet of your network ?  ie: 192.168.1.X  

I haven't used cupsys, so I can't provide any info for you.

I hope that this helps you, reply back to the post if you need more specific direction, or suggestions. Good Luck !

s.

---

### Post by Washington Irving on 2006-07-29
Thanks but none of these samba HOWTOs seem to work for me, is this really the only way to print or file share? I remember setting up a connection between a SuSE box and  Xandros one with NFS and that was really simple and easy. Ubuntu seems to be strangely lacking in this department. I've found everything else fairly easy but I just can't seem to get this up and running. :sad:

---

