---
title: "Access files on windows through linux"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by elmoslattery on 2011-06-27
I installed ubuntu yesterday and now have both windows and ubuntu installed on my machine.

there are a lot of files (music,video etc) which i downloaded on windows vista. how do I access these through ubuntu?

thanks!




P.S I am a complete n00b. sorry in advance if this is a stupid question

---

### Post by Paqman on 2011-06-27
Hover your mouse over the bar at the top of the screen, and from the "Places" menu, click on the volume that corresponds to your Windows partition (it'll be called something like "xxGB Volume" or possibly "host"). Then you can browse through the Windows folders to where your stuff is.

---

### Post by donny.davis on 2011-06-27
go to places(on the panel)
and there u will find ur windows partitions listed down
just click on the desired drive(to mount them)
n after use unmount them

there is nothing being stupid in the question
all newcomers have such doubts
but here is our forum to answer any questions

Good luck 
enjoy the new feel

---

### Post by elmoslattery on 2011-06-27
really sorry, but I am still confused...


when I click on places the options I get are

Home folder
computer
Templates trash
Network 
Search files

Documents
Pictures
Music
Videos Downloads

Add Bookmark
Edit Bookmark



I guessed (not sure) I am supposed to click Network > Windows Network > Workgroup 


When I do this I get the message "unable to mount Location"

Thanks for your help

---

### Post by halibaitor on 2011-06-27
Click on "computer" and you will see your drives.

---

### Post by Paqman on 2011-06-27
When you've got the file browser open, is it listed in the panel on the left?

---

### Post by owiknowi on 2011-06-27
you also need the correct user privileges / rights to be able to mount other partitions.
you can set them in system / administration / users and groups

---

### Post by elmoslattery on 2011-06-27
When I click on computer "120 GB Hard drive: OS tools" comes up. Now that I have clicked on it it does appear in the left panel but within that there is nothing I recognise, i have looked within that and found nothing.

I do not know how/where to navigate to system / administration / users and groups


Thanks

---

### Post by muteXe on 2011-06-27
Open up a terminal and type: sudo fdisk -l

that's a little L, not a one. 

Paste the results back in here.

---

### Post by owiknowi on 2011-06-27
it should be located as a menu in the bar at the top of your screen.
what version of ubuntu are you using? my knowledge stops at 10.10 (before unity).

---

### Post by Morbius1 on 2011-06-27
I've got a funny feeling you installed via Wubi. Open up Nautilus ( Home folder ) and go to "File System" > host. Do you see your files now?

---

### Post by computerandu on 2011-06-27
Can you provide a screen shot of the file browser? This could help us in helping you.

---

### Post by elmoslattery on 2011-06-27
> **Morbius1 said:**
> I've got a funny feeling you installed via Wubi. Open up Nautilus ( Home folder ) and go to "File System" > host. Do you see your files now?
 

Yes, they are there!

Does this mean I installed ubuntu the wrong way?

---

### Post by Morbius1 on 2011-06-27
> **elmoslattery said:**
> Yes, they are there!

Does this mean I installed ubuntu the wrong way?
No. It just means you installed it another way. 

Don't really know much about how Wubi actually works as I have never used it, but from the Windows perspective you installed Linux as an application within Windows instead of having a true dual boot. Someone more well versed in Wubi can probably detail the differences.

---

### Post by Paqman on 2011-06-27
> **Morbius1 said:**
> 
Don't really know much about how Wubi actually works as I have never used it, but from the Windows perspective you installed Linux as an application within Windows instead of having a true dual boot. Someone more well versed in Wubi can probably detail the differences.

The Wubi installer is a Windows application, but it doesn't install Ubuntu itself as a Windows app. What it does is create a nifty virtual partition inside the Windows filesystem (Windows just sees it as a file). Then after rebooting it installs into the virtual partition in the same way it would install into a normal partition. It then links up the Windows bootloader and Grub. End result is a dual-boot system without having to do any partitioning. It's clever, but a bit of a kludge.

The limitations are that you can't hibernate, maximum size is limited, and that any problems with the NTFS filesystem can prevent Ubuntu from booting.

---

