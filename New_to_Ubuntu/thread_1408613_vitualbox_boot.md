---
title: "vitualbox boot?"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by muddpup64 on 2010-02-16
I have just installed vitualbox and set up a sesion for microsoft XP. But when I try to start it, it tells me [FONT=Times New Roman](No bootable[/FONT] [FONT=Times New Roman]medium found[/FONT]![FONT=Times New Roman] System halted.)[FONT=Verdana] What's wrong?
[/FONT][/FONT]

---

### Post by HarrisonNapper on 2010-02-16
VirtualBox emulates a computer on which you can install an operating system or do other things that you might do with other computers. So the virtual hard-drive is blank by default. In other words, no operating system is on it. You will have to boot up VirtualBox with an installation medium (LiveCD) and install an operating system on to the virtual hard drive.

---

### Post by bpalone on 2010-02-16
You need your XP Installation CD or an ISO of it.  You then need to mount the CD or ISO in VirtualBox.  When you load VirtualBox you will see in the right hand pane, General, Hard Disks and then CD/DVD-ROM.  Click on the CD/DVD-ROM and it will come up with a menu where you can select which CD/DVD drive to use or you can mount an ISO.  Do that and then start it up and it should start into a normal Windows install.

Hope that helps you out.

---

### Post by muddpup64 on 2010-02-16
What do you mean by mounting it to vitualbox?

---

### Post by HarrisonNapper on 2010-02-16
It's in the settings dialogue for the VM. There are step-by-step instructions including a video of how to do it at [www.virtualbox.org](www.virtualbox.org)

Cheers.

---

### Post by bpalone on 2010-02-16
> **muddpup64 said:**
> What do you mean by mounting it to vitualbox?

When you load the application VirtualBox you will see in the right hand pane, **General**,** Hard Disks** and then **CD/DVD-ROM**. Click on the CD/DVD-ROM and it will come up with a menu where you can select which CD/DVD drive to use or you can mount an ISO.

Mount is term used that basically means to make available to the OS.  In this case you would be making your Cd drive available to VirtualBox so it can read it to do the install.  The options are fairly clear in the menu I directed you to.  It isn't to hard, I even figured it out.

---

### Post by muddpup64 on 2010-02-16
I can't find my option (under detail) to change settings for CD/DVD-ROM.
Even for floppy and hard disks.

---

### Post by muddpup64 on 2010-02-16
Sorry,(:D) I found my CD/DVD-ROM settings but I can't find my mount option.

---

### Post by bowbalitic on 2010-02-16
Is your windos iso on a cd/dvd or on your harddrive??

If its on cd/dvd put in the cd/dvd, select your virtual machine from the list, then click settings, select the cd/dvd settings. Under settings make sure VB has your cd/dvd drive mounted and selected. 

If its on you hard drive, select your virtual machine from the list, click settings, select the cd/dvd settings. Make sure Mount CD/DVD Drive is selected, and make sure ISO Image File is selected. Then add your iso to the list by clicking the folder next to the selected iso, then clicking the add button on the window that comes up.

---

### Post by muddpup64 on 2010-02-16
[Screenshot-2.png]("http://ubuntuforums.org/attachment.php?attachmentid=147314&stc=1&d=1266362532") What?

---

### Post by bpalone on 2010-02-16
You must be using a newer version of VirtualBox, as the screen there is new to me.  You will have to excuse me, as I am firm believer in "If it ain't broke, don't fix it."  So, I am using an older version of VirtualBox.

From your screen shot, it appears that you need to select the CD/DVD device by clicking on the little icon to the right of where it says host.  That will or should bring up a directory tree to allow you to select which CD/DVD drive to use or to mount an ISO image on your hard drive.

I am guessing, from seeing your screen shot.  I just love it when developers decide that you need an entirely new interface.  

Hope I have been some help.

---

### Post by mlentink on 2010-02-16
Were you expecting to find a full blown Windows XP environment to be created by VirtualBox? 
V'Box creates virtual machines that allow you to run a large number of operating systems. But you still need the original installation media for those OS's. VirtualBox cannot create one for you. 
So if you want to install XP on a virtual machine created by VirtualBox, you need a XP cd.
Such a cd should be mounted as per the above instructions

