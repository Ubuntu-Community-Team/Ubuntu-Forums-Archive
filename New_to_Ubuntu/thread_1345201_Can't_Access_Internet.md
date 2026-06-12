---
title: "Can't Access Internet"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by bogie1977 on 2009-12-03
Brand spanking new to xbuntu, just built my own computer last night and wanted to go another route than windows 7.  Anyways I got it connected to the router but not sure what to do next, with windows it detected the network automatically and all I needed was the wep.

Not sure where to even start with this to get it going.

---

### Post by cariboo on 2009-12-03
A few more details would be good. I'm not sure if you are connecting wired or wireless.

Click on the network-manager icon in the top panel and see if any wireless networks show up, if you are using wireless.

---

### Post by lisati on 2009-12-03
Try to use WPA or stronger instead of WEP if you can.

---

### Post by 3rdalbum on 2009-12-03
Have you got the Network Manager applet on your panel? (it will probably look like two little computers). If you click that, does it show wireless networks?

If it doesn't, then you might need to install a driver; connect your computer to your router via an Ethernet cable so you can get a connection, go into Synaptic Package Manager and click Reload, then close it and go to Hardware Drivers and see if it lists any drivers that can be downloaded and installed.

If it doesn't show any, then you might need to install a driver manually. In order to suggest a driver to you, we'll need the output of the following two commands:

```
lspci
lsusb
```

---

### Post by bogie1977 on 2009-12-04
I might have said this wrong or led you astray in my first post.  I have an Ethernet cord running from the router to the computer, so its not wireless.  I do have a linksys wireless network adapter but not sure if it would work with xubuntu or not and not sure where the install disk is.

Does this change anything?

---

### Post by bogie1977 on 2009-12-04
Maybe I led you astray with my first post.  I have a ethernet cord running from the router to my computer.  I do have a linksys wireless adapter that plugs in usb but not sure if I have the install disk still or if it will even work with xubuntu.

Does this change anything?

---

### Post by PariahVayne on 2009-12-04
x

---

### Post by bogie1977 on 2009-12-04
Tried the adapter but the light just stays on and never starts blinking which it does on my old computer which I'm using it on now.  Do I need to manually set something up or get information from the router to use my ethernet card in my pc?  With windows when I plugged it in it was automatically detected, guessing thats not so with xubuntu.

---

### Post by PariahVayne on 2009-12-04
x

---

### Post by bogie1977 on 2009-12-04
nothing there.  the light should start blinking after a few seconds i would assume as it does on my old pc here.  My big issue here is im doing my internet stuff here on my old pc...wondering if I need a driver

---

### Post by MooPi on 2009-12-04
You should use these comands in terminal  to let everyone know what is in your computer.
We can't help if we don't know what is under the hood.

> lspci    lsusb

---

### Post by PariahVayne on 2009-12-04
x

---

### Post by bogie1977 on 2009-12-04
Ok I'm thinking maybe I need to try reformatting (uninstall xubuntu completely) the drive and reinstall xubuntu with my pc connected to the router...just realized I didn't hook it up until after I installed xubuntu so maybe thats why its not working?  Maybe?

---

### Post by bogie1977 on 2009-12-04
> **PariahVayne said:**
> Weird O.O

Are you sure the USB port isn't dead?

I can do that but will take a few since I will have to copy and paste it into a file and transfer it using my external drive to this computer.  Will go run those commands now.  

While I'm doing that, should I do what I mentioned above and how if so.  Thanks for the help, I'm really fustrated...never realized how lazy windows makes ya.

---

### Post by Metallion on 2009-12-04
I don't think reformatting would with it in the drive would help. Let's just see what those commands tell us first.

Can you tell us which wireless adapter it is exactly? Does it show a model number anywhere?

Btw an easier way to get those commands' output into a file is this:

```
lspci >> file.txt
lsusb >> otherfile.txt
```

---

### Post by bogie1977 on 2009-12-04
Here's the lspci:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)


Gotta go get the lsusb again cause it file wont read in notepad.

---

### Post by bogie1977 on 2009-12-04
I'd prefer not to use the wireless adapter and don't think I can as on the support site it says minimum requirements only lists windows os.  I have it wired to my router with the ethernet cord and would like to have it wired as its better connection.  I built this computer myself last night so this could be another factor.

