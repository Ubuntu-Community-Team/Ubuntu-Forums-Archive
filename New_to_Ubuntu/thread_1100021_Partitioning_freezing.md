---
title: "Partitioning freezing?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by StripedVengeance on 2009-03-18
I'm having an issue when trying to install Ubuntu 8.10. 

A few steps into the guided installation process, it brings me to the partitioning section. All is well, and I select how much of my hard drive I would like to partition for Ubuntu usage.

Well, after selecting how much of my hard drive to partition, and when I start the partitioning process itself, the process seems to freeze. It never goes over 0%, and the process never advances from "resizing partition". I've waited for as much as 20 minutes for a sign of change in the partitioning process with no luck. 

Am I just being impatient? Do I need to manually partition? If so, how do I go about doing such a thing? 

Sorry if this post seems to be a bit noobish, or if I've brought something up that there is a guide for in another section of the site. I'm a bit frustrated, and just want to figure this out. 

Thanks in advance. :)

---

### Post by Botbob89 on 2009-03-18
What are you using to install? Wubi? Or something else?

Also, what OS are you trying to partition with?

---

### Post by StripedVengeance on 2009-03-18
I'm booting straight from the CD using the guided partition process, and I'm planning on dual booting with Vista Home Basic 32 bit.

Also, the CD was burned using InfaRecorder and it was burned from an image downloaded via BitTorrent, if that makes any difference.

---

### Post by Helios1276 on 2009-03-18
Use Vista's partition manager to shrink it but make sure and defrag **alot**. also you *may* have trouble getting it to shrink:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by StripedVengeance on 2009-03-18
Well, I had a friend guiding me through the installation process a while ago, and I actually partitioned my hard drive then, and it's just sitting here unused. Is there a way I can use that instead of the standard partition process it puts me through? If so, how do I do that? 

~newbish~

---

### Post by kansasnoob on 2009-03-18
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by StripedVengeance on 2009-03-19
Okay, so I woke up today after checking out the guide last night and decided to give it another go to see if I could get things rocking.

Fired up Ubuntu, went through steps one through three, and then comes four. 

I read the guide, and it states that at the partitioning stage, there should be an option to use all "unallocated space" if I recall, well, here's the issue. My options at that window are 


"Guided - Re-size partition" 

"Guided - Use Entire Disk" 

"Manual"

Now, according to the guide, the "use all unallocated space" should be number two in that line-up, and it obviously isn't. 

Is Ubuntu not registering that there's that open partition there, or is there something in the guide that I possibly missed?

---

### Post by Helios1276 on 2009-03-19
did you shrink Vista using it's partition manager? If so you should be able to install Ubuntu into the unallocated space. Hit 'manual' and you should see it.

---

### Post by StripedVengeance on 2009-03-19
Okay, when I try to go in and manually select the pre-partitioned drive, it says...

"No root file system is defined.

Please correct this from the partitioning menu."

So I open up the "Edit Partition" window, and I've got numerous things to pick from. I of course didn't do too much with them because I'm not 100% sure what they mean. Help? 

I played around with the options in the edit partition window, and tried to get something to go through, and even with what I had done to it, it wouldn't go. Help?

---

### Post by StripedVengeance on 2009-03-19
Bump?

I went through trying to get through again, and I went through the "Edit Partition" menu to try to configure it to get rid of the root file system issue. I set it up with EXT3, and got the same root file system error. I'm not really sure what else I can do. Am I missing something here?

---

### Post by Helios1276 on 2009-03-19
You need to define a root (/) partition, home partition and a swap partition.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by StripedVengeance on 2009-03-20
Yeah, I got it worked out. 

I went back and shrunk the other area I had created earlier, and went back through the install, and the option to use all unallocated space was there (yay). 

It looks like the issue I was having was that the partition made prior to this whole escapade was already dedicated as a drive, not unallocated space. :(

Either way, we're good now, but I do have a 30 gig disk gathering dust. Not sure what to do with that puppy.

---

