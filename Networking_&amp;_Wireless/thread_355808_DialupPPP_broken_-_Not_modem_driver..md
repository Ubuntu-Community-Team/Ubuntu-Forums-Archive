---
title: "Dialup/PPP broken - Not modem driver."
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by mpk23 on 2007-02-07
Greetings, and thanks in advance.

I am currently in the unenviable position of living in the sticks where only dialup is available. I  was unable to make 6.06 connect to my ISP - I've configured everything as best as possible, and even dialed up with a plain terminal to make sure I had the username/password strings in the script correct. Symptoms: Modem dials out, connection is made, and shortly thereafter, is dropped. It seems that either A) All of the different methods of dialing out fail to recognize the user/pass strings and input the correct name/pwd or B) Once the name/pwd has been entered, PPP fails to initialize (or whatever it does) and the ISP drops the connection since PPP doesn't volunteer itself.

System - AMD 900mhz, Ubuntu 6.06, modem appears to be well supported as it dials out and responds to all test strings.

I reinstalled, using Edubuntu 6.06 and found the same symptoms/problems.
I only recently learned of using Plog with Pon and Poff, so I don't have a log for you yet, but will asap. If there is a way to log with the other methods, such as wvdial, please let me know. I intend to install 6.10 tonight and see if the problem is better, but hold little hope.

This presents several problems for Ubuntu, chief among them is this cripples Ubuntu for users in most third world nations and large parts of the U.S. of A.
In addition, I was disappointed to find that nowhere in the installation process was there any mention of dialup or an attempt to set it up. This does not bode well for less advanced users, or users in the unfortunately-still-prevalent dialup land. I realize that everyone wishes dialup would die for good, myself included, but it's here to stay for a long, long time. In order for Ubuntu to be usable for all, dialup MUST be made to work, especially if development is confident enough for Long Term Service.

Thanks again for the read! I hope I move back to high-speed land soon, but until then, I'd really like to be networked in Ubuntu again. Love that OS!

--Matt

---

### Post by mpk23 on 2007-02-09
Wow - Quiet in here when you talk about dialup and ppp.

Found this  thread with pretty good insight,


[http://ubuntuforums.org/showthread.php?t=191455](http://ubuntuforums.org/showthread.php?t=191455)

Says Howiear: 
"http://mppe-mppc.alphacron.de/
 this site gives some insight into these issues. The Kernel that is included in Dapper Drake does have the MPPE module compiled in it but from all I can surmise from my endless search it doesn't have the MPPC modules compiled into it. I haven't found a source for these modules and I'm not well versed in the compiling of Kernal myself."

Mpk23 again: I am also not well versed in kernel compiling, I've actually tried it a handful of times and it's never worked. Can someone walk me through how (in Ubuntu 6.10) I would add the MPPC module and recompile the kernel, without adding too many packages, since without networking, I can't apt-get anything that wasn't on the CD, I have to ferry all home from work on a thumb drive or migrate it from my dialup winxp install.

I hope that eventually I can report that this fixed dialup and PPP in ubuntu.

Thanks again! Hope I get some takers from the kernel-compiling club.

---

### Post by Matchless on 2007-02-18
How a look at this:
[http://ubuntuforums.org/showthread.php?t=307155&highlight=kppp](http://ubuntuforums.org/showthread.php?t=307155&highlight=kppp)

---

