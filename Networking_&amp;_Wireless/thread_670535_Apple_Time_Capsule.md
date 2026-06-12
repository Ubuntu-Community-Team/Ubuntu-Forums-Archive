---
title: "Apple Time Capsule"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by ziofil on 2008-01-17
Hi everybody! ):P
I read about apple's new time capsule wireless backup device.
Does anybody know if it's compatible with ubuntu?
Or (better) does it exist something similar without spending 299€?
Thank you in advance!

PS I already know flyback, but it works with wires as far as I know, and we have 3 laptops at home... Thanks again

---

### Post by Mithrilhall on 2008-01-17
If wireless is working already for you why not just backup your data with something like Synkron ([http://synkron.sourceforge.net/)?](http://synkron.sourceforge.net/)?)

---

### Post by ziofil on 2008-01-26
i'll try it, thanks!
does it work like flyback? (flyback was good!)

---

### Post by DanWash on 2008-02-16
I'm gonna get one - coz I'm all mac'd up, so if it doesn't play nicely with Ubuntu I can just wait to figure it out.  I'll let you know how it goes.

---

### Post by ytene on 2008-03-23
Hi There...

I have a 1Tb Time Capsule and can confirm that it is readily accessible from both 7.10 and 8.04 Beta [64-bit versions of both releases].

I am sure that there are many ways of accessing the drive, but the one I found to work for me goes something like this.

1. Client Side Software
You need to install the smbfs and smbclient software, to enable your machine to talk the "Server Message Block" [now known as CIFS] protocol. You can either do this via apt-get or Synaptic, as you prefer.

2. Make a Mount Point
Just the usual, really. Go to /media and create a suitable directory to act as a mount point for the remote file system.

cd /media
sudo mkdir capsule

3. Interactive Mount Statement
The one that worked for me goes like this:-

sudo mount.cifs //192.168.1.20/"Tom Smith's Time Capsule"/tom /media/capsule -o pass=passw0rd

where 

i. the IP Address is the one that you assign to the Time Capsule using your Apple AirPort Utility on a Mac,
ii. The 'directory' name enclosed in double quotes is the name assigned to your Time Capsule when it it set up on the Mac - see how the volume appears listed on a Mac machine to derive this,
iii. /media/capsule is the name of the mount point that you selected,
iv. passw0rd is replaced with whatever password you elected to use during the Airport configuration. Apple give you two options here. You can either use the same password as your Wireless Network password [generally a bad idea] or you can select a different one [obviously much more sensible].


I'm about to write a slightly more detailed how-to for this, since I've also managed to set my environment up such that any Apple lossless audio recordings ripped from my Mac Mini are automatically stored on the Time Capsule [where there is plenty of space] and with the TC networked to my Linux boxes [such as the one I'm using right now] I can also stream that MPEG-4 content directly into Amarok [via the Xine engine] and enjoy my entire CD collection in lossless format.

What's even better, using Apple iTunes under OS/X to transcribe the CDs means that it solves the problem of "copy protected" material that otherwise Linux transcoders such as grip would traditionally b0rk at. 

So by all means go for a Time Capsule - they're quiet and fast - but do remember that you'll need a Mac to set one up. 

Also, for what it's worth, they run *incredibly* hot. Like, uncomfortable to the touch...

Hope this helps.

Best Regards to One and All

---

### Post by yeahdef on 2008-04-07
Hi thanks for the write up that really helped me out.
I now have another related issue... (thats how it always goes i guess)
I would like to have an external drive connected to the time capsule and have it show up as well on my machine.  do you have any tips on this one?

---

### Post by yeahdef on 2008-04-17
ok i figured my last question out myself

---

### Post by gadgetbox on 2008-04-19
Thanks for the post on how you managed to mount your timecapsule drive on Ubuntu. I seem to be unable to get the same result!

I'm getting a 'mount error 6 = No such device or address' message.

I've confirmed the IP address of the TC, the name and the password, so I'm not sure what the problem is. I have smbclient and smbfs installed via synaptic.

I'd appreciate any help on this, let me know if you need more information.

Thanks!

---

### Post by gadgetbox on 2008-04-19
....and nevermind...I just figured it out. Thanks again!

---

### Post by ytene on 2008-05-05
For those of you who are still experimenting with this and would like a version of the mount that is "permanent", ie something that comes back with each ubuntu reboot, try something similar to this in your /etc/fstab :-

//192.168.1.39/TimeCapsule/fred /media/capsule cifs password=pa55w0rd,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

where

the IP Address is that assigned to your Time Capsule. The name "Time Capsule" is set on that box. [ I used my Mac Mini to do this]. 

fred is the name of the top level directory that connections to the Time Capsule link to...

Hope that is a little more helpful to everyone.

---

### Post by Excelsi0r on 2008-05-09
Excellent tip - it really helped me out as I am a new Ubuntu user.

I use KTorrent and I would like my completed downloads to be automatically moved to my Time Capsule. This now works thanks to the fstab line. However, I am having one minor problem. KTorrent is unable to "rename" nested folders, i.e KTorrent cannot move folders within folders from my home directory where downloads are stored temporarily until they are completed, when KTorrent moves them to the Time Capsule. Is there a way to augment the line so that folders within folders can be created by Ubuntu on the Time Capsule?

---

### Post by eddielgarcia on 2008-05-18
It seems I have been stuck with this error for some time now:

[I]mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)[/I]

I can't get my time capsule HD to mount and I don't know what I may be doing wrong but this is what i use in the terminal:
[I]
sudo mount.cifs //10.0.1.1/Capsule/Home /media/capsule -o user=Eddie,pass=password[/I]

That is my actual address for my TC and correct directory that I have created within the capsule.  I did create a mount point inside the media directory called capsule and my password is actually something else not really "password" for posting reasons I displayed it as password.  I also installed the appropriate clients using Synaptic so I guess I must be missing some minute detail that I am not seeing.  If anybody can offer some help it would be greatly appreciated!

---

### Post by Dareus on 2008-05-18
I bought a 500Gb one, I got various problem mountin it using the simple "mount". This means that I can't use in a useful way /etc/fstab, to have a permanent mount I had to write a script to put in /etc/rcX.d/ with both dhclient to set the network up and mount.cifs to mount the device.

The only problem I have now is to use my wireless card, due to encryption used.
I'm actually using the only WEP (I prefer WEP over WPA) setting I can which has a TKIP-AES compatibility or something like that.
The problem is that it seems not to be compatible with plain WEP :)

---

### Post by ziofil on 2008-05-25
Hi! in the end I bought a big HD, mounted it in my pc case, installed samba and got it working.
Now i can use it with wirelessly my macbook pro like it's time machine, and the other 2 laptops (mom's and dad's) use it via flyback! sooo happy! :)

---

### Post by madman92 on 2008-05-26
To fix the problem 
> mount error 6 = No such device or address
Refer to the mount.cifs( manual page (e.g.man mount.cifs)

go on a mac that is using timecapsule and do an ls on /Volumes
You should see your harddrive, any other peripherals you have connected, and the timecapsule. Use the name you get from the ls.

sudo mount.cifs //10.0.1.1/[ls name]/[dir] /media/capsule -o user=Eddie,pass=password

---

### Post by danielrs on 2008-07-11
Thanks guys, this worked for me, but I have a problem with special chars like: â. Does anyone know how to solve this problem?

---

