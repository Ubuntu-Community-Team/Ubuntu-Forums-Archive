---
title: "Live USB persistent settings problem"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by ayushkumar on 2011-03-05
Hi
I am new to ubuntu 10.10. Actually to linux too. I used universal usb installer to use my 4GB FAT32 usb as a boot device instead of the Livecd. I dont exactly remember how much persistent space I allotted to the usb. I think it was around 2GB. Upon booting into Ubuntu I ran the synaptic package manager , marked all updates and applied it. It required around 328 MB for update. After everything was downloaded it started applying the updates. But halfway through it gave an error -"**No space left on device**". So I want to know how much persistent space to use on the USB. I basically want to know what the persistent settings mean. The updates were downloaded where ? To the OS or the USB..? I don't want to store any documents or media to my usb. I just want ubuntu to remember my settings and to have applications with which I can play media (from my OS). What happens to the left over space which I have not converted into persistent storage..?

Will using an 8GB usb solve this problem. How much persistent settings should I create on it so that it satisfies the above mentioned requirements. I want to dedicate this usb _solely_ to ubuntu. 

Also, I wanted to know whether it is possible to install ubuntu on an external hard disk (Seagate freeagent) like it can be installed on usb.,?
Thank you in advance..

---

### Post by maqtanim on 2011-03-05
Once the installation is complete there is no need of a USB anymore. It is installed into your hard drive. So you can eject the USB drive after installation and can boot/use Ubuntu without that USB drive. 

I am not sure whether you installed Ubuntu or you are running the live version? Ubuntu can be used from directly the USB drive without any kind of installation. This process is known as "live boot" or "live CD". When you boot the USB/CD, there should be a option like "Try Ubuntu". This option is for Live CD purpose. If you are in the live CD mode no change will be permanent.

So my question is *Did you install ubuntu or are you trying it from a live cd?* If you install it then *how much space did you allocate for root (/)?* You are running short in root partition.

---

### Post by Ben Page on 2011-03-05
You have to know what OS are you currently using, I don't understand your post. You are mentioning "the OS" and USB stick with live OS. You can check how much space you have left by going to places > computer. in there, find a "drive" labeled "filesystem" - thats your OS partition, you can check the free space you have left there. If you have another OS installed on your hard drive, boot to it and check how much space is there on the USB stick, this may give you an idea of how much persistence have you used. Live USB OS needs 1 gig for the OS and the rest can be allocated for persistence, so if you have 4 gig USB drive, there is space for 3 gigs of persistence file.

Please clarify your issue if I'm not helpful.

---

### Post by ayushkumar on 2011-03-05
i am really sorry if i was unclear in the first post..
I am on a liveusb.
I have not installed ubuntu.
And ubuntu refers to my hard disk as OS.
That is on my windows, it is my C: drive..
I am running live ubuntu from my usb, basically so that it remembers my settings when i use it the next time , which is not possible in livecd..

I also want to clarify that i dont want to install ubuntu...either on my hard disk,to my usb or to my external hard disk..
I just want to run it in live mode but with persistence...so that my settings are saved..
So is it possible to run the live version of ubuntu from my external hard disk..?

---

### Post by Ben Page on 2011-03-05
You have not allocated enough space to your USB persistence. I recommend you make another USB live OS again, from scratch. This time use LILI [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
Make sure you allocate 2 or 3 gigs for persistence.
You should have the "filesystem" drive/partition in the live OS (when you boot to it), this is your system drive, where Ubuntu lives (the "root" - "/" directory), this is where updates and other packages download, install and where your Documents, Pictures and Downloads will be (The Home directory). You'll have to mount (will happen automatically after you click them) windows filesystems to have access to them. Windows drives will appear as drives in the places  > computer window.

---

