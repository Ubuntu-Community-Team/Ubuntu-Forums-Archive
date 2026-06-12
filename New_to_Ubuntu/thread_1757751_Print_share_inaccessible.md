---
title: "Print share inaccessible"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by bradfordly on 2011-05-13
I couldn't find anything about this that worked for me so maybe somebody can help me. Im trying to connect a ubuntu 11.04 machine to a windows 7 printer. I actually got the printing to work fairly easy before this. In 10.10 i just went to printing-windows printer via samba and then browsed for the printer. I found it easily then installed the driver and everything worked great. I reinstalled it several times this way when i reinstalled 10.10 over a few times. Ive tried the same process in 11.04 but when i verify the printer it says print share inaccessible. I changed nothing on the windows 7 computer. Any ideas?

---

### Post by MiD-AwE on 2011-05-27
I'm experiencing the same issue. It's almost scandalous all the security holes I've opened in windows 7 just to get this working and still the only thing I can't do from the Ubuntu 11.04 is print. :( If you get it to work please say so.

Thanks

---

### Post by audiomick on 2011-05-27
Don't know if it will help, but the guru of all things Samba lives here:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by MiD-AwE on 2011-05-28
Thanks, as soo as I have time to try I'll know where to look. :popcorn:

---

### Post by bradfordly on 2011-06-04
I checked out the page but it seemed mostly related to file browsing and not printing. I also tried a live cd of 10.10 and i got it to work. But still not 11.04. :(

---

### Post by Laforge129 on 2011-06-04
> **bradfordly said:**
> I checked out the page but it seemed mostly related to file browsing and not printing. I also tried a live cd of 10.04 and i got it to work. But still not 11.04. :(

I'm curious is it IP Based or directory based printer?  I would think if it was an IP based all you would have to do is point samba to the IP of the printer and it should be able to find it!

---

### Post by garvinrick4 on 2011-06-04
Look at your printer location Like: smb//:WORKGROUP/XXXXX
What ever it is in the working install of 10.10 and down: or the live cd. Write down under printer preferences:
In URL type in "localhost:631" hit enter, Will go to Cups and you can install
printer from there same as with printer in ubuntu and you can put in correct
URI of printer. 11.04 comes up with a different one, slightly have to look closely.
Have not figured out why but a lot of users had the same problem in network samba workgroup printer.

---

### Post by bradfordly on 2011-06-06
> **garvinrick4 said:**
> Look at your printer location Like: smb//:WORKGROUP/XXXXX
What ever it is in the working install of 10.10 and down: or the live cd. Write down under printer preferences:
In URL type in "localhost:631" hit enter, Will go to Cups and you can install
printer from there same as with printer in ubuntu and you can put in correct
URI of printer. 11.04 comes up with a different one, slightly have to look closely.
Have not figured out why but a lot of users had the same problem in network samba workgroup printer.


Thanks a ton! I finally got it to work by copying the location from the administration-printing gui and then pasteing that into cups and setting it up there. :):)


They should really fix this so it works under the gui.  What is so different between 10.10 and 11.04 that it doesnt work the same?

---

### Post by garvinrick4 on 2011-06-06
> They should really fix this so it works under the gui.  What is so  different between 10.10 and 11.04 that it doesnt work the same?Do not really know just found a fix. Why don't you sign up for a launchpad account upper right of Ubuntu Forums page and report your first bug? Problem with Network Workgroup and Samba  printer and workaround.
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by dogday911 on 2011-07-06
Your solution pointed me at the current underlying problem, for me anyway.  The share name in windows had spaces and the location for the printer on the network found by natty translated those spaces as 20 and not presumably as %20.

From cups before working :

smb://WORKGROUP/HPM587UK/Canon20Inkjet20iP460020series



So all I did was change the share name in windows to remove any spaces and it worked.

From cups after changing windows share name to ip4600:

 smb://HPM587UK/ip4600

---

### Post by MiD-AwE on 2011-07-07
> **dogday911 said:**
> Your solution pointed me at the current underlying problem, for me anyway.  The share name in windows had spaces and the location for the printer on the network found by natty translated those spaces as 20 and not presumably as %20.

From cups before working :

smb://WORKGROUP/HPM587UK/Canon20Inkjet20iP460020series

So all I did was change the share name in windows to remove any spaces and it worked.

From cups after changing windows share name to ip4600:

 smb://HPM587UK/ip4600

Thanks, very useful. :)

---

### Post by AVH on 2011-07-08
Never mind. I wasn't reading closely. Deleting the spaces in the share name in WINDOWS 7 does work.

Thanks

---

