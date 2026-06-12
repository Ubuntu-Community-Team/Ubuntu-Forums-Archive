---
title: "Install Problem"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by mattxhand on 2011-04-24
I'm currently installing Ubuntu 10.04 on my machine as a dualboot with Vista from a USB. As soon as it opened, it automatically started (from what I assume) loading from USB with no command. It started running script on the screen and I remember it saying something about selecting choice #1 from option one. Now it erased the script and is a blank, black screen and has been for almost 30 minutes. So wtf is going on? How do I fix it?

---

### Post by candtalan on 2011-04-24
Which Ubuntu 10.04 image file did you use in the USB? 
If it was the usual Desktop version (and not the 'Alternate') then what is probably happening is simply that it is trying to start a 'Live' session. This is the default for the Desktop Version (option #1 maybe?).

Depending on the machine you are using, particularly the amount of RAM memory, then starting a live session can take some time. In very slow, old machines I may get, with 256MB ram, 15 minutes is typical.
However if you have a younger PC and have say 1GB ram, it should be up and running in less than 5 minutes.

If you are being unlucky with your type of machine, then some edit of the initial boot script may be useful, or other things, to accommodate the graphics chips maybe.

Oh, an dnot least, at this stage consier using the initial live CD boot menu to run 'Check this CD for errors' in case your drive s sticking occasionally etc.

With a Desktop Live CD you get the initial boot menu by hitting a key immediately you see some crypic symbols at the bottom of the screen early in CD boot.

---

### Post by mattxhand on 2011-04-24
The one I am on right now is the one directly from the website when you click the orange butt after selecting the 10.04 LTS. I want to say its the x.2 version, but I could be mistaken.  This is the exact script:
[241.810911] usb 2-9: usb disconnect, address 6
[241.xxxxxx] new low speed usb device usiinng ohci_hcd and adress 6
[241.xxxxxx] Configuration #1 chosen from option 1

Then it started going on some rampage that couldn't read.

CPU specs are 3GB DDR2 dual-channel, 1TB hard drive, AMD Athlon 64 x2 6000+

---

### Post by Old_Grey_Wolf on 2011-04-24
How did you make the USB? Did you use UNetbootin?

---

### Post by mattxhand on 2011-04-24
I used the one that they reccomended on the site. I forgot the name of it.

---

### Post by candtalan on 2011-04-24
> **mattxhand said:**
> The one I am on right now is the one directly from the website when you click the orange butt after selecting the 10.04 LTS. I want to say its the x.2 version, but I could be mistaken. 

That sounds like the Desktop version 10.04.2  (second image including updates, of 10.04) which should be no worry.
I will try to burn a 10.04.2  from the image I have and see if I can compare the text lists  you see...

---

### Post by Old_Grey_Wolf on 2011-04-24
> **mattxhand said:**
> I used the one that they reccomended on the site. I forgot the name of it.

That would be the "Universal USB Installer". Some people have problems with that one. If candtalan isn't able to help you, you could try making the USB with UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/). 

Also check the MD5 of the iso image you downloaded.

Edit: Sometimes the iso download from the main server can be corrupted during the transfer. That is why I use the alternate download option on the Ubuntu page and select a torrent ([http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)) to download from. You would want to select this torrent ubuntu-10.04.2-desktop-i386.iso.torrent. It is also faster to download that way.

---

### Post by candtalan on 2011-04-24
> **Old_Gray_Wolf said:**
> That would be the "Universal USB Installer". Some people have problems with that one.

Ah that makes sense, I have sometimes had that not work for me too. I did not know what the solution was, I simply went and used unetbootin instead.

I have burned a CD just now but have not proceeded further because I think it will be more useful to follow the other suggestions. 

Maybe check the downloaded image file first?
This site seems useful but I have never used it:
[http://www.md5summer.org/](http://www.md5summer.org/)

Then maybe use netbootin. First download it, install it in windows and use it to re create the usb stick?
I have always found unetbootin to make good bootable drives.

---

### Post by Old_Grey_Wolf on 2011-04-24
> **candtalan said:**
> 
Maybe check the downloaded image file first?
This site seems useful but I have never used it:
[http://www.md5summer.org/](http://www.md5summer.org/)


I was hoping someone would post a link for checking MD5sum on Microsoft Windows. I have never had to do that since I use torrents for iso downloads. I would have thought that an MD5 checking application would come with the default Windows installation; however, I don't use Windows very often anymore. :)

---

### Post by mattxhand on 2011-04-24
Well I just attempted UBootin and I started from scratch. Used it to download 10.04.2, formatted a new removable drive, and ran through the program. I rebooted when it said to do so, and I booted from the drive. The black and blue screen popped up and said "Default download in 10...9...8..." so I let it do its thing. It froze after about 30 seconds of loading. I went back and chose to check the disk for errors and it found two. I don't really know what else to do.:confused:

---

### Post by Old_Grey_Wolf on 2011-04-24
> **mattxhand said:**
> Well I just attempted UBootin and I started from scratch. Used it to download 10.04.2, formatted a new removable drive, and ran through the program. I rebooted when it said to do so, and I booted from the drive. The black and blue screen popped up and said "Default download in 10...9...8..." so I let it do its thing. It froze after about 30 seconds of loading. I went back and chose to check the disk for errors and it found two. I don't really know what else to do.:confused:

Did you download the file using the torrent I provided a link to and use UNetbootin to install the downloaded iso to the USB or did you let UNetbootin download from the main server. From your post, it appears you let UNetbootin download from the main server. A torrent checks the quality of the download while it is downloading and retries when errors or detected. Downloading from the main server does not provide error checking as the download takes place; therefore, any error induced by your network, the ISP you use, or other network issues beyond your control can corrupt the download.

It could be a bad USB; however, I think that is very very unlikely.

---

### Post by mattxhand on 2011-04-24
> **Old_Gray_Wolf said:**
> Did you download the file using the torrent I provided a link to and use UNetbottin to install the downloaded iso to the USB or did you let UNetbootin download from the main server. A torrent checks the quality of the download while it is downloading and retries when errors or detected. Downloading from the main server does not provide error checking as the download takes place; therefore, any error induced by your network, the ISP you use, or other network issues beyond your control can corrupt the download.


I did download it, however I don't really know what to do after the initial download. Care to explain?

---

### Post by Old_Grey_Wolf on 2011-04-24
> **mattxhand said:**
> I did download it, however I don't really know what to do after the initial download. Care to explain?

Try this page [http://unetbootin.sourceforge.net/#other](http://unetbootin.sourceforge.net/#other). They explain installing from a downloaded iso better than I could. Basically you select the disk image by selecting where you downloaded the iso file.

If you didn't download it using the torrent, you may still have problems with corruption during the transfer over the Internet.

I wish things were going better for you. I know it can be very frustrating.

---

### Post by mattxhand on 2011-04-24
I appreciate it. I've never had this many problems with something like this. I have Ubuntu loaded on a laptop, but I'd just really like to have in on my desktop. I guess I'll just keep plugging away at it.

---

### Post by K_45 on 2011-04-24
I'd download the standard live CD and burn it with Imgburn in WIndows. Set the burn speed to 24x, check verify and wait for a few minutes. Don't do anything with the system until the burn is finished. Then reboot and see what happens.

---

### Post by candtalan on 2011-04-25
> **mattxhand said:**
> I appreciate it. I've never had this many problems with something like this. I have Ubuntu loaded on a laptop, but I'd just really like to have in on my desktop. I guess I'll just keep plugging away at it.

I usually use the iso download method, however I always check the downloaded image md5sum after download and also after burning to cd. If you are seeing problems it is worth doing checks to find out what is going wrong.

Torrent is also good and I use it also a lot, mostly for seeding though, but before I knew what to do it seemed a bit complicated.

I mostly use Unetbootin for live usbsticks. When I use Unetbootin I also always make use of an iso image file I have previously downloaded for myself, I do not use the semi automatic unetbootin offer. It is nice of them to offer a list, but I prefer to be sure I have exactly what I want.

---

