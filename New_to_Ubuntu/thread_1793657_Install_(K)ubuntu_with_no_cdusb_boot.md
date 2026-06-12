---
title: "Install (K)ubuntu with no cd/usb boot"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by Greydog on 2011-06-29
My searching for a solution has only confused the issue for me.
I have a Sony Vaio laptop with a borked dvd drive and there is no option in the BIOS to boot from USB.There is an option to boot from network.
I would like to do a fresh install but, I am not sure how to proceed.
Is there a way to do a fresh install over my LAN?
Thanks for any help.

---

### Post by Bachstelze on 2011-06-29
Yes though I'm not sure it will let you install Kubuntu directly, you might have to first install a command-line system, then install the Kubuntu packages manually.

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

Note that you will need another machine to act as a PXE server.

---

### Post by TerribleLIar on 2011-06-29
If you have the means available, you should also be able to install Kubuntu by taking the HDD out, put it in an external enclosure (or in another laptop), and install Kubuntu on that HDD through the other computer's optical drive or USB.

---

### Post by Greydog on 2011-06-29
Thanks for the ideas.
I saw the PXE server solution, Bachstelze and got scared.:)
I hadn't thought of the HDD removal idea,Terrible. I'll have look further into it.
Thanks again.

---

### Post by amjjawad on 2011-06-30
[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)

---

### Post by jtarin on 2011-06-30
Sometimes your bios will not show boot option USB flash specifically, some bios refer to it as a HDD.

---

### Post by Greydog on 2011-06-30
Thanks guys.
I'm not sure how the PloP thingie would work, as I'm not dual-booting is there a way?
Would the USB show up as a separate HDD in the BIOS? I haven't made a bootable USB as yet?
Thanks again

---

### Post by amjjawad on 2011-06-30
> **Greydog said:**
> Thanks guys.
I'm not sure how the PloP thingie would work, as I'm not dual-booting is there a way?
Would the USB show up as a separate HDD in the BIOS? I haven't made a bootable USB as yet?
Thanks again

I posted the link, read it.


Sometimes, this is how BIOS detect USB Drives: [http://ubuntuforums.org/album.php?albumid=2145&pictureid=7191](http://ubuntuforums.org/album.php?albumid=2145&pictureid=7191)

---

### Post by whatthefunk on 2011-06-30
Ive got a Sony Vaio laptop too..doesnt boot from USB.

What kind of ports does your laptop have?  Ive got a firewire (I.LINK, S400 or whateer you call it) port on mine.  I installed with an external CD drive that uses this firewire port.

---

### Post by SoFl W on 2011-06-30
Try booting with the USB stick inserted and then going into BIOS and see if it is now part of the menu selection of boot options.
If any USB option appears try it.  I can't remember the details but I had a machine at work that I think we had to select USB ZIP drive to get the machine to boot off from an external CD drive.

---

### Post by mastablasta on 2011-06-30
> **Greydog said:**
> Thanks guys.
I'm not sure how the PloP thingie would work, as I'm not dual-booting is there a way?
Would the USB show up as a separate HDD in the BIOS? I haven't made a bootable USB as yet?
Thanks again
 
 
plop works just fine. if oyu have a floppy drive and floppy it can act instead of boot sector of your USB key.

---

### Post by drs305 on 2011-06-30
In your current setup do you boot from the Grub2 menu? If so, there is a way to install from a K/U/buntu ISO stored on your hard drive.

If this is something you want to try, here is the guide I wrote about how to do it:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")
Look at the two "Install" sections.

---

### Post by drs305 on 2011-06-30
There is a way to install from a K/U/buntu ISO stored on your hard drive if you boot the ISO from the Grub2 menu.

Here is a link to the guide I wrote about it:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

The guide was for booting the LiveCD from the rescue prompt, but you can do it by building a custom entry and booting it, or using the procedures from the grub prompt, which you would access by pressing 'c' at the G2 menu.

---

