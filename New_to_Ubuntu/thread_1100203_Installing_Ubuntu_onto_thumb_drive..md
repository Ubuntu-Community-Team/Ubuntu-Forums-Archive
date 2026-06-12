---
title: "Installing Ubuntu onto thumb drive."
date: 2009-03-19
forum: New to Ubuntu
---

### Post by davidstri on 2009-03-19
I wanted to have a portable ubuntu so I used this tutorial, [http://ubuntuforums.org/showthread.php?t=464113]("http://ubuntuforums.org/showthread.php?t=464113"), but I get stumped at "change grub address to *sdd*. After booting from the live CD, I tried looking for the grub folder in /boot/ but I did not find it. I just find a few text files, but no grub folder. Where is it?

---

### Post by jordanae on 2009-03-19
Actually, you can do this easily through the GUI. Since you're using a Live CD you won't need to download the ISO. Just go to System> Make Bootable Thumb Drive... or something like it.
I'm using Xubuntu (which doesn't let you do it this way) so I might be off on the location, but you should get it.

---

### Post by Paqman on 2009-03-19
And if that doesn't work, try installing unetbootin and using that.

---

### Post by sleepyjon on 2009-03-19
The way I usually do it is through an already installed system. I download the iso I want, install the usb creator in synaptic, and in xubuntu it's applications>system>create usb

---

### Post by davidstri on 2009-03-19
Oh, cool, thanks. It (system > administration > Create USB Startup Disc) worked.

---

### Post by davidstri on 2009-06-01
Hey, turns out the "USB Startup Disk Creator" app for Jaunty 9.04 doesn't make persistent installations of Ubuntu 9.04 on a USB thumbdrive. 
But, I found this website ([http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)) that makes persistent Ubuntu 9.04 Jaunty Jackalope installations to a USB thumbdrive for you. You may not like it but it helped me a lot. All you need it a windows computer, hehe.
I tried it out, and the Ubuntu 9.04 Jaunty Jackalope USB thumbdrive works perfectly, completely persistent and saves all the changes that I make, including any apps that I download.
I know that there is an ubuntu way to do it, but I just got tired of trying to do it, but I'm pretty sure I came very close.
I think, all that you need is a fat32 formatted thumbdrive, and then you have to make a partition (not sure what type) after you install ubuntu onto the USB, and name it casper-rw. That's as far as I got, and I don't know if it will even work, sorry.

---

### Post by thongkh on 2009-06-04
i guys, i have problem when trying to make a usb linux with pendrivelinux instruction, after i run the u904p.bat, when it prompt me for the drive name and i enter it, it said my drive is not reconized. tried to format and reformat the usb, still cant. i tried to create using usb startup creator disk via live cd, but not presistant.
please advice on pendrivelinux usb presistant ubuntu 9.04 creation.
thankz

---

### Post by davidstri on 2009-06-06
Hi thongkh,
I'm sorry but I'm no computer expert. I can just tell you what I did.
When I clicked u904p.bat and it asked me for my drive letter, I just put h as my drive letter, because that is what the computer called it. If you want to see what yours is called just click into "Computer"(or if you have an older version of windows, "My Computer") from your windows desktop and it should show you. Just try to match the drive letter with the size of the thumbdrive in gigabytes.
If you don't see your thumbdrive in Computer, try plugging it into a different computer to see if the problem is with the thumbdrive or the computer.

---

### Post by thongkh on 2009-06-08
> **davidstri said:**
> Hi thongkh,
I'm sorry but I'm no computer expert. I can just tell you what I did.
When I clicked u904p.bat and it asked me for my drive letter, I just put h as my drive letter, because that is what the computer called it. If you want to see what yours is called just click into "Computer"(or if you have an older version of windows, "My Computer") from your windows desktop and it should show you. Just try to match the drive letter with the size of the thumbdrive in gigabytes.
If you don't see your thumbdrive in Computer, try plugging it into a different computer to see if the problem is with the thumbdrive or the computer.

hi david, thankz for the reply, but i cant really understand what u mean by match the drive letter with size of the thumbdrive. do you mean if i have 8 gb thumbdrive in N drive, when it prompt me the drive letter i should type "**N 8**" or "**N8**"?
please advice.

---

### Post by wpshooter on 2009-06-08
1) make CD drive first boot device
2) Unplug all internal & external hard drives on your computer
3) Plug you USB key into a slot
4) Boot the computer to an ALTERNATE (not live) CD version of Ubuntu.
5) Install the ALTERNATE version to your USB key.
6) When done with the installation, change first boot device to USB key and you have a USB version of Ubuntu.

P.S. - Make sure your USB key is 8gb or larger.

---

### Post by dileepm on 2009-06-08
[http://www.scribd.com/doc/4090276/Installing-Ubuntu-In-Pen-Drive](http://www.scribd.com/doc/4090276/Installing-Ubuntu-In-Pen-Drive)

---

### Post by davidstri on 2009-06-08
Oh, sorry, I meant, if you know that you have an 8 gig thumbdrive and you see drive h has 8 gigs of space then you should type h.

---

### Post by Johan-Steyn on 2009-06-08
Hi,

Please do yourself a favor and check out the Portable Linux option from rudd-o.com.

No CLI required, as it it's a deb install.

Here's the site: [http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

Hope it helps.

Regards,

JS

---

### Post by davidstri on 2009-06-09
Cool, I will do myself a favor and check it out.
Can you say for sure that this works as well as pendrivelinux.com?
Have you tried it?
Unlike the bootable and persistent pendrivelinux, ubuntu usb, can I make it boot into my account instead of booting into a live account?
Thanks.

---