---

### Post by MooPi on 2009-12-04
Thank you bogie, it looks as if your ethernet adapter is not recognized correctly. It may not be a Linux compatible device or is malfunctioning.

> 01:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)

---

### Post by bogie1977 on 2009-12-04
Here's the lsusb:

Bus 005 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Metallion on 2009-12-04
Thanks, for the output. :) I found another thread about your issue and it looks like the OP has managed to solve it.

Here's his thread:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

Here's what he did:

> 1) I installed ubuntu hardy 64bit, i has build-essential package installed
2) Then i downloaded the linux driver from: [http://support.asus.com/download/dow...model=P5KPL-CM](http://support.asus.com/download/dow...model=P5KPL-CM)
(as per my original post)
3) I then transfered the driver via usb stick to my laptop and unpacked the zip. (Actually i unpacked it on windows first as it has a .rar file that i could not unpack on linux Then i packed it up again on windows).
4) cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src
5) then i ran: sudo KBUILD_NOPEDANTIC=1 make
6) then i ran: sudo KBUILD_NOPEDANTIC=1 make install
7) that worked and put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/at1le.ko
8 ) i cd into that director and i run: sudo insmod ./atl1e.ko

I hope this helps. It looks like you will need to install the build essentials package to do this though.

---

### Post by bogie1977 on 2009-12-04
> **Metallion said:**
> Thanks, for the output. :) I found another thread about your issue and it looks like the OP has managed to solve it.

Here's his thread:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

Here's what he did:



I hope this helps. It looks like you will need to install the build essentials package to do this though.

I just found that post with google myself but all I have is the xubuntu disk I bought at microcenter when I bought the stuff to build my computer.  Really fustrating that I can build a computer but can't get internet on it lol.  But anyways my cd rom doesnt work on my old computer which is the only place I have internet.

The question is how do I modify the instructions to get it working with the current install I have or do I have to reinstall xubuntu with this other build or something.  I'm losing hair by the seconds tonight.

---

### Post by MooPi on 2009-12-04
I found another post from the forum that will probably scare you but it lists a solution for your problem. I have a question though, What version of Xubuntu are you using. If your not using a current version you may want to try the latest Xubuntu first. Here is the other link:

