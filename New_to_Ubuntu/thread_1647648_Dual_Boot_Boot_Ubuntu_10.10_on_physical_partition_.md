---
title: "Dual Boot: Boot Ubuntu 10.10 on physical partition natively *and* virtually; How?"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by SimonHF on 2010-12-17
I have system which originally had a single partition with Windows 7 on it. I then installed Ubuntu 10.10 as dual boot (Ubuntu automatically shrunk the Windows partition, created the new partition for Ubuntu, and added the grub OS selection thing). Now I can boot into either Windows 7 or Ubuntu 10.10. I installed the Ubuntu drivers for an NVidia GTS 450 graphics card.

Now I'd like to be able to boot into Windows 7 and start Ubuntu 10.10 on the physical partition using either VirtualBox or VMware. And I'd also like to be able to re-boot directly into Ubuntu (without Windows) too.

I've seen lots of posts relating to doing this the other way around. But how to set this up for Ubuntu? And would it be better to do this with VirtualBox (better for desktop rendering performance?) or VMware? How would I configure Ubuntu to use the NVidia settings when booted directly via dual boot, and the virtual graphics card settings when booted as a virtual machine from the Windows host?

Thanks in advance.

---

### Post by hwychld on 2010-12-17
Using Windows as the Host operating system it is possible to run Ubuntu in a virtual machine.  It will not be able to load this image from the dual boot Ubuntu partition.  VMs create their own virtual disk image that appears just like a regular (albeit large) file on your windows system.  

As for Virtual Box or VMware, both are really solid and would do what you need to do very easily.  I have used both and prefer Virtual Box, but have talked to many others that prefer VMWare.

---

