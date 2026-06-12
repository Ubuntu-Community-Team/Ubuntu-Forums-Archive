---
title: "Gutsy File Sharing"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by Jerry N on 2007-10-13
File sharing between UBUNTU 7.04 and an XP machine works fine but  file sharing with Gutsy Tribe 5, Gutsy Beta, and Gutsy RC does not work in either direction.  File between XP and  Freespire 2.0.3 works great, (Mandriva 2008 refuses to install Samba, but who cares) so I don't think the problem is at the Windows end.  I haven't tried copying the ip table definitions and Samba configuration from the working Ubuntu 7.04 drive to 7.10RC but I guess the worst thing that could happen is that I would have to re-install 7.10RC.  

Is anyone else having problems with this?  I am concerned that the final release of Gutsy will be the same.

Jerry

---

### Post by ljonesj on 2007-10-13
my server runs 7.04 my 2nd laptop runs 7.10rc but they work as i can share files between them and my windows machine can see both fine too. do you have your samba user and password setup right

---

### Post by Jerry N on 2007-10-14
I don't know if I have Samba and the passwords set up right or not but it is exactly the same as I am using with Ubuntu 7.04.  I have copied the Samba Conf file from 7.04 to 7.10RC but that has not helped at all.  At this point, Ubuntu 7.10RC will not communicate with the XP machine at all (no file sharing, no printing) but Firefox talks to the internet through the router without any difficulty.  Ubuntu 7.10RC has the latest updates.  

The computer I use for diddling with various versions of Linux has a "Mobile drive rack" and Ubuntu 7.04 and Ubuntu 7.10RC are on different hard drives that can be plugged in.  

Jerry

---

### Post by Jerry N on 2007-10-14
I think I have this solved now.  I had to clean out the iptables and revert to the simplest default configuration.  I also had to fiddle a bit with smb.conf and make it look like the smb.conf that works in Freespire 2.0.3.  Printed pages aren't page feeding properly but that probably means I will need to delete the printer setup and reinstall it.  The printer is an HP Laserjet 1320 and is connected to the Windows XP machine.  

I feel better about the upcoming Ubuntu 7.10 final release now.

Jerry

---

### Post by kghosh22 on 2007-10-15
Could you please elaborate the steps you followed to get samba working. I had manged to get samba to see the share folders for about two hours before samba closed eyes. 

Thanks in advance,
K.Ghosh

---

### Post by smuggly on 2007-10-15
Same Problem Here i can get to the internet and see the other box but cant connect? any help?
                                                    Thanx     Tom

---

### Post by Jerry N on 2007-10-15
File sharing worked OK in Freespire without any fiddling with Samba so I just made my Gutsy smb.conf look like the one in Freespire.  However, my prime problem was with iptables, not Samba.  

Jerry

---

