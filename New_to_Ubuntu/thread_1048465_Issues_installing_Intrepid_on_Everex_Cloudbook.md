---
title: "Issues installing Intrepid on Everex Cloudbook"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Nxion on 2009-01-23
OK so I decided to put Intrepid on this netbook. Everything seems to go fine with the install but I have one problem. The issue is there is no cdrom on the machine but it has the ability to install via usb drive. I used Unetnbootin to load a net install version on the pen drive. THe whole install goes as planed except when it gets to the boot loader part. When it goes to install grum instead of loading grub on the internal harddrive, it wants to load it on the pendrive!

Does anyone know a way around this? This is the only issue I have come across with te install and I can't seem to get past it lol.

---

### Post by northern lights on 2009-01-23
During the installation process, you can choose where to install GRUB. Watch out for the option. It's after partitioning and before selection of *ubuntu-desktop* as additional package.

---

### Post by Nxion on 2009-01-23
OK, maybe I over looked that option. I don't have the laptop in front of me at the moment. If I remember correctly the option to install GRUB was near the end but it did not give me a choice. One of the issue I think contributed to this is that the usb drive was being recognized as scsi1 and the internal hard drive was scsi4.

---

### Post by Nxion on 2009-01-23
Also like I mentioned I am using a net install version so it does not have the GUI

---

### Post by stchman on 2009-01-23
> **Nxion said:**
> OK so I decided to put Intrepid on this netbook. Everything seems to go fine with the install but I have one problem. The issue is there is no cdrom on the machine but it has the ability to install via usb drive. I used Unetnbootin to load a net install version on the pen drive. THe whole install goes as planed except when it gets to the boot loader part. When it goes to install grum instead of loading grub on the internal harddrive, it wants to load it on the pendrive!

Does anyone know a way around this? This is the only issue I have come across with te install and I can't seem to get past it lol.

I installed Intrepid on my Acer Aspire One with no issues.

I used the Create USB drive on another machine to make a bootable USB drive from the Intrepid .iso I downloaded.

After that I booted by AA1 off the USB and selected install.  During Install I selected whole disc and everything went along smoothly.

After installation I rebooted into Ubuntu.  My AA1 has an hdd as well not an SSD.

---

### Post by Nxion on 2009-01-23
> **stchman said:**
> I installed Intrepid on my Acer Aspire One with no issues.

I used the Create USB drive on another machine to make a bootable USB drive from the Intrepid .iso I downloaded.

After that I booted by AA1 off the USB and selected install.  During Install I selected whole disc and everything went along smoothly.

After installation I rebooted into Ubuntu.  My AA1 has an hdd as well not an SSD.

Well I guess I will try it that way. I don;t know if it will make a difference or not. Did you use a alt install image with the text install mode or the gui install mode?

---

### Post by northern lights on 2009-01-23
> **Nxion said:**
> Also like I mentioned I am using a net install version so it does not have the GUI
This option exists in the alternative GUI also (Though you've only got 16 colors and crude '80s graphics, it's still a GUI).

As an aside, in the normal installation, you don't have to select *ubuntu-desktop* manually either.

---

### Post by mrbiggbrain on 2009-01-24
i would actualy sujest that you invest in an externel cdrom drive, it makes life alot easier with a netbook :-)

---

### Post by Nxion on 2009-02-04
Well I ended up getting Crunchbang installed on a USB drive and loading it on the netbook that way. It went pretty smoothly, I am liking this netbook :)

---

### Post by Nxion on 2009-03-09
:)

---

