---
title: "Ubuntu host, Windows XP guest, shared folder fails in VirtualBox"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by mmasroorali on 2010-06-17
Dear All,
I have been successful with this before, but somehow, after a fresh full installation, the same procedure is not working.

I have VirtualBox OSE installed in Lucid Lynx machine. Windows XP has been installed as a guest. To create the a shared folder, previously I followed the procedure in [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12), and it worked in the first try. This is for Vista, but it worked for me in XP.

Now, this time, it does not work. Here is my procedure.

I have guest additions installed properly.


Network is properly enabled. See image (network.png).

Shared folder has been created and assigned in VirtualBox. See image (sharedfolder.png).

In Windows, I tried both the graphical interface and command line, both failed. See images (mapnetdrive.png and commandnetuse.bmp).

I am clueless here, can not even determine how do I start diagnosing the problem. Any suggestion will be appreciated.

---

### Post by _Mark_ on 2010-06-17
You're problem is in the first screenshot, Network NAT this means the guest is a self contained network if you look at both guest and host IP's they will be on different subnets no chance of talking in any form

host only is probably what you need, so then the host and guest will be on the same subnet, see this post explaining network setup [http://ubuntuforums.org/showpost.php?p=6122142&postcount=3](http://ubuntuforums.org/showpost.php?p=6122142&postcount=3)

---

### Post by mmasroorali on 2010-06-18
> **_Mark_ said:**
> You're problem is in the first screenshot, Network NAT this means the guest is a self contained network if you look at both guest and host IP's they will be on different subnets no chance of talking in any form

host only is probably what you need, so then the host and guest will be on the same subnet, see this post explaining network setup [http://ubuntuforums.org/showpost.php?p=6122142&postcount=3](http://ubuntuforums.org/showpost.php?p=6122142&postcount=3)

If that is my problem, how come the procedure in [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12) worked for me previously? 

The host only option did not work, by the way.

---

### Post by rewyllys on 2010-06-18
> **mmasroorali said:**
> . . . . I have VirtualBox OSE installed in Lucid Lynx machine. Windows XP has been installed as a guest. To create the a shared folder, previously I followed the procedure in [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12), and it worked in the first try. This is for Vista, but it worked for me in XP. . . . 

To share a folder between Lucid and XP, I suggest the following workaround: 

In Lucid, open an account with Dropbox

[https://www.dropbox.com/home#/](https://www.dropbox.com/home#/)

(Such accounts are free up to 2GB.)

Take the folder you want to share, and place it within your Dropbox folder in Lucid.  

In your Windows XP inside VirtualBox, go to dropbox.com and tell Dropbox that you already have a Dropbox account, which you now want to share with yourself working in XP.

You'll then find the shared folder available, and automatically constantly synchronized, in both Lucid and XP.

I have this kind of arrangement working just fine with: (1) Lucid on my laptop, (2) XP inside VirtualBox on my laptop, (3) Lucid on my desktop, (4) XP inside VirtualBox on my desktop, and (5) Vista on my desktop when I dual-boot--rarely--into Vista rather than Lucid.

---

### Post by mmasroorali on 2010-06-18
> **rewyllys said:**
> To share a folder between Lucid and XP, I suggest the following workaround: 

In Lucid, open an account with Dropbox

[https://www.dropbox.com/home#/](https://www.dropbox.com/home#/)

(Such accounts are free up to 2GB.)

Take the folder you want to share, and place it within your Dropbox folder in Lucid.  

In your Windows XP inside VirtualBox, go to dropbox.com and tell Dropbox that you already have a Dropbox account, which you now want to share with yourself working in XP.

You'll then find the shared folder available, and automatically constantly synchronized, in both Lucid and XP.

I have this kind of arrangement working just fine with: (1) Lucid on my laptop, (2) XP inside VirtualBox on my laptop, (3) Lucid on my desktop, (4) XP inside VirtualBox on my desktop, and (5) Vista on my desktop when I dual-boot--rarely--into Vista rather than Lucid.

Thanks a lot. I will try it, but not with dropbox, rather with SpiderOak, to which I subscribe.

---

### Post by _Mark_ on 2010-06-18
> **mmasroorali said:**
> If that is my problem, how come the procedure in [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12](http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12) worked for me previously? 

The host only option did not work, by the way.

OK but my point still stands if the guest and host are on different subnets they will never be able to talk, unless Vbox get's around that somehow

Just noticed from you're screenshots when you are mapping the drive in windows you are using \\vboxsvr\VBS where are you getting that server name from? and how is the guest resolving that to the host's IP address?

Try using the IP address of the host rather than the server name

---

### Post by mmasroorali on 2010-06-19
> **_Mark_ said:**
> OK but my point still stands if the guest and host are on different subnets they will never be able to talk, unless Vbox get's around that somehow

Just noticed from you're screenshots when you are mapping the drive in windows you are using \\vboxsvr\VBS where are you getting that server name from? and how is the guest resolving that to the host's IP address?

Try using the IP address of the host rather than the server name


Yes, vbox can make them talk, when I ping from guest (10.0....) to host (172.16......), the ping is successful. So, vbox knows the way to make them talk.

The name vboxsvr is suggested by vbox, see the attached image. Guest additions have been installed.

If the shared folder is shared as samba share from host, then it can be mapped to guest (using the 172.. IP address). But this is not the way I did it previously.

---

### Post by mmasroorali on 2010-06-19
It works!!!

The step I had forgotten is you need to install Guest Additions in the guest as well after it had been installed in the host.

---

### Post by saneojseje on 2010-07-20
> **mmasroorali said:**
> It works!!!

The step I had forgotten is you need to install Guest Additions in the guest as well after it has been installed in the host.

This is also what I missed! Now it's okay! Thanks!

---

