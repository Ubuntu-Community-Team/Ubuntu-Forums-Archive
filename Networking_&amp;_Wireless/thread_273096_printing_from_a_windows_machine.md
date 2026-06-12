---
title: "printing from a windows machine ?"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by case_uk on 2006-10-07
I know this was started previously, but it was also deleted.

Background info:

I have insalled Ubuntu 6.06 LTS, it is connect to a belkin wireless router via ethernet.  Attached and installed on the linux system is a brother mfc-210c printer / fax / scanner which is working fine.

What i would now like todo is print from my windows machine via the network (this is also connected to the belkin router via ethernet), i have read some other posts that mention samba, i have managed to get a shared folder from my linux machine that shows up on my windows machine in the workgroup view and the linux system shows up when i view workgroup computers so i know they can "see" each other.

I have ran the add printer wizard on the windows machine and it can see the linux sytem, but cannot find / see any printers attached.

I originally set myself alist of things that a linux setup would have todo for me to keep it, use it and learn it ad over the past 2 days along with help from this website and one other, i have managed to achieve almost all of those goals. So i'm hopeful that this can also be resolved.

On the plus side, my wife now wants me to erase her windows box and install ubuntu for her, and a friend of mine is building a pc for a customer and will be dual boting it with windows / ubuntu (this being the primary OS and windows as a backup).

So this is one of my final tasks to complete .... so please someone help me. ](*,)

---

### Post by raphha on 2006-10-07
hi,
put this
```

[printers]
path = /var/tmp
printable = Yes

```

at the end of your /etc/samba/smb.conf

and make sure you have the lines
```

printing = cups
printcap name = cups

```

in the [global]-section of your smb.conf

execute "sudo invoke-rc.d samba reload"

Now you should see the printer from your windoze maschine.

Install a driver there and start printing.
(you may first have to open the shared folder (to be promted for you password) so you are authenticated on your linux maschine. Otherwise printing may fail.

good luck,
raph

---

### Post by lidingtian on 2006-10-07
> **case_uk said:**
> I know this was started previously, but it was also deleted.

Background info:

I have insalled Ubuntu 6.06 LTS, it is connect to a belkin wireless router via ethernet.  Attached and installed on the linux system is a brother mfc-210c printer / fax / scanner which is working fine.

What i would now like todo is print from my windows machine via the network (this is also connected to the belkin router via ethernet), i have read some other posts that mention samba, i have managed to get a shared folder from my linux machine that shows up on my windows machine in the workgroup view and the linux system shows up when i view workgroup computers so i know they can "see" each other.

I have ran the add printer wizard on the windows machine and it can see the linux sytem, but cannot find / see any printers attached.

I originally set myself alist of things that a linux setup would have todo for me to keep it, use it and learn it ad over the past 2 days along with help from this website and one other, i have managed to achieve almost all of those goals. So i'm hopeful that this can also be resolved.

On the plus side, my wife now wants me to erase her windows box and install ubuntu for her, and a friend of mine is building a pc for a customer and will be dual boting it with windows / ubuntu (this being the primary OS and windows as a backup).

So this is one of my final tasks to complete .... so please someone help me. ](*,)

[lidingtian]("http://www.lidingtian.com")
[&#21147;&#39030;&#22825;]("http://www.lidingtian.com")
[&#26426;&#26800;]("http://www.lidingtian.com")
[&#20379;&#27714;&#20449;&#24687;]("http://www.lidingtian.com")

---

### Post by Matchless on 2006-10-08
Hi,
     Just have a read through this, it may have a bit on what you need.
[http://ubuntuforums.org/showthread.php?t=263047](http://ubuntuforums.org/showthread.php?t=263047)

---

### Post by case_uk on 2006-10-08
Thanks to everyone who has posted links and replies, i have it working now and i'm happy.

all thats left is to get my windows machine to use the linux as a server for php & mysql webpages.

---

