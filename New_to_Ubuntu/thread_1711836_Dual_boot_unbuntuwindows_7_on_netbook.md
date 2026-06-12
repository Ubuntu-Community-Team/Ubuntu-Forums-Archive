---
title: "Dual boot unbuntu/windows 7 on netbook"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Perfect_Illusion on 2011-03-21
I got a new netbook today that came with Windows 7 Starter and I want to give unbuntu a try. I've read over a couple guides, all of which requires unbuntu to be installed 1st then installing Windows 7 after the fact. The question I have is that my netbook didn't come with a Windows 7 installation disk because netbooks have no disk drives. The 200GB hard drive is partitioned into two 100GB disks, So I'm assuming one drive has a back up on it.

I would like to know how to go about setting up a dual boot cleanly and safely. I'm not really worried about losing any data on netbook as I have had it for less than 24 hours but I don't want to do something stupid and corrupt the drive with no way to re-install Windows.

The netbook I have is ASUS Eee PC 1015PED-PU17-BK

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220782](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220782)

Any links or help would be greatly appreciated! :)

---

### Post by wilee-nilee on 2011-03-21
You have more then two partitions most likely they are hidden. You also can start with a wubi install if you want or a full partitioned install. The wubi is just a file inside windows that boots, basically for trying it out.

You will need a bootable Ubuntu in general can you load a thumb with Ubuntu and take a screen shot of gparted?

Don't worry about the install order here.

---

### Post by Perfect_Illusion on 2011-03-21
I in ubuntu right now. Trying to set up and connect to my wirless router but Google is failing me. I little light says my wifi is on but I dont think the OS acknowledges that because hitting the button doesnt turn it off. This is alot different than I thought it would be but I'll play around with it to see if I can figure it out. Any help would be appreciated

---

### Post by mcavoybn on 2011-03-21
Are you in the virtual environment inside of Windows, or did you partition and install Ubuntu completely??

---

### Post by Perfect_Illusion on 2011-03-21
I used the windows installer from this link:
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

The computer restarted into ubuntu. Do I need to fully partition the drive to get it work?

When I boot up my computer I get the option to start Windows or Ubuntu.

---

### Post by mcavoybn on 2011-03-21
Yes, what you did was an install WITHIN windows. Basically it just booted from the ubuntu files you downloaded, and loaded like sort of a game, a kind of full screen program, that looks and functions just like Ubuntu (tbh I don't really know much about how it works XD). 

What you need to do if you want to run the FULL version of Ubuntu is go here:

[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Follow the steps, they are very easy and made so anybody can do it. Since you have a netbook, you are going to want to find a usb drive (you don't have a cd-rw drive right?) and put the ubuntu installer onto the usb. You will probably end up booting from the usb drive, and then following the instructions you are prompted with once the computer boots up.

What you will be doing is creating a new partition on your hard drive, that ONLY linux will be able to use. This will install the full version of linux onto your newly created partition, and from then on you will be able to choose, on startup, which operating system you wish to boot to.

If none of what I said makes sense to you, just follow the instructions on the link provided, and everything should run very smoothly. Make sure to read EVERYTHING about what you are doing with your hard drive, and keep yourself educated about what you are doing, so you don't mess anything up.

---

### Post by adduds on 2011-03-21
also if you do make a bootable USB stick...i suggest trying ubuntu before partitioning and installing!

unlike windoze you have the option to try ubuntu install ubuntu...just a good way to make sure everything works on your computer

---

### Post by wilee-nilee on 2011-03-21
Your wireless setup is probably broadcom which needs some tweaking, here is a link to get you started, identify this with the command at the top of the page.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Since your installed and this is a different problem you may want to start a thread with a specific header, for help.

This card would not work in better in a partitioned boot then the wubi setup you have now.

---

### Post by Perfect_Illusion on 2011-03-21
That makes sense. Do I need to do anything like shrink the partitions made by windows? I have two 100GB, one 20MB, and one 15GB partition. Or will ubuntu just steal what it needs from windows? Can I just use the partiton utility in windows to delete a 100GB partition entirely?

---

### Post by Perfect_Illusion on 2011-03-22
> **adduds said:**
> also if you do make a bootable USB stick...i suggest trying ubuntu before partitioning and installing!

unlike windoze you have the option to try ubuntu install ubuntu...just a good way to make sure everything works on your computer

Yeah thats what I did. Everything worked fine except for the wifi.

---

### Post by mikewhatever on 2011-03-22
> **Perfect_Illusion said:**
> That makes sense. Do I need to do anything like shrink the partitions made by windows? I have two 100GB, one 20MB, and one 15GB partition. Or will ubuntu just steal what it needs from windows? Can I just use the partiton utility in windows to delete a 100GB partition entirely?

You could resize one of the existing partitions to carve some dedicated space for Ubuntu, but an 'inside Windows' install is also fully functional. Since you aren't sure if you want to use Ubuntu, I'd recommend installing inside Windows.

---

### Post by mcavoybn on 2011-03-22
> **Perfect_Illusion said:**
> That makes sense. Do I need to do anything like shrink the partitions made by windows? I have two 100GB, one 20MB, and one 15GB partition. Or will ubuntu just steal what it needs from windows? Can I just use the partiton utility in windows to delete a 100GB partition entirely?

When you start up the Ubuntu installation, there will be a slider that looks like this: 
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_04_medium.jpg[/IMG]

It will show all your current partitions, and allow you to adjust the size of your new ubuntu partition.

---

### Post by Perfect_Illusion on 2011-03-22
Thanks guys. I cleared 120GB of unallocated space and I'm current downloading the iso. Thanks for the help. I'm sure you'll hear from me again thou lol

---

### Post by Perfect_Illusion on 2011-03-22
Ran into my 1st issue trying to install unbuntu. The BOIS on the netbook is funky. I think I need the command prompt way of booting from the USB drive. I dont know command prompt off top of my head. The is screen I get when I boot up and press f10 and f2

---

### Post by adduds on 2011-03-22
that theres no bios :P

i don't think...

did you try f1 esc and del aswell?

---

