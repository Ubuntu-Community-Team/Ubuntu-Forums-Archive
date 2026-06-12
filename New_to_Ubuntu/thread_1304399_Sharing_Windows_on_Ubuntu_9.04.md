---
title: "Sharing Windows on Ubuntu 9.04"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by mrapoc on 2009-10-29
Hey guys

I understand that 9.10 is dawning and I will be upgrading in the next week, but for some reason, I cannot get Ubuntu 9.04 to "see" or "connect" to my Windows 7 share (Videos folder "E:\My Videos") and a data folder ("F:\Data Disk 1").

I click on network in ubuntu, and Windows network and my PC name comes up. Double click the PC name and a prompt comes up for username, domain (workgroup) and password. I have tried all of my windows login accounts to try and connect and none work. 

I can also go into Windows network, this then shows "Workgroup". Double click and the same happens. So technically I am not getting to the stage where it will show my shares?

All windows 7 settings are on default but it "should" be sharing?

---

### Post by dgoosens on 2009-10-29
lol
Windows does not share anything by default....

that's how one sees things over there at M$...
(and not just about the stuff on your computer)

---

### Post by mrapoc on 2009-10-29
I have right clicked each folder, set to share for each user and in network centre network discovery etc. is on.

So basically what worked in vista doesnt now?

---

### Post by camon on 2009-10-29
same problem here.

it seems that this is a problem with win 7 and ubuntu

has someone solved it yet?

---

### Post by Bölvaður on 2009-10-29
are you trying to get to a file that is on the same computer, a local computer (on your lan) or some computer on the internet?


if it is the same computer then look into fstab to automount

if it is on lan look at samba

if it is over the internet you might want to look at dropbox or ftp server


it's not like you are the only one that have wanted to what ever you are trying. I bet there are few hundreds tutorials on the internet if you google them.

---

### Post by camon on 2009-10-29
what i want to do is the simple share process. 

Share a folder on windows 7 and at ubuntu access that folder, with both computers in the same LAN

---

### Post by dgoosens on 2009-10-29
Google is your best friend:

[http://www.rizwan-rafique.com/share-folders-between-windows-xpvista7-and-linux-machines](http://www.rizwan-rafique.com/share-folders-between-windows-xpvista7-and-linux-machines)

---

### Post by camon on 2009-10-29
did that and it says

mount error(13): Permission denied

Tried everything, disabled password, etc and no go.

---

### Post by Bölvaður on 2009-10-29
> **dgoosens said:**
> Google is your best friend:

[http://www.rizwan-rafique.com/share-folders-between-windows-xpvista7-and-linux-machines](http://www.rizwan-rafique.com/share-folders-between-windows-xpvista7-and-linux-machines)

just like I said, samba.

man sharing with windows is a pain. why dont they implement nfs

---

### Post by theozzlives on 2009-10-29
In Windows 7 you have to set your credentials for each machine. I have yet to find out how to share from Windows (aside from typing smb://<IP Address>/<share> in Nautilus). I'm attending a Windows 7 conference on the 4th, maybe I'll have answers then.

---

### Post by camon on 2009-10-29
i can't even that way it keeps asking for my password. I don' have one :S

---

### Post by mrapoc on 2009-10-29
I have set passwords for those I am trying to access the shared folder with and still no avail. It is on the same lan, so you think installing samba is the way forwards? 

I mean it worked fine before with vista - didnt have to install anything. I shall try again with 9.10, and have seen others having this problem (asking for password  yet not accepting any!)

Then ill try samba..
thanks

---

### Post by ghstridr on 2009-10-29
Windows 7 has a new method of sharing called a Home Group which works over IPv6.  Exactly how they have implemented that, I'm not sure.
The other thing to try is turning off the firewall for a short while to see if that is getting in the way.  
I've got a copy of 7 that I'm going to throw into a VM instance and see which way will work best.  My curiosity is piqued.

---

### Post by mrapoc on 2009-10-29
So tis not just me?

I'm not currently using homegroups either so it should surely be standard sharing?

---

### Post by camon on 2009-10-29
yeah not just you same problem here

---

### Post by theozzlives on 2009-10-29
As I said, I'll ask on the 4th at the convention and post a "How To". I have a feeling that Samba may have to revise and conform to the new standard. I have my shares set to Everyone. I don't know how Microsoft translates that, but I always thought it meant EVERYONE.

---

### Post by Jerry N on 2009-10-29
Right this moment I am sharing a couple of Win 7 (RC) folders with an Ubuntu 8.04.3 installation.  It took a couple of minutes to set up the share on Win 7 and then access that share on Ubuntu.  I told Win 7 to "share read/write with everyone".  The Ubuntu machine did ask for a password, I hit ENTER and it then asked for my Ubuntu administrator password.  Gave it that, everything is OK.  I see no problem here other than that it requires a couple more steps than Win XP.  

And to the comment about "Windows doesn't share anything by default":  Of course it doesn't and it shouldn't!  Neither does Ubuntu!  And why should Windows go to NFS?  To help people running Linux? Big deal!  I haven't seen anything wonderful about NFS.

BTW I have never used VISTA so I don't know how it worked there.

Jerry

---

