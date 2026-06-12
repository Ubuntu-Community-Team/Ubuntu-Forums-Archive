---
title: "unetbootin help!!"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by JohnCDI on 2009-11-12
I'm trying to install ubuntu on a laptop where the cd drive is fried and i dont have the option to install through usb ive gotten unetbootin on the laptop and got through parts of the install up until it starts the partitioner at that point it doesnt recognize my hard drive any advice would be appreciated

---

### Post by coldReactive on 2009-11-13
Do you know what model computer you have? Has the harddrive been upgraded?

---

### Post by jimmy the saint on 2009-11-13
I don't understand.  Try some punctuation to make your question understandable. 

Are you saying that Unetbootin cannot create the bootable USB?

you say you don't have the option to install through USB.  What do you mean by that?

Or are you saying that you did make and boot off the USB, but the Ubuntu installer cannot detect your HD?

---

### Post by Paqman on 2009-11-13
Did you check the integrity of the .iso you downloaded? If that's ok, try running it through Unetbootin again. I'd also try Ubuntu's USB Startup Disk Creator if you have a working Ubuntu machine handy.

If none of that works it's probably your hardware. If the laptop is failing to recognise an optical drive it may well also be having trouble with a hard drive.

---

### Post by coldReactive on 2009-11-13
> **Paqman said:**
> If none of that works it's probably your hardware. If the laptop is failing to recognise an optical drive it may well also be having trouble with a hard drive.

Some laptops use module interfaces so that drives like the optical drive are hot swappable (IE: IBM ThinkPad T41.)

That's why it's imperative that we know the model/etc. of the laptop.

---

### Post by JohnCDI on 2009-11-13
the model of the laptop is a thinkpad r51 i don't have the option for a USB install because i dont own a flash drive.

---

### Post by bennachie on 2009-11-13
I assume that you are using Unetbootin to download the distribution directly and proceed straight to installation. While the process should certainly work, I haven't personally tried it (it's easier to verify the integrity of the ISO when you download it directly - and, of course, verification is automatic if you use Torrent). Incidentally, 2GB flash drives are more or less being given away with the breakfast cereal at my local computer "supermarkets" - around $AUD 5 seems typical.

The most likely problem is that something has gone wrong in the download process, but more detail about your system would be helpful in assessing the options for fixing the problem (as suggested by a previous contributor).

I don't think that USB Drive Creator offers any compelling benefits over Unetbootin UNLESS you really want the "persistence" feature. In fact, it would be nice if Ubuntu would follow the lead of other distros and use hybrid ISOs that can be installed to a flash drive without any special software.

---

### Post by JohnCDI on 2009-11-13
sorry for not stating no im not using it to download the iso i already have the iso on the HD and im choosing the file with unetbootin then choosing the hard drive option it proceeds then i reboot i choose unetbootin from bootloader then you can start the install it gets up to where it starts the partitioner when the partitioner starts it shows no drives

---

### Post by NickJones on 2009-11-13
Put in your USB, go to My Computer and make a note of the drive letter, then fire up Unetbootin, select the ISO, and then make sure the drive letter is the same as your USBs and click install.
Then boot off the USB.

---

### Post by JohnCDI on 2009-11-13
i do not have a flash drive to use.....

---

### Post by bennachie on 2009-11-13
Your simplest solution would certainly be to buy or borrow a flash drive. While I've never actually tried to do what you are attempting, I suspect that the installer will (understandably) balk at partitioning the drive that contains the active operating system. The option provided in Unetbootin would make sense if you had multiple hard disks.

---

### Post by Paqman on 2009-11-14
> **JohnCDI said:**
> i already have the iso on the HD

In that case you can very easily install the system using [Wubi]("http://wubi-installer.org/") (assuming you have a working Windows install on the machine)

Just download [wubi.exe]("http://wubi-installer.org/images/download-button.jpg") and make sure it downloads into the same folder as your .iso. Then run wubi.exe and allocate at least about 8GB of space to Ubuntu. It'll set up a dual boot system with Ubuntu on a virtual partition located on the NTFS partition.

---

