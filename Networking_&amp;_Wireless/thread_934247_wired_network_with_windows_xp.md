---
title: "wired network with windows xp"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by danylong on 2008-09-30
Hey
ive followed several tutorials all of them ended unsuccessfully
what I am trying to do is set up a samba network so that I can share files with read/write access on each computer
ex. share music on ubuntu view files and edit them on the windows box
also share music on windows and read/write them on ubuntu
I have gotten to the point where i can read all the files on the windows box in ubuntu but not write them
Also i cannot see ubuntu from windows
any assistance is greatly appreciated
thanks

---

### Post by superprash2003 on 2008-09-30
well firstly ensure that both pcs are able to ping each other and that no firewall is blocking.. also ensure that "simple file sharing" in disabled.. go to windows explorer.. view->folder options .. and there disable "simple file sharing".. and then you would have options to allow write access..
  there could be some mistake in your samba setup..
For reference : setting up samba server [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by Another Monkey on 2008-09-30
As superprash2003 says, you need to make sure that Windows is set-up correctly first, no firewall causing grief and ping works (a very basic "Hello!" check between computers).

You also need to have samba installed (adding Ubuntu to the same workgroup as windows and creating a share should be enough).

You will almost certainly have to access directly via IP and the share name (at least from Ubuntu) e.g. "smb://windows.ip/your-share" as there is a [bug in Gnome]("http://bugzilla.gnome.org/show_bug.cgi?id=522494").

There is a [this thread]("http://ubuntuforums.org/showthread.php?t=202605") which contains a lot of info.  Bar the bug I mentioned, it is pretty easy to set up and get going (so don't go crazy trying to get network browsing working).  Although you will need to consider security etc. at some point.

I found [this article]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting") really helpful in making sure I did things right.

---

### Post by stimpyaw on 2009-01-25
THANK YOU!! for the info.  I was knocking my head against the wall for the longest time.  Turned off the "simple file sharing" and followed the setting up samba server link and that worked. WOOHOO!! Ubuntu RULES!! :D


> **superprash2003 said:**
> well firstly ensure that both pcs are able to ping each other and that no firewall is blocking.. also ensure that "simple file sharing" in disabled.. go to windows explorer.. view->folder options .. and there disable "simple file sharing".. and then you would have options to allow write access..
  there could be some mistake in your samba setup..
For reference : setting up samba server [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

