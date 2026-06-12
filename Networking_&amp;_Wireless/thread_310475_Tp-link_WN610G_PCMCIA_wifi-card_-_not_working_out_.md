---
title: "Tp-link WN610G PCMCIA wifi-card - not working out of the box with network-install"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by Striatum on 2006-12-01
Hi there,

I have an IBM Thinkpad without CD-ROM drive, so I install Ubuntu Edgy over a wired network via PCX, which works quite fine.
The main network connection for my laptop after the installation should be via wlan, specifically via a Tp-link WN610G PCMCIA-card. I read lots of reports that this card should work out-of-the-box, but not for me. I suppose this is because Ubuntu already thinks that the wired eth0 is sufficient, so how can I force the detection of my wlan-card?
Or doesn't my card work out-of-the-box?

Thank you very much!
Dominik

---

### Post by FrodoB on 2006-12-01
Did you install using the Alternate CD? If so then:

1) Have the install CD ready for use.

2) Open a terminal command prompt and type the following:

sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

If you did not install using the Alternate CD them provide the output of:

lspci -v

---

### Post by Striatum on 2006-12-01
Hi there,

as stated, my laptop doesn't have a CD-ROM drive, so this is not an option.
Why isn't my TP-Link running out-of-the-box?

---

### Post by FrodoB on 2006-12-01
Well, did you install from the alternate cd or the normal install disk that startup as live CD and then select the install icon from the desktop?

---

### Post by Striatum on 2006-12-02
I used the netboot files from ([http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/)) served by my tftp/dhcp server. This brings up the Ubuntu installer in text mode/framebuffer on my laptop.

---

### Post by siddharth_s on 2006-12-02
hi,
i understand ur problem. what uve gotta do is download the alternate install cd from one of the mirrors and mount it using the following terminal command.

sudo mount -t iso9660 -o loopsudo mount -t iso9660 -o loop /<address of the image> /media/cdrom/

that should mount the cd and run it.
then you can try the process mentioned by frodoB.
i hope it works.

siddharth

---

### Post by FrodoB on 2006-12-02
Can you get the restricted modules for your version of the kernel downloaded to this other machine and then bring them over to the Ubuntu machine by ftp and install them using:

dpkg --i linux-restricted-modules-?????

Use uname -a to find out which kernel you have.

---

### Post by Striatum on 2006-12-02
got it to work, thanks for your help!

I need to run

iwpriv ath0 mode 0
iwpriv ath0 turbo 1

to enable G-mode manually. Where to put these commands in Edgy Eft to do this automatically on startup?

---

### Post by FrodoB on 2006-12-02
Try putting this just after the beginning of your interfaces record something like:

iface wlan0 inet dhcp
pre-up iwpriv ath0 mode 0[FONT=monospace]
[/FONT]pre-up iwpriv ath0 turbo 1
etc.

Just a guess. Test with ifdown and ifup and see it that does it for you.


> **Striatum said:**
> got it to work, thanks for your help!

I need to run

iwpriv ath0 mode 0
iwpriv ath0 turbo 1

to enable G-mode manually. Where to put these commands in Edgy Eft to do this automatically on startup?

---

