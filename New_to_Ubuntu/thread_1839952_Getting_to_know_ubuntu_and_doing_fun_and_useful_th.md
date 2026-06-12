---
title: "Getting to know ubuntu and doing fun and useful things with samba."
date: 2011-09-06
forum: New to Ubuntu
---

### Post by Kracer on 2011-09-06
I've only started experimenting with open source linux etc. And i can't wait to get home from vacation to get the hdd to make a proper installation of ubuntu rather than using wubi.
While i was looking round for a use for the old computer that I'm getting the hdd from i thought i could make my pendrive more useful by being able to use it to run a programm able to access a samba server that i could run on the old machine.
To make clear what im asking, can i use an exe on pendrive so that the "foreign" computer (be that school or at family) can access files on the samba server so that programms on the computer can use it. (be that java files at school, or docs open in word at family)
Sorry a lot for the essay
Thanks in advance.

---

### Post by snip3r8 on 2011-09-06
Windows computers can access samba shares the same way they access normal windows shares

---

### Post by Kracer on 2011-09-07
No but i want to do that over the internet without installing anything on the host machine.
You can access files via a web browser but not open them up in normal programms.
I want to do so so that i have a single folder alqays updated whereever i work.

---

### Post by nipunshakya on 2011-09-07
> **Kracer said:**
> No but i want to do that over the internet without installing anything on the host machine.
You can access files via a web browser but not open them up in normal programms.
I want to do so so that i have a single folder alqays updated whereever i work.

hmm....looks like you are trying to cook something new here...or maybe discovered already....but i found your thing interesting.....i shall wait like you to see if someone has some valuable suggestions stored for this thread.....goodluck...):P

Regards,WinuxUser

---

### Post by westie457 on 2011-09-07
Hello.

A LiveUSB stick with a persistence file (space for installed apps and downloaded files) should be able to access Samba shares without writing anything to the host computer's hard drive.

Or a slightly more technical solution is a full install to a USB stick (8GB minimum size) with its own Grub should be able to do the same thing.

Either is really an ultra-portable computer in a pocket.

---

### Post by Kracer on 2011-09-07
But i cant open files over the internet???
So i have no olld versions new versions
Just 1 file thats always updated from wherever i work or play.
ie:not download them
If it's not possible i might just as well write it into my list of ideas for programms when i get out of basic java and into more advanced stuff
Can u explain more what u said about grub etc. Pls??

---

### Post by westie457 on 2011-09-07
> **Kracer said:**
> But i cant open files over the internet???
So i have no olld versions new versions
Just 1 file thats always updated from wherever i work or play.
ie:not download them
If it's not possible i might just as well write it into my list of ideas for programms when i get out of basic java and into more advanced stuff
Can u explain more what u said about grub etc. Pls??

Are you suggesting something along the lines of a 'Remote Desktop' where you sign-in at home or school and work directly on a file that is on a computer somewhere completely different? I know that is possible between computers however I have not tried to work on a file while it is in 'the cloud'. All my cloud storage accounts only allow me to upload and download or share the files.

Now to the Grub question.

As you may be aware when you create a bootable USB or CD there is a small piece of code written to the first few sectors of the medium to make it bootable so the ISO file can start. With a full install of Ubuntu to an external USB drive or a Memory stick Grub has to be installed to the root/MBR of the device so the operating system will run. Settings in the BIOS have to be changed to tell the computer to look for the USB device before the internal hard drive is accessed. Nothing to it really. It is fun to borrow someones computer and see the look on their face when their pc starts using something other than Windows and you are surfing the 'net or playing music in less time than they ever could.

Hope this is explained clearly and is useful to you.

---

### Post by Kracer on 2011-09-08
Ohhhh so thats how booting from an external medium works.
Good to know thx.
Hmmm i wish i could code vry well so i can write this programm.
Thanks A LOTT
Wish me luck in the world of open source and linux

---