[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

---

### Post by bogie1977 on 2009-12-04
Gonna go have a smoke to ease my stress...will be back in 15 minutes or so.

---

### Post by MooPi on 2009-12-04
Okay while your out smoking I'll type. Try downloading the latest iso for Xubuntu and transfer via flash drive to your new computer and burn the image to disk. Since this was a new installation you won't be loosing anything by reinstalling. Hopefully the latest kernel will have the info for your ethernet adapter.

---

### Post by Metallion on 2009-12-04
I don't think you need to modify the commands for your current install. What happens when you try them out?

In case it complains about not finding make or gcc or something you can try this:

```

Put your Xubuntu CD into the drive.
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

Then try the commands from my previous post again.

---

### Post by bogie1977 on 2009-12-04
> **Metallion said:**
> I don't think you need to modify the commands for your current install. What happens when you try them out?

In case it complains about not finding make or gcc or something you can try this:

```

Put your Xubuntu CD into the drive.
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```Then try the commands from my previous post again.

 Will that work with my dvd rom/burner as well?

---

### Post by Metallion on 2009-12-04
As long as it can read the CD i think it should work. :) I'm assuming it's where you installed Xubuntu from? If yes, then it should work.

---

### Post by bogie1977 on 2009-12-04
> **Metallion said:**
> I don't think you need to modify the commands for your current install. What happens when you try them out?

In case it complains about not finding make or gcc or something you can try this:

```

Put your Xubuntu CD into the drive.
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```Then try the commands from my previous post again.


Okay I ran the above commands (one at a time I assumed) and the first two did nothing but when I entered the install build-essential...it seemed to do something.  Am I right?

Here's what I got from all three commands, scroll down and you'll see the build-essential:

> bogie@Bogart:~$ sudo apt-cdrom add
[sudo] password for bogie: 
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter    
Mounting CD-ROM...
Identifying.. [8092bea177fc0ad6e0f8e1322783529e-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)'
Copying package lists...gpgv: Signature made Wed 02 Jul 2008 06:23:29 AM CDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
bogie@Bogart:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done          
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
bogie@Bogart:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done          
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
bogie@Bogart:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 upgraded, 9 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/8703kB of archives.
After this operation, 34.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-libc-dev.
(Reading database ... 90763 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.34_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.24-19.34) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...


---

### Post by bogie1977 on 2009-12-04
Oh and btw still no internet after running those commands.  SHould I restart?  Whats next?

---

### Post by bogie1977 on 2009-12-04
Okay I downloaded and transfered the drivers listed on this thread to my computer:  [http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

I transfered the drivers file to my computer using my external hard drive but now I can't open the zip files on xubuntu as I get an error it cant open it.  So I unpacked them on windows again and tried using terminal to open the files unpacked...either this won't work or I can't figure out the command to CD.

> 4) cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src

what exactly do I need to input for <HOME_DIR> to get it to work??

---

### Post by bogie1977 on 2009-12-04
I somehow got it working ... I'm now on my new computer and xubuntu.  I feel like a new journey is about to begin.  Where's my beans? =)

---

### Post by bogie1977 on 2009-12-04
Ok now I got totem to work and play movies from my external hard drive but now there is now sound.   I'm thinking I need to install the audio drivers but not sure how.  Any advice?

---

### Post by Sylslay on 2009-12-04
long day bogie1977?

is any sound at all?
see for drivers :
type
lsmod 
and look for anything lake : 
soundcore               7264  1 snd
snd_page_alloc          9252  2 snd_intel8x0,snd_pcm


what kind of movie is it? 

as you got internet now, install all codec 
in console :

sudo apt-get update
sudo apt-get install ubuntu-restricted-extras

about 90Mb off all stuff ,that you need?

ps. can you post : lsub with internet adapter plug in into usb,

thah we know what vendor build it and what chip they used.:popcorn:

---

### Post by Metallion on 2009-12-04
Alright I'm happy to hear that you have internet working now! :D

About the sound, before we try something rash... Are you sure the volume isn't just muted?

Is there an icon that looks like sound settings in your panel? If not, try opening a terminal and type alsamixer.

You should be able to set the volume from there.

---

### Post by bogie1977 on 2009-12-04
Okay I ran the alsamixer command and now i have sound but its just audible at the highest setting.  Maybe I need new speakers...time to go shopping again.

---

### Post by Metallion on 2009-12-04
> **bogie1977 said:**
> Okay I ran the alsamixer command and now i have sound but its just audible at the highest setting.  Maybe I need new speakers...time to go shopping again.

Could be but did you move all the sliders to the max? The volume shouldn't be much different than it is in windows or another OS. It could be the speakers like you say but just trying to rule out that it's a setting. :) Perhaps you can try putting the speakers on your other comp and see what volume they have there first. Would be a waste to buy new speakers if it's not really needed.

Edit: You could also try to plug in a headphones or some other speakers and see if the volume is ok then. Just making sure the speakers are at fault :)

---

### Post by bogie1977 on 2009-12-04
Well with my dinosaur of an emachines the speaker volume was fine but I had a new laptop for like 6 months before a water leak damaged it and the speakers had the same issue I'm having here except you could barely hear em.  They aren't new speakers and have been beat up over the years, probaly will try new ones just to see.  I'll let ya know.

Having a few other issues...like installed flash player (yes even the restricted extras or something as told) and flash won't work in firefox, or let me say it won't let me play two games ... quickhit.com or gridironlive (facebook app).  Loads the warning that I don't have flash and to install yet when I check firefox it shows it as an extention and when i load synaptic package manager it says I have flash as well.  I think quickhit requires adobe air which might be part of the problem, having figured out how to get that on xubuntu.  

The other weird thing is I can use hulu.com which I thought used flash for videos, could be wrong on that though.

---

### Post by Metallion on 2009-12-06
Does Flash work on other websites? What happens when you use another browser?

---

### Post by Satendra.kohli on 2009-12-06
i have same problem.....

---

