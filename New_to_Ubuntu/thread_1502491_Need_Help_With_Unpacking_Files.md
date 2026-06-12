---
title: "Need Help With Unpacking Files"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by earthlychaos on 2010-06-05
I'm really new to Linux and I don't quite understand the unpacking process. I'm pretty sure that I managed to get it to unpack, but it doesn't look like it did anything. If it helps at all, I'm trying to install ndiswrapper in the hopes that it will let me install my wireless usb adapter.

---

### Post by dv3500ea on 2010-06-05
what were you trying to unpack:
an archive?
a .deb package?

You can [install a gui for ndiswrapper]("apt:ndisgtk")
by going to System -> Administration -> Synaptic Package Manager
typing 'ndistk' without the quotes
marking the package for installation by clicking on the tick box next to it
and finally pressing the Apply button.

---

### Post by earthlychaos on 2010-06-05
It's actually a gz file? The file name is ndiswrapper-1.56.tar.gz. I'm also trying to install a kernel file that's packed as file name linux-2.6.45.tar.bz2. I thought I managed to unpack both of them, but it doesn't look like it did anything.

I also tried what you said and it didn't come up with any results.

---

### Post by saakeman on 2010-06-05
> **earthlychaos said:**
> It's actually a gz file? The file name is ndiswrapper-1.56.tar.gz. I'm also trying to install a kernel file that's packed as file name linux-2.6.45.tar.bz2. I thought I managed to unpack both of them, but it doesn't look like it did anything.

I also tried what you said and it didn't come up with any results.

Is it like a program ?? 

maybe we have an alternative for you 

--------------------**
join facebook's dusitbin of history
**
dustbin of history

---

### Post by earthlychaos on 2010-06-05
It lets me extract it like it is a rar file. I don't know if that helps you out at all.

---

### Post by saakeman on 2010-06-05
> **earthlychaos said:**
> It lets me extract it like it is a rar file. I don't know if that helps you out at all.

some times it helps

---

### Post by earthlychaos on 2010-06-05
I have a question on a whole different topic. I used Wubi to Ubuntu and now I can't get my computer to boot from a disc. Is there anything that I can use to erase my hard drive and start from scratch?

The cd drive that was originally on my computer doesn't work anymore, and the computer won't boot from the second cd/dvd drive that I had installed at Best Buy. I also borrowed an external cd drive and it won't launch from that, either. I need to find a way to boot from a certain cd to erase my hard drive so that I can get everything working again. What can I do?

---

### Post by saakeman on 2010-06-05
> **earthlychaos said:**
> I have a question on a whole different topic. I used Wubi to Ubuntu and now I can't get my computer to boot from a disc. Is there anything that I can use to erase my hard drive and start from scratch?

The cd drive that was originally on my computer doesn't work anymore, and the computer won't boot from the second cd/dvd drive that I had installed at Best Buy. I also borrowed an external cd drive and it won't launch from that, either. I need to find a way to boot from a certain cd to erase my hard drive so that I can get everything working again. What can I do?

Leave the cd , try the live usb 
google live linux usb installer 

you will need another pc for this

---

### Post by earthlychaos on 2010-06-05
How do I burn an iso file onto a usb drive so that it will launch from there?

---

### Post by Penguin Guy on 2010-06-05
In Linux you do not use GZip archives - instead you use the software manager: [click here]("apt:ndisgtk").

---

### Post by acrazyplayer on 2010-06-05
You use "unetbootin" for "burning" a cd to usb.

On ubuntu simply type "sudo apt-get install unetbootin" into a terminal and if you already have the .iso then choose that option and locate it, otherwise you can download a whole new one. Also make sure your usb is plugged in before hand and has been formatted to FAT32 to avoid any problems

---

