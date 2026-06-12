---
title: "Virtual box and Puppy"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Koobelakahn on 2009-09-03
I have downloaded Puppy linux. I want to boot puppy linux in a Virtual Box.
How do i go about doing that?
I used Add/Remove programs to install Virtualbox. I dont have an icon. Any help with that too? or was that intended in its design?

If im being unclear, im sorry, i have been up for around 30 hours straight. Just ask me, and ill clarify any of my questions, and answer any questions you all have

I have never started Virtual box

 I am running Ubuntu 9.04 


Any help is appreciated
Thank you

---

### Post by brian3 on 2009-09-03
download from the virtual site it installs everthing for you

---

### Post by louieb on 2009-09-03
Look under Applications>System Tools. Just started using VB myself.
Pretty easy 
Build your Virtual Machine
Put the Puppy CD in the tray
Start the VM
Play Away.

---

### Post by jimingkui on 2009-09-03
Click this link download virtualbox[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by MrWES on 2009-09-03
> **louieb said:**
> Look under Applications>System Tools. Just started using VB myself.
Pretty easy 
Build your Virtual Machine
Put the Puppy CD in the tray
Start the VM
Play Away.


VB can actually boot from the iso, no need to burn the CD.

Bill

---

### Post by Ichtyandr on 2009-09-03
also "sudo apt-get install virtualbox-ose" is a simple installation procedure

---

### Post by A_M_S on 2009-09-03
Try this
[http://ubuntuforums.org/showthread.php?t=1212893](http://ubuntuforums.org/showthread.php?t=1212893)

---

### Post by MrWES on 2009-09-03
> **Ichtyandr said:**
> also "sudo apt-get install virtualbox-ose" is a simple installation procedure


I believe the version in the repositories does not have USB support.

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Grab the .deb from that link if you wish to have USB support,otherwise the version in the repositories will suffice. 

~Bill

---

### Post by Koobelakahn on 2009-09-03
I downloaded the ISO version of puppy, it asked what mouse i used. i answered. it asked what keyboard. i answered. It then asked which Video Type i wanted (Xorg or something else) I chose Xorg, because when i had the puppy cd, xorg worked. I got an entirely black screen, so i shut down the virtualbox. I decided to restart it.

Now it just says
FATAL: No bootable medium found! System halted.


How do i fix this?

---

### Post by earthpigg on 2009-09-03
something went wrong with the puppy install.

have vbox boot from the .iso again and start the install over.

puppy's installer is *not* the most intuitive, in my opinion.

---

### Post by Koobelakahn on 2009-09-03
Never mind, i got puppy running.
Its a funny thing when you set up to boot from a device you dont have lol

---

