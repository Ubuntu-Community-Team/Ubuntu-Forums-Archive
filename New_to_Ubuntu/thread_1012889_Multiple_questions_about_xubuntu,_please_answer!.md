---
title: "Multiple questions about xubuntu, please answer!"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by NonStop on 2008-12-16
My brother has got a free (given by a mate) laptop. The specs are Microsoft Windows 2000 Professional, Service Pack 4, 18GB hard drive (split into a 10 GIG partition for Windows and a 8 GIG partition for data), 391 MB RAM, not sure about the processor, and it some sort of Sony Vaio (on the right hand bottom corner it says PCG-FX105K but on the bottom of the laptop it says model PCG-9536). 

Basically, I was thinking it might be wise to install xubuntu on it, as even with the low specs it would still run well. However, I've never done it before, and so have a few questions.

If I was to do just a normal install, would it wipe out the data from both partitions, would it install onto one only, or what?

What software can be installed onto it? Can openoffice be installed? What about some kind of chatting client which can handle msn chatting?

What are the chances of it working through wireless?

What are the chances of it working through Ethernet?

Finally, what are the chances of it working on this laptop?

---

### Post by nandemonai on 2008-12-16
> **NonStop said:**
> My brother has got a free (given by a mate) laptop. The specs are Microsoft Windows 2000 Professional, Service Pack 4, 18GB hard drive (split into a 10 GIG partition for Windows and a 8 GIG partition for data), 391 MB RAM, not sure about the processor, and it some sort of Sony Vaio (on the right hand bottom corner it says PCG-FX105K but on the bottom of the laptop it says model PCG-9536). 

Basically, I was thinking it might be wise to install xubuntu on it, as even with the low specs it would still run well. However, I've never done it before, and so have a few questions.

If I was to do just a normal install, would it wipe out the data from both partitions, would it install onto one only, or what?

What software can be installed onto it? Can openoffice be installed? What about some kind of chatting client which can handle msn chatting?

What are the chances of it working through wireless?

What are the chances of it working through Ethernet?

Finally, what are the chances of it working on this laptop?

Normal install will give you the option to partition how ever you like, resize, wipe whatever.

Any software you can get for ubuntu will install on xubuntu. (just a different window manager)

Wireless? Pretty good. Depends on the chipset. Again, same as Ubuntu.

Ethernet? I'd say 99%

Chances of it working on that laptop? Well as far as specs go that's fine. Can't comment on 100% hardware compatibility but should be near perfect.

Best of luck ;)

---

### Post by NonStop on 2008-12-16
Thank you. Judging by the amount of problems that are cropping up with this Windows installation, I think installing this is the best decision.

Oh, one big question. Windows doesn't recognise the DVD drive that's connected to the PC. However, if I were to use the xubuntu installation CD, would it? Just when I start up the laptop it goes straight to windows?

---

### Post by Michael.Godawski on 2008-12-16
>  If I was to do just a normal install, would it wipe out the data from both partitions, would it install onto one only, or what?

What software can be installed onto it? Can openoffice be installed? What about some kind of chatting client which can handle msn chatting?

What are the chances of it working through wireless?

What are the chances of it working through Ethernet?

Finally, what are the chances of it working on this laptop?Installation depends on your wishes. You can select manual for additional options or guided: resize existing partitions and use whole drive.

There are over 20000 packages (applications) more or less. Of course OpenOffice will work, it is preinstalled in Ubuntu and can be easily added to Xubuntu.
[http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html) <---- how to install guide
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) <----- aysiu's how to install guide

For msn check out aMSN.

Wireless will depend on the chipset of the wlan card. Usually they work out-of-the-box. Some require heavy tweaking.

Ethernet works.:p it is very unlikely that it is not.

With Xubuntu ( which is running flawlessly) you get a acceptable working machine.

---

### Post by clive littlewood on 2008-12-16
Hi

Install the CD as a "live" first off

This will enable you to check your hardware and network compatability without changing any of the current setup.

To boot the CD from statup you will have to change the Bios to boot from CD.

Hope this helps

Clive

---

### Post by NonStop on 2008-12-16
Thanks for much for the info people. One thing, the laptop seems to boot straight into Windows, a Sony screen appears, then it goes straight into Windows, with the only options being able to change are Windows 2000 Advanced Options Menu; how can I stop this?

Also, I wouldn't be able to try out live CD as windows 2000 isn't recognising the DVD-ROM drive.

---

### Post by BDNiner on 2008-12-16
You have a press a certain key to enter the bios before windows 2000 loads. It is different for each computer. Some use <del> others use <F10>. in the bios u will be able to set which device the computer tries to boot from first. It should be set to the DVD drive not the Hard disk. Then you will be able to boot using the live CD instead of booting into windows 2000. the Bios may also tell you if the DVD drive is not being detected at all by the computer not only by windows 2000.

---

### Post by NonStop on 2008-12-16
> **BDNiner said:**
> You have a press a certain key to enter the bios before windows 2000 loads. It is different for each computer. Some use <del> others use <F10>. in the bios u will be able to set which device the computer tries to boot from first. It should be set to the DVD drive not the Hard disk. Then you will be able to boot using the live CD instead of booting into windows 2000. the Bios may also tell you if the DVD drive is not being detected at all by the computer not only by windows 2000.

Hmm, have tried repeatdely pressing both, but neither work, nothing brings up BIOS.

---

### Post by BDNiner on 2008-12-16
It is different for each computer. I would consult any documentation you have for the computer or search online. Some computers will display the key to enter the bios while it is booting. This is when you first turn on the computer and before the windows 2000 loading screen.

---

### Post by samden on 2008-12-16
> **NonStop said:**
> Also, I wouldn't be able to try out live CD as windows 2000 isn't recognising the DVD-ROM drive. Is your cd drive not working at all, or is it just that Windows won't recognise it? If its just a Windows problem that shouldn't affect Ubuntu, if you can run the alternate cd to install it you should be able to run a live cd to test it, your specs are high enough.

---

### Post by cardinals_fan on 2008-12-16
> **NonStop said:**
> 
If I was to do just a normal install, would it wipe out the data from both partitions, would it install onto one only, or what?
You'll have a number of choices, just like regular Ubuntu.  That drive is pretty small, but it can still be chopped into a couple partitions.
> **NonStop said:**
> 
What software can be installed onto it? Can openoffice be installed? What about some kind of chatting client which can handle msn chatting?
Xubuntu can use any software Ubuntu can; it accesses the same repositories.  You can install OpenOffice easily.  Pidgin is included and can handle MSN, and aMSN is another choice available in the repos.
> **NonStop said:**
> 
What are the chances of it working through wireless?
I don't know; what's your card?
> **NonStop said:**
> 
What are the chances of it working through Ethernet?
Same as above, but more likely.
> **NonStop said:**
> 
Finally, what are the chances of it working on this laptop?
Pretty good.  Xubuntu is not a very lightweight distro, but you can always lighten it up after installation if it's too heavy.  If it actually can't boot (unlikely; that should be enough RAM), you can try the command-line installer on the alternate CD.

---

### Post by nandemonai on 2008-12-17
As a side note, a buddy of mine has a Vaio. His BIOS key is F2.

Try that. He says you gotta mash it a few times as soon as you power up. ;)

---

### Post by NonStop on 2008-12-17
My bro got the DVD drive working through working in the registry (it was more of a windows problem, then), so the possibility of xubuntu is now realised! I don't think I have any questions left now, thanks to everyone that's answered!

---

