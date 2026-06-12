---
title: "Virtual box install and run problems"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by hdanap on 2011-05-15
Hi all,

Been trying to use virtualbox ose to create a virtual machine,

1.Ist of all when i try to add the ubuntu iso to the storage tree in the virtual machine settings, 
 keep getting this error 

"  p, li { white-space: pre-wrap; }  Failed to open the CD/DVD image /home/sara/Desktop/ubuntu-10.04.2-desktop-i386.iso.
 Could not get the storage format of the medium '/home/sara/Desktop/ubuntu-10.04.2-desktop-i386.iso' (VERR_NOT_SUPPORTED).
Details
  p, li { white-space: pre-wrap; }     Result Code: 
  VBOX_E_IPRT_ERROR (0x80BB0005)
   Component: 
  Medium
   Interface: 
  IMedium {9edda847-1279-4b0a-9af7-9d66251ccc18}
   Callee: 
  IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}

"




2. Also, even when i try to start the virtual machine like that, i get this error even though i was able to start it before but only had fatal error cos i guess there was nothing to boot as i couldnt add the ubuntu iso

"  p, li { white-space: pre-wrap; }  Failed to open a session for the virtual machine fghj.
 The virtual machine 'fghj' has terminated unexpectedly during startup with exit code 1.
Details
  p, li { white-space: pre-wrap; }     Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  Machine
   Interface: 
  IMachine {662c175e-a69d-40b8-a77a-1d719d0ab062}

"
 p, li { white-space: pre-wrap; }then below quote pops up infront saying

"  p, li { white-space: pre-wrap; }  RTR3Init failed with rc=-1912 (rc=-1912)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.


Abort

 "

Please any ideas, I can download team viewer if someone can help me, cos ive used google, youtube to no success.

Help, Thanks

p.s I have the virtualbox-ose-dkms package installed

---

### Post by tkelito on 2011-05-16
Can you run in Terminal:

```
sudo /etc/init.d/vboxdrv setup
```

That command seems to fix 99% of my issues with Virtualbox, and plan on running it every time update your kernel.  The command will take 2-3 minutes, be patient, it feels like it hangs but it doesn't.


Try to run your box after it re-registers the Virtualbox Kernel modules.


I also suggest using the PUEL version straight from Oracle due to the added features (like USB) as opposed to OSE from Synaptics.

---

### Post by wildmanne39 on 2011-05-16
> **hdanap said:**
> Hi all,

Been trying to use virtualbox ose to create a virtual machine,

1.Ist of all when i try to add the ubuntu iso to the storage tree in the virtual machine settings, 
 keep getting this error 

"  p, li { white-space: pre-wrap; }  Failed to open the CD/DVD image /home/sara/Desktop/ubuntu-10.04.2-desktop-i386.iso.
 Could not get the storage format of the medium '/home/sara/Desktop/ubuntu-10.04.2-desktop-i386.iso' (VERR_NOT_SUPPORTED).
Details
  p, li { white-space: pre-wrap; }     Result Code: 
  VBOX_E_IPRT_ERROR (0x80BB0005)
   Component: 
  Medium
   Interface: 
  IMedium {9edda847-1279-4b0a-9af7-9d66251ccc18}
   Callee: 
  IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}

"




2. Also, even when i try to start the virtual machine like that, i get this error even though i was able to start it before but only had fatal error cos i guess there was nothing to boot as i couldnt add the ubuntu iso

"  p, li { white-space: pre-wrap; }  Failed to open a session for the virtual machine fghj.
 The virtual machine 'fghj' has terminated unexpectedly during startup with exit code 1.
Details
  p, li { white-space: pre-wrap; }     Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  Machine
   Interface: 
  IMachine {662c175e-a69d-40b8-a77a-1d719d0ab062}

"
 p, li { white-space: pre-wrap; }then below quote pops up infront saying

"  p, li { white-space: pre-wrap; }  RTR3Init failed with rc=-1912 (rc=-1912)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.


Abort

 "

Please any ideas, I can download team viewer if someone can help me, cos ive used google, youtube to no success.

Help, Thanks

p.s I have the virtualbox-ose-dkms package installed

