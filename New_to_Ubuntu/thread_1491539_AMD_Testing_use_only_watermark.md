---
title: "AMD Testing use only watermark?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Chaotic Caveman on 2010-05-23
I've just installed the proprietary ATI driver for my Sapphire HD5830.  All seems good except the fact that I'm seeing a "Watermark" on the bottom right of my screen. It has an AMD logo & reads Testing use only.  How do I remove this annoyance?

                                                                                                              AMD 
                                                                                                             Testing
                                                                                                             use only

This is the driver;
ati-driver-installer-8.703-x86.x86_64.run

Thank you.

---

### Post by quadproc on 2010-05-23
> **Chaotic Caveman said:**
> I've just installed the proprietary ATI driver for my Sapphire HD5830.  All seems good except the fact that I'm seeing a "Watermark" on the bottom right of my screen. It has an AMD logo & reads Testing use only.  How do I remove this annoyance?

I don't know how you installed the driver but I do know that the Hardware Drivers function in Ubuntu does not necessarily correctly report your system status.  I am running the ATI version 10.3 fglrx driver right now and the Hardware Drivers utility says "no proprietary drivers are in use" even though it is.

If you allowed Hardware Drivers to select and install the driver then I suggest uninstalling it, downloading the correct driver from the ATI web site, and installing it yourself.  I also suggest putting the downloaded driver into its own directory, cd to that directory, then use
```
sudo sh <the_ati_file_name> --keep --install
```This will leave behind all of the bits and pieces that the installation used so that you can examine them.  The contents of that directory are not needed after the install is complete so you can remove them anytime, or keep them around for reference or examination.

I have noticed that the ATI install scripts sometimes put extra junk into your xorg.conf file so you may need to go into that file and clean it up manually.  In particular, I found duplicates of a lot of things and that seems to confuse the X server so I discarded the duplicates.

Your new driver will not be in use until after you restart the X server.   A reboot will do this or there are a couple of other ways to do it.

Your system may not work well with kernel mode setting (KMS) which is the default for Ubuntu 10.04.  Many people find that they need to say nomodeset in the grub entry.

quadproc

---

### Post by liju.g.chacko on 2012-07-16
Though AMD driver is showing watermark power consumption of my laptop came down by around 2 Watts when compared to driver installed via system settings>additional hardware drivers.

---

