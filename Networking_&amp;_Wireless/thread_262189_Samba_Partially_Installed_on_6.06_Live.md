---
title: "Samba Partially Installed on 6.06 Live"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by Mr Wrath on 2006-09-21
I just finished installing the Dapper Drake 6.06 from the Live CD on a test machine and noticed that part of the samba package is not installed (samba daemons for example {init.d/samba}).  I did an aptget for the samba package and reinstalled it on the machine.  Everything works fine now, but the question is; was part of the package left out for a reason?  If there has been talk about this, please let me know so that I may catch up.

---

### Post by Iowan on 2006-09-21
I neglected to notice when I installed 6.06 whether Samba's client package came pre-installed, or if I had to add it.  I see there's a /etc/samba/smb.conf file on this workstation that I haven't set up yet, but no daemons running (or in /etc/init.d/).

---

### Post by Mr Wrath on 2006-09-22
That is what I was refering to...the daemons are not with the install.  I am going to do another install a little later to see what else exactly is missing, but the reason I am bringing this topic up is, with the growing popularity of Linux (slow, I know); Ubuntu to be more specific, people are going to be connecting other machines to this one (Ubuntu) as their small network.  Most people have more than one computer at their home office and/or small office, and the home/small offices that will be trying out 'Linux' will try to connect to their other machines (primarily Windows) in the home/small office environment.  This is where the importance of the whole samba package comes in.  They'll read about samba connections, how it works, and how to configure, but as they research the latest Ubuntu, they will come to understand 'hey, the samba package comes with the installation.'  When they configure and run their newly founded connection to, well, just about anything, its going to just...not work.  The outcome of the scenario will be a little frustration, and a constant thought of what else may not work on this operating system.  'Linux', in general, has enough challenges with keeping some of todays ventures from returning back to the crappy side of the information technology world which is Windows.   This all leads me back to my original question...why is part of the samba package missing?  Was there an error when the creation of the installation disk was created?  I don't mean to offend or anger anyone in anyway, I am just thinking about the people that will venture away from Windows to do their daily computing needs.  If they use it, like it, and tell a friend...that is more help to the whole Linux community, and the more people there are to the 'Linux' community, the more companies will want their involvement in and around the open source way of life.  I have come to a greater understanding of computers and how they work due to Linux (more specifically Debian & Ubuntu).  SORRY, I'M JUST LETTING OUT IDEAS...OR YOU CAN CALL IT RANTING.  MAY BE I'M PUTTING TOO MUCH INTO IT, won't be the first, well, maybe for this forum.  If anyone thinks I am going about this the wrong way or that I am not making any sense...please let me know.

---

### Post by Mr Wrath on 2006-09-22
edit:  I will be constantly checking out this thread...Please any and everyone with any ideas and/or comments at anytime...please speak up.  I am just looking for some insight.

---

### Post by Mr Wrath on 2006-10-11
***chirping of a cricket***

---

### Post by Iowan on 2006-10-11
I can't speak for the developers as to why/what packages are included on the CD. I know one CD is pretty minimal for a full OS these days - albeit other distros have the OS on one CD and a multitude of packages on the other(s). 
> Most people have more than one computer at their home office and/or small office, and the home/small offices that will be trying out 'Linux' will try to connect to their other machines (primarily Windows) in the home/small office environment 
I suppose the half-full vs half-empty glass affects whether you view Samba as half-installed or half-omitted.  The client-side lets Ubuntu connect with those other (primarily Windows) machines. Like the PDF viewer for Adobe, it lets you see someone else's work.  If you need the full package, you can get it.

---

### Post by Mr Wrath on 2006-10-16
> **Iowan said:**
> I can't speak for the developers as to why/what packages are included on the CD. I know one CD is pretty minimal for a full OS these days - albeit other distros have the OS on one CD and a multitude of packages on the other(s). 
 
I suppose the half-full vs half-empty glass affects whether you view Samba as half-installed or half-omitted.  The client-side lets Ubuntu connect with those other (primarily Windows) machines. Like the PDF viewer for Adobe, it lets you see someone else's work.  If you need the full package, you can get it.

...good point, I did not think about it like that.

---

