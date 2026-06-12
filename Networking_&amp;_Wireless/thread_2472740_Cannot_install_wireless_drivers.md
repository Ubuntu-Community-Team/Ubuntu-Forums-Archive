---
title: "Cannot install wireless drivers"
date: 2022-03-11
forum: Networking &amp; Wireless
---

### Post by GeoffatMM on 2022-03-11
Hi all, first a bit of information.

I have created a live install on a usb drive and it works fine on my MacBook Air running Big Sur 11.6.2.  It also works on my iMac running High Sierra 10.13.  each time I use it I have to install the additional drivers for my wireless device but it works.

I used the live install to then create a full installation on a large (32 Gb) usb drive.  It loads on the MacBook Air but it does not get recognised by High Sierra on the iMac at all so I cannot load it through the boot loader.  **This is the first issue I would like to find a solution to if possible**.

Although the MacBook Air recognises and loads the full installation and allows me to access file etc. it also does not load the Broadcom drivers.  However, when I access "Additional Drivers" and try to install the drivers for the device it recognises, it tells me it cannot do it without an internet connection!  But I need the drivers installed to have an internet connection as the MacBook Air does not have an ethernet port and relies entirely on wireless for internet access.

I added (by ticking the box) the CD Rom with ubuntu 20.04 "Focal Fossa" (which I assume is the full installation files on the USB)as a source but it still gives an error.  I added the original live install usb to the machine's second USB port to see if it would recognise it as a software source but it did not and I cannot see how to make it do so.

I need to find a solution that allows me to install the drivers without accessing the internet but I do not know which files I will need or where to access them.  They must be on the live usb (and probably also on the full install usb even though it is not finding them)  but I do not know how to find or use them.  **This is the second and main issue I need a solution for.**

The device is recognised as a Broadcom and gives the following information in the additional drivers page:

Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)

The error message I get is:

pk-client-error-quark: Cannot download packages whilst offline (257)

Can anyone help me out of this loop please? 

Geoff

---

### Post by mIk3_08 on 2022-03-11
> **geoff-jankowski said:**
> 
Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)
 This hardware device usually and automatically be added under Additional driver in 20.04 and 18.04 and this works smoothly on both 20.04 and 18.04 I've tried it already.  Additional drive will be seen under the software & update tab. regards and cheers.

---

### Post by GeoffatMM on 2022-03-11
Thanks for the response but as I carefully explained in my post, when I try to do that I get the error shown.   It works on the live usb fine but not on the full install.  That is why I am posting this thread for help.  

G

---

### Post by GeoffatMM on 2022-03-12
Well I read up about trying to install it but most advice was based on internet access which was no good.  The only one I found that did not need the internet looked a bit complicated and I was worried I would cause more damage than good.

So I then looked to connect the machine over bluetooth to the internet via my iPhone and it proved surprisingly easily.  It was slow and took a few attempts and a reboot to get it to work but the driver has now installed and I have full internet connection.  This proved to be the easiest solution for me.

---

### Post by mIk3_08 on 2022-03-12
> **GeoffatMM said:**
> Well I read up about trying to install it but most advice was based on internet access which was no good.  The only one I found that did not need the internet looked a bit complicated and I was worried I would cause more damage than good.
So I then looked to connect the machine over bluetooth to the internet via my iPhone and it proved surprisingly easily.  It was slow and took a few attempts and a reboot to get it to work but the driver has now installed and I have full internet connection.  This proved to be the easiest solution for me.
Wow! cool. Good Luck and cheers. Welcome to Linux World.

---

