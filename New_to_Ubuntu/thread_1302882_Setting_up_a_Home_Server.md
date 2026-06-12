---
title: "Setting up a Home Server"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by drdeath691 on 2009-10-27
I have an old computer that i want to convert to a dedicated file server. I want to use 1 Hdd for the OS (Ubuntu Server) and then use 3 1.5 TB  HDD in a Software Raid 5 setup. Is this possible? I have limited ubuntu expereince but I can follow Guides well ;)... Any help would be great before I jump in and try this.

Thanks in advance....

---

### Post by CharlesA on 2009-10-27
Yeah, that's possible. You can use mdadm.

Here's a howto: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by shadow120 on 2009-10-27
there are tons of guides on this just have to stfw here are a few that look good
[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)
[http://blog.ari.is/index.php/2008/07/home-file-server-ubuntu-samba-raid-5/](http://blog.ari.is/index.php/2008/07/home-file-server-ubuntu-samba-raid-5/)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by drdeath691 on 2009-10-27
Would it be easier to use ubuntu or ubuntu server for my setup. I will be connecting to the server using 3 window 7 PC's. I can remote desktop into it from Windows or is the Server Edition almost the same just controlled through an SSH interface. Meaning can I install files etc or is the Server edition all terminal work. Can I go ahead and set up the os on the primary HDD and install the raid via software once my HDD's drive come in, or should I wait and do it all at once?

---

### Post by stlsaint on 2009-10-27
for a server setup i recommend going with server edition and yes you will use the cli unless you use something like webadmin,(i use cli tbh so no exp with gui apps for server) and when it comes to using win 7 to manage computers yes you will be using ssh(looking into putty for windows) but since win7 cant read ubuntu filesystems im not sure how that would work, maybe make hdd ntfs on servers and looking into SoftwareRaidSetup or FakeRaidSetup
for raid settings.

SoftwareRaid=https://help.ubuntu.com/community/FakeRaidHowto

FakeRaid=https://help.ubuntu.com/community/Installation/SoftwareRAID

---

### Post by bribera on 2009-10-27
If the clients are all Windows, I'd assume he's setting it up as a dedicated samba server.

That said, you can go ahead and install the operating system on the primary hard drive. You can even install and configure samba at this point.

Once your drives arrive, you can set up the RAID and edit your fstab to mount the samba shared directory on that partition.

---

### Post by drdeath691 on 2009-10-27
yea its going to be a dedicated file server but i want to run sabnzb,episode butler and a few other things on it. I ssume this will be from the primary hdd. This only thing I'll be accessing with the Windows PC's is the samba shares (Windows Media Center, itunes etc...)

Thanks for everyones help thus far.

---

### Post by shadow120 on 2009-10-27
> **drdeath691 said:**
> Would it be easier to use ubuntu or ubuntu server for my setup.

i would install the desktop then add the programs you need.  that way you have the gui to set eveything up

---

### Post by 3rdalbum on 2009-10-28
Hmm... my server runs Ubuntu Desktop. I'd suggest Ubuntu 9.10 desktop as it comes with Palimpsest (System > Administration > Disk Utility) that can help you set up a RAID.

---

### Post by Bender Rodriguez on 2009-10-28
> **3rdalbum said:**
> Hmm... my server runs Ubuntu Desktop. I'd suggest Ubuntu 9.10 desktop as it comes with Palimpsest (System > Administration > Disk Utility) that can help you set up a RAID.
 
My advise too. Unless you know you're way around server setup then go with the desktop edt. and have the gui tools help setup. On the other hand if you decide to use your server for more than just filesharing, like for instance a webserver, some DHCP3-servering, or perhaps mail setup - then you should definetly consider going server edt, where you can from the installation, setup everything having all the tools you need. Also you can still install X for desktop gui stuff afterwards..

---

### Post by MrWES on 2009-10-28
> **Bender Rodriguez said:**
> My advise too. Unless you know you're way around server setup then go with the desktop edt. and have the gui tools help setup. On the other hand if you decide to use your server for more than just filesharing, like for instance a webserver, some DHCP3-servering, or perhaps mail setup - then you should definetly consider going server edt, where you can from the installation, setup everything having all the tools you need. Also you can still install X for desktop gui stuff afterwards..

I definitely agree with that logic. I felt the same way when I was deciding on how to setup my home server. However, I decided to go strictly with the server installation and I'm very glad I did. My Ubuntu/Linux knowledge has grown 10 fold because I was more-or-less forced to learn the command line to run my server. 

If it's a project where you have the time and energy to setup a traditional command line server installation ([http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")) I would highly recommend it, as the knowledge gained will certainly make it worthwhile.

~Bill

P.S. the howtoforge link is the exact one I used. I went with 8.04 because it was LTS and very stable.

---

