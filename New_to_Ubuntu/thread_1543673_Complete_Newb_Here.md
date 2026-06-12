---
title: "Complete Newb Here"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by elspeck0o0 on 2010-08-01
I downloaded Ubuntu yesterday and I have a couple problems.

1. My laptop is not detecting my WiFi connection. Under Network Connections, Wireless there are no connections available. When I go to 'Add' a connection it asks for SSID, Mode, BSSID, MAC Address, and MUT, along with many other Advanced Options. Not really sure what to do here. I've got my connection's SSID and MAC Address (isn't this the same as BSSID?) but making a new connection with this info still does not work.


2. I am having equal amounts of trouble going back to my Windows 7 OS. When I boot up my system it does not present a choice of operating system. When I had downloaded Ubuntu I selected a manual partition so I figured Windows would still be available.


These seem to be pretty serious issues and I have spent a ton of time trying to fix them already. I would greatly appreciate any help. Sorry for being a complete newb.

---

### Post by ACorder on 2010-08-01
I had the same problem with it not recognizing my wireless card. To fix this problem I had to connect to the internet through a wired connection and download the proper drivers, which Ubuntu automatically found for me.

As far as the Windows issue I'm really not sure, if you didn't accidentally delete the windows partition, it could be something with GRUB. I know there's a function that keeps it invisible unless you hit a certain button during the boot sequence. If that's the case then I think the default button is the spacebar and you can then choose the OS you wish to use from there..that's just assuming that's the problem.

---

### Post by elspeck0o0 on 2010-08-01
> **ACorder said:**
> I had the same problem with it not recognizing my wireless card. To fix this problem I had to connect to the internet through a wired connection and download the proper drivers, which Ubuntu automatically found for me.

As far as the Windows issue I'm really not sure, if you didn't accidentally delete the windows partition, it could be something with GRUB. I know there's a function that keeps it invisible unless you hit a certain button during the boot sequence. If that's the case then I think the default button is the spacebar and you can then choose the OS you wish to use from there..that's just assuming that's the problem.

I was thinking about trying that. Thanks a lot

---

### Post by dreamsR4living on 2010-08-01
Can you run the following code in terminal, or Alt + F2, paste the code and check "Run in terminal" 

```
lspci -v
```

It will output your hardware information. We need to know what wireless card you are using in order to determine what drivers to install for it. Please paste the output in this thread.

If you want to know if your Windows partition is still there go to system > administration > disk utility and select the harddisk which contains your Ubuntu an Windows installation to see if it is still there.

---

### Post by Windows Nerd on 2010-08-01
> **dreamsR4living said:**
> If you want to know if your Windows partition is still there go to system > administration > disk utility and select the harddisk which contains your Ubuntu an Windows installation to see if it is still there.
If it is still there, then Grub should have auto-detected it (Or at least thats what I think Grub2 does, which I assume you are using). If you see no menu, Hold the Shift key right after your BIOS loads and you should see a menu.

If your Windows Partition is there, but does not show up on the Grub2 Menu, you will have to add Windows to your Grub file. Unfortunately I have never used Grub2 so I cannot help you there.

Scott

---

### Post by oldsoundguy on 2010-08-01
> **ACorder said:**
> I had the same problem with it not recognizing my wireless card. To fix this problem I had to connect to the internet through a wired connection and download the proper drivers, which Ubuntu automatically found for me.

Whenever I am setting up an OS on a computer, Linux or Windows, A HARD WIRED connection through my router is much better than ASSUMING the Wi-Fi in the unit will shake hands with the wireless.  
The "my Wi-Fi won't connect" problem is not confined to Linux when it comes to a new install .. be it a full install as the only OS or be it installing on a partition, VM or whatever.

---

### Post by elspeck0o0 on 2010-08-01
My main concern right now is that I'm not having any luck locating Windows on my hard disk.. am I ****ed?

edit: There is a visible partition but it doesn't say anything about Windows on it.

---

### Post by dreamsR4living on 2010-08-01
> My main concern right now is that I'm not having any luck locating Windows on my hard disk.. am I ****ed?

[IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4b.png[/IMG]

What option did you use for partitioning disks? Install side by side, or use and erase entire disk?

If you chose the erase option you indeed have a problem.

---

### Post by dreamsR4living on 2010-08-01
> edit: There is a visible partition but it doesn't say anything about Windows on it.

Can you see what filesystem it uses? NTFS (Windows) or Ext3/ Ext4 (Linux)

---

### Post by dreamsR4living on 2010-08-01
Please give the output of the following command:

```
sudo parted /dev/sda print
```

Alt + F2, paste, Run in terminal, type your password...

This will print your partitions and filesystems.

---

### Post by elspeck0o0 on 2010-08-01
Model: ATA WDC WD3200BJKT-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  250GB  250GB   primary   ext4         boot
 2      250GB   320GB  70.1GB  extended
 5      250GB   320GB  70.1GB  logical   ext4


Yeah I checked out the partitions again. As you can see they're both ext4. I assume all my files are gone along with Windows?

---

### Post by dreamsR4living on 2010-08-01
> Yeah I checked out the partitions again. As you can see they're both ext4. I assume all my files are gone along with Windows?

I am very sorry to say this, but I am afraid that is the case...

This is what it looks like with Windows on my disk;

```
Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  73.4GB  73.4GB  primary   ext4
 2      73.4GB  94.4GB  21.0GB  primary   ntfs            boot
 3      94.4GB  115GB   21.0GB  primary   ext3
 4      115GB   120GB   4631MB  extended
 5      115GB   120GB   4631MB  logical   linux-swap(v1)

```

Edit: Did you back up your essential files before installing Ubuntu?

---

### Post by elspeck0o0 on 2010-08-01
I backed up my hard drive a couple of months ago. Hopefully I can salvage something. Anyway I'm just going to try to move on. 

I ran lspci -v on terminal and got a ton of code. Would you need to see all of it, dreams?

---

### Post by elspeck0o0 on 2010-08-01
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
	Subsystem: Dell Device 0271
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1c00 [size=256]

```

Here's the beginning of it.

---

### Post by dreamsR4living on 2010-08-01
> I ran lspci -v on terminal and got a ton of code. Would you need to see all of it, dreams? 

Anything about network, ethernet or communications controller would be fine. I am sorry for not telling you. 

Use the name and typenumber of your wireless card to find more info on it in combination with Ubuntu on Google and search the Ubuntu Forums for any threads about your card. Big chance you will find what driver to install for your card and if necessary, howto's.

When you post your output here I will have a look at it too, later.

Good luck!

---

### Post by dreamsR4living on 2010-08-01
> 2. I am having equal amounts of trouble going back to my Windows 7 OS. When I boot up my system it does not present a choice of operating system. When I had downloaded Ubuntu I selected a manual partition so I figured Windows would still be available.

I am now reading your post again and see that you have used manual partitioning, which is an expert feature. Next time you should only use it with a good manual. The best option to choose however is the first, install systems side by side and use the slider to define the space for your old Windows and new Ubuntu partition. That way I never lost information, or my Windows partition.

Another downside of partitioning manually is that the output you placed about your partitions is showing me that there is no swap space assigned to the hard disk, which Ubuntu uses when your computer is out of memory. And that your extended partition is over 70GB!! Swap and extended should only be about 2 to 5 GB. That is a lot of space that you are not able to use right now.

I also don't have a clue what happens when your system is running out of memory without a swap space.

I know it might be a frustrating first encounter with Ubuntu and Linux in General, But before you are going to fix the wireless (and if you have not been configuring Ubuntu for many hours), I recommend installing Ubuntu again, using the first option in the partitioning menu. And if you want to have Windows 7 and Ubuntu side by side, first do a basic re-installation of Windows, figure out how much space you need for it (which OS are you going to use the most) and then install Ubuntu and use the slider to assign the right disk space for each OS.

If you need any help reinstalling Ubuntu this can come in handy; [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) and this one about installing Windows or any other OS next to Ubuntu; [https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)

Pls let me know what you are going to do, and good luck again!

---

### Post by Kixtosh on 2010-08-01
DreamsR4 is right on the money in my opinion. Since you have blasted your W7 off the face of the planet by accident, at this point, unless you urgently need W7 back again, I would simply install Ubuntu all over again, using the "erase and use entire disk" option, and go from there. You won't have to specify the size of any partitions that way, and it's much easier as a new user.

The *lspci -v* output requested earlier will show all your devices, including any that might be causing issues with wireless operation, but I would still install Ubuntu properly first, and try to fix wireless (if it still needs fixing by then) later.

Best of luck!

---

### Post by elspeck0o0 on 2010-08-01
[FONT="Verdana"]How do you mean install it properly? Are you saying I should clean out everything, then reinstall Windows 7 first, then go through and install Ubuntu with appropriate partitions?[/FONT]

---

### Post by waynefoutz on 2010-08-01
> **elspeck0o0 said:**
> [FONT="Verdana"]How do you mean install it properly? Are you saying I should clean out everything, then reinstall Windows 7 first, then go through and install Ubuntu with appropriate partitions?[/FONT]

The easiest way to go is to install Windows 7, have it delete all partitions, format the entire disk, then install Ubuntu again, his time make sure you set it up right to dual boot. Installing Windows after Ubuntu wipes out the grub menu.

---

### Post by PremiereWebDesign on 2010-08-01
> **elspeck0o0 said:**
> [FONT=Verdana]How do you mean install it properly? Are you saying I should clean out everything, then reinstall Windows 7 first, then go through and install Ubuntu with appropriate partitions?[/FONT]
I agree totally with Waynefoutz. After reinstalling Windows 7, then reinstall Ubuntu. During the installation, you will see a screen that asks you "Where do you want to install Ubuntu". Be sure that you select the option to install side by side, choosing between them each startup."
This option will allow you to choose either Windows 7 or Ubuntu every time you boot your computer.

---

### Post by dreamsR4living on 2010-08-02
> The easiest way to go is to install Windows 7, have it delete all partitions, format the entire disk, then install Ubuntu again, his time make sure you set it up right to dual boot. Installing Windows after Ubuntu wipes out the grub menu. 

> I agree totally with Waynefoutz. After reinstalling Windows 7, then reinstall Ubuntu. During the installation, you will see a screen that asks you "Where do you want to install Ubuntu". Be sure that you select the option to install side by side, choosing between them each startup."
This option will allow you to choose either Windows 7 or Ubuntu every time you boot your computer. 

This is exactly what I am proposing.

> How do you mean install it properly? Are you saying I should clean out everything, then reinstall Windows 7 first, then go through and install Ubuntu with appropriate partitions?

Indeed the Windows 7 install should do the cleaning, it has to format the entire disk. During the Ubuntu install you will define the size of the Ubuntu and Windows partitions, using the install side by side option and use the slider to specify the sizes.

Edit: You should only install Windows 7 if it is your wish to use both Windows and Ubuntu. I would recommend it though, as you are new to Ubuntu. When something doesn't work the way you want to, or when something goes wrong entirely, you'll always have Windows to fall back to.

I myself have a Windows XP partition, that I never use, just in case something happens, but I am using Ubuntu since 2006. Because of playing around in Ubuntu, it saved me more than once.

---

### Post by Kixtosh on 2010-08-02
Just to clarify what everyone has been saying:
 
1) If you want W7, then you will have to re-install it. It will wipe the drive clean, including Ubuntu, in the process.
 
2) If you want dual boot with W7 and Ubuntu, you should really install W7 first (wiping the hard drive at the same time), then install Ubuntu again using the default "side by side" installation procedure. You cannot easily add W7 once Ubuntu has already been installed. It's better to install W7 first, and Ubuntu second.
 
3) If you want to just try Ubuntu first, and get it working properly before you decide if you ultimately want to keep it, then I would still go through a completely new Ubuntu install, wiping the hard drive entirely ("use entire disk" option) since the current installation is not optimal and is not working properly. You can do this without installing W7 first for now, mostly to save all the time it takes to install W7 (and everything that goes with it, inlcuding applications, virus protection, firewall protection, etc. etc.). 
 
So why choose option (3) when you'll still have to install W7 later? 
 
Well firstly, you can adequately work out your wireless issue first, and only then decide if you want to keep Ubuntu or not. If you decide not, then you'll simply wipe it out with your new W7 install when that time comes.
 
Secondly, if you follow option (3) and then decide that you DO want to have a dual boot option with W7 (probably the best option, as DreamsR4 suggests), you can then go ahead and install W7. Yes, it will wipe your new, now fully functional Ubuntu completely. Yes, you will have to install Ubuntu all over again, but honestly, installing Ubuntu again (once you have worked out your wireless problem) is really not much of an issue. Believe me: it's actually fairly simple and not in the least bit scary once you've done it twice already. At least you will know by then why this might be worth all the effort.
 
When everything is working, you won't have to worry about any of this again. The only wrong decision at this point is to give up, or not bother, because you hit a bump along the road! Best of luck.

---

### Post by alanrlow on 2010-08-02
A couple of other thoughts. Running a "live CD" is a good way to try things out before you install and once you have wireless sorted will make installing easier with net access.
Another under reported trick is to install your "HOME" on a separate partition. This way you can re-install the OS as often as you like and even try different distros without losing your data and setup as long as you tell it not to format your home partition. When installing go very slowly and read EVERYTHING and be sure you understand it before moving on.
Good luck and don't get discouraged, it's well worth the time and effort to change.

---