Hi, I agree with what the person said in post # 2 you should install the one from virtualbox.org and there you will find all the instructions and requirements that you need to have installed before you install a virtual machine.Also if you install all the required software you do not have to run this command sudo /etc/init.d/vboxdrv setup everytime there is an update to the kernel.:D

---

### Post by hdanap on 2011-05-16
> **tkelito said:**
> Can you run in Terminal:

```
sudo /etc/init.d/vboxdrv setup
```That command seems to fix 99% of my issues with Virtualbox, and plan on running it every time update your kernel.  The command will take 2-3 minutes, be patient, it feels like it hangs but it doesn't.


Try to run your box after it re-registers the Virtualbox Kernel modules.


I also suggest using the PUEL version straight from Oracle due to the added features (like USB) as opposed to OSE from Synaptics.

Thanks for the hint, i uninstalled ose and installed oracle vm and followed all the instruction on the page, now the virtual box actually boots but i just can add ubuntu-10.04.2-desktop-i386, should i be trying to add natty nartal instead,

Im really finding it next to impossible to add the iso file

I also did the sudo /etc/init.d/vboxdrv setup and still not adding the iso file,

Please advice

---

### Post by wildmanne39 on 2011-05-16
> **hdanap said:**
> Thanks for the hint, i uninstalled ose and installed oracle vm and followed all the instruction on the page, now the virtual box actually boots but i just can add ubuntu-10.04.2-desktop-i386, should i be trying to add natty nartal instead,

Im really finding it next to impossible to add the iso file

I also did the sudo /etc/init.d/vboxdrv setup and still not adding the iso file,

Please advice
Hi, did you read how to boot an iso image at virtualbox.org? click settings,storage,under storage tree, host drive or it might say something elese in your case,then on the right under attributes cd/dvd click the little cd icon and select choose virtual hard disk and it will open a file location that should be where your iso file is the click on it.Then on the system menu make sure you have cdrom as your first boot choice.:)

---

### Post by wildmanne39 on 2011-05-16
> **hdanap said:**
> Thanks for the hint, i uninstalled ose and installed oracle vm and followed all the instruction on the page, now the virtual box actually boots but i just can add ubuntu-10.04.2-desktop-i386, should i be trying to add natty nartal instead,

Im really finding it next to impossible to add the iso file

I also did the sudo /etc/init.d/vboxdrv setup and still not adding the iso file,

Please advice
Hi, one other thing you do have to download the ubuntu iso that you want to use before you can use the instructions that I gave you, it is equal to putting a disk in the cd drive and installing from it.

---

### Post by hdanap on 2011-05-16
> **wildmanne39 said:**
> Hi, one other thing you do have to download the ubuntu iso that you want to use before you can use the instructions that I gave you, it is equal to putting a disk in the cd drive and installing from it.

Bro,

Unbelievable, It all came down to the iso image i was trying to boot, the 10.4 desktop .iso was the problem as soon as i down loaded the natty and used that, i worked instantly

Amazing.

Thanks for help bro,

More beans to u man, SOLID

---

### Post by tkelito on 2011-05-16
Awesome glad you got it working.  You'll be much happier using the PUEL version over OSE.  It always happen you find out the downfall of OSE once you need one of the extra features.  

Cheers

---

### Post by wildmanne39 on 2011-05-16
> **hdanap said:**
> Bro,

Unbelievable, It all came down to the iso image i was trying to boot, the 10.4 desktop .iso was the problem as soon as i down loaded the natty and used that, i worked instantly

Amazing.

Thanks for help bro,

More beans to u man, SOLID

Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.):P

---

### Post by hdanap on 2011-05-16
> **tkelito said:**
> Awesome glad you got it working.  You'll be much happier using the PUEL version over OSE.  It always happen you find out the downfall of OSE once you need one of the extra features.  

Cheers

Thankx man for the assist, very helpful tips. Nice

---

### Post by hdanap on 2011-05-16
> **wildmanne39 said:**
> Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.):P

Kool will do that,
thanks again for the assist

---

### Post by sgriesel on 2012-10-24
yep had the same problem. busy installing 10.04 now. can't wait to start!! new to linux and looking forward learning new things, any tips you guys maybe want to share?

---

### Post by overdrank on 2012-10-24
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