---

### Post by bowbalitic on 2010-02-16
Please say whether your booting from cd/dvd or iso file so I can be specific (and type less :P)

---

### Post by muddpup64 on 2010-02-16
I am booting for a CD but iso file if I have to.

---

### Post by bowbalitic on 2010-02-16
Ok, like nearly every one else stated... I have never seen that setup for vbox. I don't know if its new or old. So I'm kinda guessing here. So be patient with me. 

It looks like at the bottom of your screen you have your virtual machine open. You cant make any real changes with the virtual machine open so make sure its closed. 

In the Host drop down arrow what does it show?? It looks like it picks up your drive (the storage tree shows the name of your drive) so is that under the drop down arrow? How many drives do you have? Is it selecting the wrong one as default?

If that doesn't work, try adding the iso as bootable in the list. 

First, before you rip a copy of your disk, try clicking that folder with the green arrow on it (the add icon) If you see an option to add, click it. If it automatically takes you to a navigation window, go to filesystem/media/cdrom (or dvd) double click, if it opens another folder, try finding a .iso file and double clicking on that. 

Post back what you find, take pics if you have to, I cant see whats going on and so you have to be specific so I can help you. Hope one of these things works though.

---

### Post by muddpup64 on 2010-02-16
Hey, thanks everybody for their help I'll try some of your tips and if they don't work I've got a buddy who is a computer genius. He works on huge company web servers and the one who started me on Ubuntu. Well anyway thanks everybody.:D

---

### Post by mlentink on 2010-02-16
> **muddpup64 said:**
> I am booting for a CD but iso file if I have to.


So, where do you have your Windows XP Installation disk? Have you already made an .iso out of it? Or do you have the CD proper?

---

### Post by bowbalitic on 2010-02-16
Well good luck, sorry we couldn't help. Backup and experiment :P, another really helpful tool would be the manual for your version of vbox. Garanteed they will tell you whats up (since booting from iso or cd is a requirement for "every" vbox virtual machine)

---

### Post by Merk42 on 2010-02-16
I dunno if you're still checking this thread, but I have the same Virtualbox you do.

At that window you showed it's current set to Host Drive, meaning if you put in the Windows XP disc in the actual drive of your computer, then it'll be read by the virtual machine.

If you have the disc, put that in the drive, then start the VM, the VM should detect the CD and you'll be good to go.

---

### Post by muddpup64 on 2010-02-16
Really? Huh, because I tried it with Windows 95, just to try it out since my XP CD is with a buddy at the moment.

---

### Post by spillin_dylan on 2010-02-16
Did your Windows 95 CD come with a bootable floppy disk, though?  Because if I remember right, mine did, and thus wouldn't boot off of the CD solely, it required a 3.5" floppy to load the CD-ROM drivers and such before it could install.

---

### Post by muddpup64 on 2010-02-16
Either it didn't come with one or it got lost sometime.

---

### Post by Merk42 on 2010-02-16
> **spillin_dylan said:**
> Did your Windows 95 CD come with a bootable floppy disk, though?  Because if I remember right, mine did, and thus wouldn't boot off of the CD solely, it required a 3.5" floppy to load the CD-ROM drivers and such before it could install.

This.

I'm pretty sure XP was the first Windows OS that could boot from CD, it MIGHT have been 2000.

---

### Post by muddpup64 on 2010-02-16
Thanks, I think that helped to figure some stuff out.

---

### Post by bpalone on 2010-02-17
Windows 95 requires a boot disk.  You can download one from [http://www.bootdisk.com/]("http://www.bootdisk.com/")

If I remember correctly, they have images and they can be mounted to the floppy without actually making a floppy.  Just like mounting a CD ISO.

VirtualBox doesn't do real well with 9x versions of Windows.  It has to do with 9x itself more than it does with VirtualBox.  People have done it and done some tweaking to make it work better.  Without the tweaking, you end with high CPU usage with 9x versions.  NT, 2000, XP etc work very well in VirtualBox.

Glad you got it figured out.  I have set up a 95 VM, but only to just say I did it.  I prefer 2K.

---

