---
title: "Watching traffic"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Tazmman on 2011-02-22
Please help
 I'm  Inquiring if there is a way to monitor what my computer is used for on my network. 
I  my self  have left the computer maintaining to a Boarder at my house .  I'm I'm concerned of some malicious activities  that have occurred in  the past. 
 I've heard of Key loggers,  Can a key logger be installed  in stealth, as not to be automatically detected. I've heard of clam AV,  or such that I used for detection. If there a way of putting a logger  program on an "exceptions" list of detection that would be helpful. I  can access of machine "unmanned" and open
 I'm also wondering  how to  id monitoring programs, as not to be uncovered, while accessing has  occurred, ie; a "last time" program executed log, that can edited . 
It  might seem extreme , But I,m speaking of catching  a thief, in a fraud  worth "thousands" , against my elderly parents . I 'm sure he's not  aware that I on to him .   [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]  I don't want to blow a chance of collecting  evidence . 
Again any help wold be appreciated. 
Thankyou.
P>S> I'm not an absolute beginner, But its time to "up", my Ubuntu knowledge

---

### Post by sanderd17 on 2011-02-22
can you look in /var/log/ and say if you want anything more.

---

### Post by bodhi.zazen on 2011-02-22
> **Tazmman said:**
> Please help
 I'm  Inquiring if there is a way to monitor what my computer is used for on my network. 
I  my self  have left the computer maintaining to a Boarder at my house .  I'm I'm concerned of some malicious activities  that have occurred in  the past. 
 I've heard of Key loggers,  Can a key logger be installed  in stealth, as not to be automatically detected. I've heard of clam AV,  or such that I used for detection. If there a way of putting a logger  program on an "exceptions" list of detection that would be helpful. I  can access of machine "unmanned" and open
 I'm also wondering  how to  id monitoring programs, as not to be uncovered, while accessing has  occurred, ie; a "last time" program executed log, that can edited . 
It  might seem extreme , But I,m speaking of catching  a thief, in a fraud  worth "thousands" , against my elderly parents . I 'm sure he's not  aware that I on to him .   [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]  I don't want to blow a chance of collecting  evidence . 
Again any help wold be appreciated. 
Thankyou.
P>S> I'm not an absolute beginner, But its time to "up", my Ubuntu knowledge

See the stickies at the top of the security section:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Honestly though, at the end of the day, such things  come down to who has more security-foo , you or the intruder.

From you question it is apparent you have little or no knowledge of linux security, and thus you are on the short end of the sick. As such, I advise you start doing a lot of reading and / or seek professional assistance.

Your question is obviously from a "Windows" perspective and in Linux the threats from viruses and key loggers are minimal to none. You will need to learn to use tools such as snort, OSSEC, and apparmor.

One "easy" alternate for you would be to use Fedora. On Fedora install the xguest package. xguest is a kiosk mode locked down by selinux and would be quite secure out of the box.

This is an old link, but ...

[http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html](http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html)

---

### Post by HermanAB on 2011-02-22
$ man tcpdump

:)

---

### Post by Grenage on 2011-02-22
> **Tazmman said:**
> Please help
 I'm  Inquiring if there is a way to monitor what my computer is used for on my network. 
I  my self  have left the computer maintaining to a Boarder at my house .  I'm I'm concerned of some malicious activities  that have occurred in  the past. 
 I've heard of Key loggers,  Can a key logger be installed  in stealth, as not to be automatically detected. I've heard of clam AV,  or such that I used for detection. If there a way of putting a logger  program on an "exceptions" list of detection that would be helpful. I  can access of machine "unmanned" and open
 I'm also wondering  how to  id monitoring programs, as not to be uncovered, while accessing has  occurred, ie; a "last time" program executed log, that can edited . 
It  might seem extreme , But I,m speaking of catching  a thief, in a fraud  worth "thousands" , against my elderly parents . I 'm sure he's not  aware that I on to him .   [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]  I don't want to blow a chance of collecting  evidence . 
Again any help wold be appreciated. 
Thankyou.
P>S> I'm not an absolute beginner, But its time to "up", my Ubuntu knowledge

I don't know where you are, or what laws apply, but I doubt anything that you personally gather would be submissible as evidence.  If the PC is yours, and the relevant authorities believe there is something in what you suspect, then trained people could investigate it.

---

### Post by Tazmman on 2011-02-24
Thank you  for the  info starting point.  I'll source it out to A " Linux Savy" guru I've been directed to . Will be back in touch as things progress  thanks.

---

