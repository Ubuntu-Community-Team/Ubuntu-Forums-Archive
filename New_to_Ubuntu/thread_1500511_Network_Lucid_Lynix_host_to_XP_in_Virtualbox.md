---
title: "Network Lucid Lynix host to XP in Virtualbox"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Old Newville on 2010-06-03
Hello,

I'm running Lucid Lynx with Windows XP in Virtualbox. My printer, a Dell (sorry to use a swear word so early in the morning), only works with Windows. There are no Linux drivers for it.

So, I'd like to figure out if I can network Ubuntu and Windows such that Ubuntu could use the printer. Is that possible? I could just buy a new printer, but I like the challenge of trying to figure this out. Plus, its cheaper that way.

Any tips, suggestions, links, would be appreciated!

Thanks.

---

### Post by Tryer(ForLife) on 2010-06-03
It'a not morning here where i am;)

Sure you can have your printer inside the VM, i have mine epson inside a VB machine...

I assume that the printer connects to PC via USB?

It probably does, so you need USB support for the VirtualBox, i don't know which version of Virtual Box you have, if you installed it from Ubuntu Software Center it's probably a version in which you don't have USB support, something was changed in Lucid so USB doesn't work in older version of VirtualBox.

I downloaded this beta version
virtualbox-3.2_3.2.0~beta1-60785~Ubuntu~lucid_i386
and USB works in it. 

Try to find it and install it, i can't help you out further since i'm in Windows right now, but as soon i boot up ubuntu i will post more on how you can get it to work.

---

### Post by Old Newville on 2010-06-03
Thanks for your reply. Yes, I too discovered the lack of USB support in the OSE version and replaced it with the latest from the Virtualbox webpage. So there is USB support. I installed guest additions for file sharing, but so far I can only see the Ubuntu folders in Windows. Not the other way around.

---

### Post by Tryer(ForLife) on 2010-06-07
hi, sorry for not replying, i had some stuff that i needed to do.

So you installed the latest version of the VirtualBox and you have USB support, i'm guessing that you enabled USB in the Setting for your Virtual Machine?

If not do it.

Next thing that you have to do is enable the printer while you are in your VM, go to Devices which is on the top of the screen and then under USB Devices mark your printer as active and it should pop up in the Virtual Machine, then you install drivers there.

As far as seeing folders from Virtual Machine in Ubuntu, i don't think that's possible, and you can just set up shared folders so that you can see Ubuntu folders inside your VM and transfer files like that. All that you will have to do it remove the Read Only atribute in Settings for Shared Folders in VirtualBox and you can save your work in them and then easilly access them from ubuntu...

i hope i made myself clear and that it works ok with you, if not do tell, and i'll try to explain better.

---

### Post by Old Newville on 2010-06-07
Thanks again for your time, Tryer(ForLife). After reading the Dell manual and anything else I can find on the subject, I think my options here are limited. I can use the Dell as a stand-alone fax machine and buy a standard printer for less than $50. I think that would solve my problem. There's also been suggestions in cases like mine that a wireless router would work. Again, gotta part with my greenbacks.

---

### Post by Tryer(ForLife) on 2010-06-08
if ubuntu isn't recognizing the Dell at all, then i don't know what to do, cause ubuntu needs to recognize the printer in order for it to become usable inside the VM....

Luckily my ubuntu is recognizing my epson, i see it on USB port so i can have it in VM....

---

### Post by Old Newville on 2010-06-08
Ubuntu recognizes the printer -- it shows up in all of my applications -- but when I hit print, nothing happens. I've tried many of the CUPS generic print drivers, but none of them gets any reaction from the Dell.

---

### Post by Tryer(ForLife) on 2010-06-09
are trying to print from Ubuntu or from the Virtual Machine?


Eanble  USB in the Virtual Machine Settings, then enable the printer in the Devices, you get that option when you run the Virtual Machine and it should work there....

[IMG]http://j.imagehost.org/0716/Screenshot_6.png[/IMG]

[IMG]http://j.imagehost.org/0305/Screenshot-1.png[/IMG]

Have you tried?

---