### Post by SimonHF on 2010-12-17
Thanks for the response. I'm not sure about VirtualBox, but in VMware there are three ways to create the disk for the guest:
1. Virtual disk that grows (appears as a file(s) on host OS)
2. Virtual disk that is fixed (appears as a file(s) on host OS)
3. Physical partition (see [http://www.vmware.com/support/ws55/doc/ws_disk_raw_install_os.html](http://www.vmware.com/support/ws55/doc/ws_disk_raw_install_os.html))

Are you saying that (a) VirtualBox doesn't support the physical partition mechanism, and/or (b) the physical partition mechanism uses a different format to a regular, non-vm physical partition?

In searching for the last link, I found the following link :-)
[http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html](http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html)
[http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html](http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html)

Unfortunately, it doesn't say anything about how to configure the guest OS. Does anybody know how to configure a Ubuntu guest? And does VirtualBox support physical partitions? It would be annoying if only VMware supports physical partitions and only VirtualBox supports graphics acceleration...

---

### Post by SimonHF on 2010-12-17
A bit more Googling has found me the following interesting links to try out:
1. "Unable to boot raw Ubuntu 10.04 LTS 64bits from Win7 64bits" [http://forums.virtualbox.org/viewtopic.php?f=6&t=36534&p=163746&hilit=physical+partition#p163746](http://forums.virtualbox.org/viewtopic.php?f=6&t=36534&p=163746&hilit=physical+partition#p163746)
2. "Tutorial: Boot existing Ubuntu Partition using Virtualbox inside Windows (deprecated)" [http://www.ltyer.com/wordpress/tutorial-boot-existing-ubuntu-partition-using-virtualbox-inside-windows](http://www.ltyer.com/wordpress/tutorial-boot-existing-ubuntu-partition-using-virtualbox-inside-windows)
3. "Tutorial: Boot Ubuntu 9.10 Partition using Virtualbox inside Windows (deprecated)" [http://www.ltyer.com/wordpress/tutorial-boot-ubuntu-9-10-partition-using-virtualbox-inside-windows](http://www.ltyer.com/wordpress/tutorial-boot-ubuntu-9-10-partition-using-virtualbox-inside-windows)

Unfortunately, there appears to be no current tutorial for the latest grub / ubuntu combination :-(

---

### Post by SimonHF on 2010-12-17
Another link reporting failure with VirtualBox:
"Running Ubuntu 10.04 from a physical partition" [http://forums.virtualbox.org/viewtopic.php?f=6&t=31771&p=145583&hilit=physical+partition#p145583](http://forums.virtualbox.org/viewtopic.php?f=6&t=31771&p=145583&hilit=physical+partition#p145583)

---

### Post by SimonHF on 2010-12-17
Another interesting link using 'coLinux' which I'm not sure will do what I want and/or optimize graphics:
"Is it possible to load my installed Ubuntu from my windows(XP, Vista, 7)?" [http://askubuntu.com/questions/1986/is-it-possible-to-load-my-installed-ubuntu-from-my-windowsxp-vista-7](http://askubuntu.com/questions/1986/is-it-possible-to-load-my-installed-ubuntu-from-my-windowsxp-vista-7)

---

### Post by SimonHF on 2010-12-18
Now my problem is partly solved!

The solved bit:

I followed the instructions here:
[http://www.ltyer.com/wordpress/tutorial-boot-ubuntu-9-10-partition-using-virtualbox-inside-windows](http://www.ltyer.com/wordpress/tutorial-boot-ubuntu-9-10-partition-using-virtualbox-inside-windows)

Notes which made this tutorial work for me:

I had to use this command because I had a newer grub:
sudo grub-mkrescue --output=GRUB2CD.iso /boot/grub

The 'VBoxManage.exe' had to be run 'as administrator' for it to work for me using Windows 7.

Because I don't have Ubuntu on a separate disk, but on a separate partition of my only disk then I had to use this command instead (note the zero on the end):
VBoxManage.exe internalcommands listpartitions -rawdisk \\.\PhysicalDrive0

Again, because of the partitions containing Ubuntu then I had to use this command (note windows for me is on partitions 1 & 2, while Ubuntu is on 5 & 6):
VBoxManage.exe internalcommands createrawvmdk -filename C:\ubuntu.vmdk -rawdisk \\.\PhysicalDrive0 -register -partitions 5,6

When running VirtualBox then I had to run it 'as administrator' to be able to access the raw disk partitions.

The unsolved bit:

So now I can boot and log into my Ubuntu 10.10 running using the physical partition mounted by VirtualBox running in Windows 7. However, I only get terminal access and no desktop. Well, the tutorial does say the following:

"It doesn’t seem to like nvidia drivers in this release so you might have to reset your x.org for it to work inside a VM. Just have to live with the lack of acceleration!"

When I boot natively into Ubuntu then I get the desktop using the NVidia drivers and everything looks great. So how to get Ubuntu to start the desktop using the video acceleration provided by VirtualBox?

Do I need two X configs?

If so, how automatically use the right one?

---

### Post by SimonHF on 2010-12-18
So in order to get at accelerated Ubuntu desktop up and running under VirtualBox then I had to do the following steps:

Step 1: Don't install OS upgrades because apparently there is a buggy package which causes the default gnome and very ugly desktop theme to show and you can never select the new and sexy aero themes ever again.

Step 2: Uninstall the NVidia drivers, otherwise it won't be possible to switch on desktop acceleration inside Ubuntu. I did this with the following command:
sudo apt-get --purge remove nvidia-*

Step 3: Follow the instructions here:
"HOWTO: Install Linux Guest Additions + Xorg config"
[http://forums.virtualbox.org/viewtopic.php?t=15679](http://forums.virtualbox.org/viewtopic.php?t=15679)

Now the only draw back is that VirtualBox does not support multiple monitors... I guess you can't have everything.

Next thing I need to do is figure out how to be able to swap between the VirtualBox and NVidia drivers depending upon how Ubuntu was booted... any ideas anyone?

---

### Post by SimonHF on 2010-12-19
Okay, so I rebooted into Ubuntu natively to install the NVidia drivers. Before doing so, I save the /etc/X11/xorg.conf for VirtualBox.

After installing the NVidia drivers I also save the new /etc/X11/xorg.conf.

Then I added the following bit of script into /etc/rc.local :

if lspci | fgrep -qi virtualbox
then
	ln -fs /etc/X11/xorg.conf.virtualbox /etc/X11/xorg.conf
else
	ln -fs /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
fi

This detects whether we're running in VirtualBox before starting X and copies the appropriate xorg.conf :-)

This works nicely when booting into Ubuntu natively. I get the NVidia drivers powering dual moniter with all visual effects enabled :-)

However, when booting into Ubuntu via VirtualBox, I do get the single monitor desktop but the visual effects are no longer enabled and trying to enable them always results in "Desktop effects could not be enabled" in the System, Preferences, Appearance, Visual Effects dialog :-( This is exactly the same problem I had when trying to enable them before when the NVidia drivers were installed... grrr... I thought it might work now because I enabled the visual effects before installing the NVidia drivers. Rats.

So why can't I enable visual effects for the VirtualBox graphics driver while the NVidia graphics drivers are installed? Are there some other files which I need to manipulate in my rc.local script? Please help!

---

### Post by SimonHF on 2010-12-20
So I did a sha1 on every file on the hard disk before and after enabling visual effects for the NVidia drivers. I then did a diff on the two sets of sha1s in order to find out what had changed. Apart from a bunch of log files and sys counters then my money is on a file called .gconfd/saved_state . A bit of Googling shows then this file finds its way into bug reports about Ubuntu's appearance quite often :-) I'm wondering if I give this file the some treatment as xorg.conf then will everything start working?

---

### Post by SimonHF on 2010-12-26
In the end I gave up using VirtualBox. The final straw is that VirtualBox does not support 3D acceleration in Windows 64 bit guests; only Linux 64 bit guests! It was also frustrating that VirtualBox does not support multi-monitor configurations in Linux guests. So I switched back to beloved VMware. VirtualBox may be mature but is lacking a wider range of features. VMware allows me to have multi-monitor support in the guests... which I can't do with VirtualBox. I can also boot the Ubuntu physical partition natively and as a guest. Plus I can boot a Windows 64 bit guest with 3D acceleration. The only thing I can't do is have Compiz acceleration... but then I can't have that is VirtualBox either. So in short, here's the summary:
- Boot Ubuntu physical partition both ways: VMware: yes, VBox: yes
- Multi-monitor support in Linux guests: VMware: yes, VBox: no
- 3D acceleration in 64 bit Windows guests: VMware: yes, VBox: no
- 3D acceleration in 64 bit Linux guests: VMware: no, VBox: no *1
*1 Not if booting the physical partition natively as well as as a guest:-(

Hope this helps somebody...

---

### Post by batistuta on 2011-01-15
your post definitely helped me. 

I'm running Virtualbox and don't care about 3D acceleration or multiple monitors, so everything is fine for my requirements.

Thanks for sharing your findings. You have saved me and I'm sure many others a lot of time.

---

### Post by SimonHF on 2011-01-15
batistuta, I'm glad you found it useful. I also have a small update: VirtualBox also has a slight advantage over VMware if you have a system with 12 cores (which the high end Intel I7 has, as well as some of the Xeons). This configuration of cores is supported by VirtualBox but not by VMware which strangely seems to only support 8 or 16 cores but not 12.

---

### Post by dwhiting on 2011-01-22
I have been doing this for some time, using a slightly modified version of the "deprecated" tutorials linked above. I didn't have to do anything with the X config stuff. It "just worked"! I was able to install Guest Additions (GAs)  in my Ubuntu guest, and they worked great when running inside VirtualBox. When I did a physical boot into the Ubuntu partition, that also worked fine. FWIW, I have attached the modified tutorial, with both thanks and apologies to whoever wrote the original.

Anyway, this method worked fine for me with VirtualBox 3.x (several versions) and Ubuntu 9.10/10.04/10.10, over the past couple of years as I upgraded versions of each.

However, since I installed VB 4.0, this has stopped working in a strange and very annoying way. I can run without GAs and continue to dual boot and run in VBox. However, once I install the GAs, the physical boot stops working. It hangs right after giving error messages:
   [FONT=Courier New]Starting the VirtualBox Guest Additions ... fail!
   (modprobe vboxguest failed)
   Starting VirtualBox Guest Addition service VirtualBox Additions module not loaded![/FONT]

I can then press Ctl-Alt-Del and the Ubuntu boot screen shows up for a few seconds, and then the system reboots.

However, Ubuntu continues to run just fine under VBox! If I delete the GA files, then I can also run under VBox, just without GAs, but physical boot still doesn't work. If I restore the Ubuntu partition from a backup, then I can again physically boot and also run VBox without GAs. So I have to choose between dual boot or using GAs, which is pretty limiting. Somehow, installing the GAs is *completely *breaking physical boot.

There really needs to be better (and *much *more user-friendly) support for this kind of usage. At the very least, the documentation should say more than "it's possible and is left as an exercise for the clever reader", which is effectively what it currently states.

Does anybody have a solution here (other than going back to VBox 3.x)?

---

