---
title: "New ubuntu 18.04 installation - wireless dongle issue"
date: 2019-05-19
forum: Networking &amp; Wireless
---

### Post by riggster on 2019-05-19
This is my first experience with Linux. I used DBAN to wipe the hard drive on a computer and installed Ubuntu 18.04 from a USB bootable drive. The installation seemed to work fine, but in the wireless settings, it says "no wifi adapter found". I have done some reading online and this is the information I have:

I only have the usb wifi dongle, no other way to connect the computer to the internet. The computer does have a ethernet port, but I only have access to the internet via wifi.

The first time I installed the OS, I forgot to check the button that says to install third party software for wifi devices, or something to that effect. I re-installed, and made sure to check that box, and that did not change anything.

When I open a terminal and type ```
lsusb
```, I get the following line that relates to my dongle. I know this is the correct line, because it does not show up when I remove the dongle and run lsusb again.

Bus 002 Device 005: ID 0bda:c811 Realtek Semiconductor Corp.

when I type ```
sudo lshw -C network
```, the only network device that is listed has the following information:

description: Ethernet interface
product: 82579LM Gigabit Network Connection
vendor: Intel Corporation
bus info: pci@0000:00:19.0

can someone help me figure this out? Thanks a ton!

Riggster

---

### Post by wildmanne39 on 2019-05-19
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by chili555 on 2019-05-19
> I only have the usb wifi dongle, no other way to connect the computer to the internet. Can you tether your phone?

Do you still have the original installation disk? If you can't tether, many of the packages we'll need to compile a driver are on it.

---

### Post by riggster on 2019-05-19
I can't tether my phone, and I don't have the original disk. I do have access to the internet through my windows laptop though, or if I need to I will find a way to get it hard wired.

---

### Post by riggster on 2019-05-19
Internet connectivity solved. I bought a cat5 cable and am set up in my storage room plugged into the back of my router.

---

### Post by jeremy31 on 2019-05-19
See [https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)
You will need to have Secure Boot disabled if you have an UEFI install

---

### Post by chili555 on 2019-05-19
Here is the exact procedure: [https://askubuntu.com/questions/1089790/usb-wifi-realtek-not-an-mtp-device/1090069#1090069](https://askubuntu.com/questions/1089790/usb-wifi-realtek-not-an-mtp-device/1090069#1090069)

You will probably also need to install a few prerequisites:```
sudo apt-get install git dkms build-essential linux-headers-generic 
```Post back if you get stuck or need additional guidance.

Thanks, Jeremy.

---

### Post by riggster on 2019-05-19
I ran the command:
```
sudo mokutil --disable-validation
```

and got the following output: This system doesn't support Secure Boot

So, It looks like I don't need to disable Secure Boot.

When I execute 
```
sudo apt-get install dkms
```


I was asked to insert a disc into my cd-rom labeled 
'Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)'.
I don't have this disc. Do you have any suggestions? I have included the entire output of the command below.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-7 gcc gcc-7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan4 libatomic1
  libc-dev-bin libc6-dev libcilkrts5 libfakeroot libgcc-7-dev libitm1 liblsan0
  libmpx2 libquadmath0 libstdc++-7-dev libtsan0 libubsan0 linux-libc-dev make
  manpages-dev
Suggested packages:
  menu debian-keyring g++-multilib g++-7-multilib gcc-7-doc libstdc++6-7-dbg
  gcc-multilib autoconf automake libtool flex bison gcc-doc gcc-7-multilib
  gcc-7-locales libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg
  libasan4-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg
  libmpx2-dbg libquadmath0-dbg glibc-doc libstdc++-7-doc make-doc
The following NEW packages will be installed:
  build-essential dkms dpkg-dev fakeroot g++ g++-7 gcc gcc-7
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan4 libatomic1 libc-dev-bin libc6-dev libcilkrts5 libfakeroot
  libgcc-7-dev libitm1 liblsan0 libmpx2 libquadmath0 libstdc++-7-dev libtsan0
  libubsan0 linux-libc-dev make manpages-dev
0 upgraded, 28 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/26.9 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Media change: please insert the disc labeled
 'Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)'
in the drive '/cdrom/' and press [Enter]



Also, I tried to go ahead and clone the github repo, but I didn't have git installed. When I execute ```
sudo apt install git

```, the command failed because of an uninstallable dependency (liberror-perl). See the output below:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 git : Depends: liberror-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

Any suggestions on this problem?

---

### Post by chili555 on 2019-05-19
Please open Software and Updates and then disable the CDROM. Be certin that main, universe, restricted and multiverse are enabled. You should be prompted to update the package index; do so. Next, open the terminal and run: ```
sudo apt-get update
sudo apt-get install git dkms build-essential linux-headers-generic
```Then proceed with installing the actual driver.

---

### Post by riggster on 2019-05-19
I was able to work through all the steps, but in the wifi settings it still says a wifi adapter isn't being detected. Rebooting didn't help either.

---

### Post by chili555 on 2019-05-19
What is the exact response to the terminal commands:```
modinfo 8821cu | grep C811
sudo modprobe 8821cu && dmesg | grep 8821
```

---

### Post by riggster on 2019-05-19
ryan@LinuxBox1:~$ modinfo 8821cu | grep C811
alias:          usb:v0BDApC811d*dc*dsc*dp*icFFiscFFipFFin*
ryan@LinuxBox1:~$ sudo modprobe 8821cu && dmesg | grep 8821
[sudo] password for ryan: 
[ 9211.745460] 8821cu: loading out-of-tree module taints kernel.
[ 9211.745926] 8821cu: module verification failed: signature and/or required key missing - tainting kernel
[ 9211.749680] usbcore: registered new interface driver rtl8821cu

---

### Post by chili555 on 2019-05-20
The driver loads without complaint and is verified to cover your device. Did you try a reboot? Did you try removing and reinserting the device? It ought to take off like a rocket!

Please run:```
tail -f /var/log/syslog
```Remove and reinsert the device. Note and post the resultant text. 

Get out of 'tail' with Ctrl+c.

---

### Post by riggster on 2019-05-20
rebooting didn't help. unplugging and plugging didn't help. Here is the output from that tail command you gave me. 

ryan@LinuxBox1:~$ tail -f /var/log/syslog
May 20 17:17:01 LinuxBox1 CRON[7161]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 20 17:46:01 LinuxBox1 gnome-software[2653]: no app for changed [email]ubuntu-dock@ubuntu.com[/email]
May 20 17:46:01 LinuxBox1 gnome-software[2653]: no app for changed [email]ubuntu-appindicators@ubuntu.com[/email]
May 20 17:46:01 LinuxBox1 gvfsd-metadata[3282]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
May 20 17:46:01 LinuxBox1 gvfsd-metadata[3282]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
May 20 17:46:01 LinuxBox1 gnome-shell[1867]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.78/org/ayatana/NotificationItem/software_update_available
May 20 17:46:01 LinuxBox1 kernel: [84071.154836] ISO 9660 Extensions: Microsoft Joliet Level 3
May 20 17:46:01 LinuxBox1 kernel: [84071.156566] ISOFS: changing to secondary root
May 20 17:46:01 LinuxBox1 systemd[1]: Started Clean the /media/ryan/Realtek1 mount point.
May 20 17:46:01 LinuxBox1 udisksd[855]: Mounted /dev/sr1 at /media/ryan/Realtek1 on behalf of uid 1000
May 20 17:49:33 LinuxBox1 kernel: [84283.157067] usb 2-1.8: USB disconnect, device number 7
May 20 17:49:33 LinuxBox1 systemd[1]: Unmounting /media/ryan/Realtek1...
May 20 17:49:33 LinuxBox1 udisksd[855]: Cleaning up mount point /media/ryan/Realtek1 (device 11:1 no longer exists)
May 20 17:49:33 LinuxBox1 udisksd[855]: Error cleaning up mount point /media/ryan/Realtek1: Error unmounting: Command-line `umount -l "/media/ryan/Realtek1"' exited with non-zero exit status 32: umount: /media/ryan/Realtek1: not mounted.
May 20 17:49:33 LinuxBox1 udisksd[855]: Cleaning up mount point /media/ryan/Realtek1 (device 11:1 no longer exists)
May 20 17:49:33 LinuxBox1 systemd[1]: Unmounted /media/ryan/Realtek1.
May 20 17:49:33 LinuxBox1 systemd[1]: Stopping Clean the /media/ryan/Realtek1 mount point...
May 20 17:49:33 LinuxBox1 systemd[1]: Stopped Clean the /media/ryan/Realtek1 mount point.
May 20 17:49:33 LinuxBox1 upowerd[1096]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0
May 20 17:49:33 LinuxBox1 upowerd[1096]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8
May 20 17:50:14 LinuxBox1 kernel: [84323.828206] usb 2-1.8: new high-speed USB device number 8 using ehci-pci
May 20 17:50:14 LinuxBox1 kernel: [84323.937046] usb 2-1.8: New USB device found, idVendor=0bda, idProduct=1a2b, bcdDevice= 2.00
May 20 17:50:14 LinuxBox1 kernel: [84323.937050] usb 2-1.8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 20 17:50:14 LinuxBox1 kernel: [84323.937053] usb 2-1.8: Product: DISK
May 20 17:50:14 LinuxBox1 kernel: [84323.937055] usb 2-1.8: Manufacturer: Realtek
May 20 17:50:14 LinuxBox1 kernel: [84323.937425] usb-storage 2-1.8:1.0: USB Mass Storage device detected
May 20 17:50:14 LinuxBox1 kernel: [84323.938722] scsi host7: usb-storage 2-1.8:1.0
May 20 17:50:14 LinuxBox1 mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8"
May 20 17:50:14 LinuxBox1 mtp-probe: bus: 2, device: 8 was not an MTP device
May 20 17:50:14 LinuxBox1 upowerd[1096]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0
May 20 17:50:14 LinuxBox1 upowerd[1096]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8
May 20 17:50:15 LinuxBox1 kernel: [84324.943099] scsi 7:0:0:0: CD-ROM            Realtek  Driver Storage   1.00 PQ: 0 ANSI: 0 CCS
May 20 17:50:15 LinuxBox1 kernel: [84324.949290] sr 7:0:0:0: [sr1] scsi3-mmc drive: 0x/0x caddy
May 20 17:50:15 LinuxBox1 kernel: [84324.949477] sr 7:0:0:0: Attached scsi CD-ROM sr1
May 20 17:50:15 LinuxBox1 kernel: [84324.949570] sr 7:0:0:0: Attached scsi generic sg3 type 5
May 20 17:50:15 LinuxBox1 systemd[1]: media-ryan-Realtek.mount: Failed to run 'mount' task: No such file or directory
May 20 17:50:15 LinuxBox1 systemd[1]: media-ryan-Realtek.mount: Failed with result 'resources'.
May 20 17:50:15 LinuxBox1 systemd[1]: Failed to mount /media/ryan/Realtek.
May 20 17:50:16 LinuxBox1 kernel: [84325.349134] ISO 9660 Extensions: Microsoft Joliet Level 3
May 20 17:50:16 LinuxBox1 kernel: [84325.350888] ISOFS: changing to secondary root
May 20 17:50:16 LinuxBox1 systemd[1]: Started Clean the /media/ryan/Realtek1 mount point.
May 20 17:50:16 LinuxBox1 udisksd[855]: Mounted /dev/sr1 at /media/ryan/Realtek1 on behalf of uid 1000

---

### Post by chili555 on 2019-05-21
All we see above is a USB key being removed and reinserted; not a USB wireless device. It identifies as:> 
New USB device found, idVendor=[COLOR="#FF0000"]0bda[/COLOR], idProduct=[COLOR="#FF0000"]1a2b[/COLOR], bcdDevice= 2.00
As you said above, your wireless is:  ID 0bda:c811 Realtek Semiconductor Corp.

Just to experiment, with the device inserted, do: ```
sudo usb_modeswitch -KW -v 0bda -p 1a2b
```What is the result?

---

### Post by riggster on 2019-05-21
Here is the output of the last command you gave me. However, I think I steered you wrong before. I was going back and forth between different forums and my terminal and gave you the wrong wireless id. When I run lsusb, I get the following for my wifi dongle:

Bus 002 Device 010: ID 0bda:1a2b Realtek Semiconductor Corp.


ryan@LinuxBox1:~/Downloads/rtl8821CU$ sudo usb_modeswitch -KW -v 0bda -p 1a2b
Take all parameters from the command line


 * usb_modeswitch: handle USB devices with multiple modes
 * Version 2.5.2 (C) Josua Dietze 2017
 * Based on libusb1/libusbx

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x0bda
DefaultProduct= 0x1a2b

StandardEject=1

Look for default devices ...
  found USB ID 0bda:1a2b
   vendor ID matched
   product ID matched
  found USB ID 0781:5567
  found USB ID 046d:c00e
  found USB ID 8087:0024
  found USB ID 1d6b:0002
  found USB ID 8087:0024
  found USB ID 1d6b:0002
 Found devices in default mode (1)
Access device 010 on bus 002
Get the current device configuration ...
Current configuration number is 1
Use interface number 0
 with class 8
Use endpoints 0x0b (out) and 0x8a (in)

USB description data (for identification)
-------------------------
Manufacturer: Realtek
     Product: DISK
  Serial No.: not provided
-------------------------
Sending standard EJECT sequence
Looking for active drivers ...
 OK, driver detached
Set up interface 0
Use endpoint 0x0b for message sending ...
Trying to send message 1 to endpoint 0x0b ...
 OK, message successfully sent
Read the response to message 1 (CSW) ...
 Response successfully read (13 bytes), status 1
Trying to send message 2 to endpoint 0x0b ...
 OK, message successfully sent
Read the response to message 2 (CSW) ...
 Response successfully read (13 bytes), status 0
Trying to send message 3 to endpoint 0x0b ...
 Sending the message returned error -1. Try to continue
Read the response to message 3 (CSW) ...
 Response reading failed (error -1)
 Device is gone, skip any further commands
-> Run lsusb to note any changes. Bye!

---

### Post by chili555 on 2019-05-22
> -> Run lsusb to note any changes. Bye!Please do and post the result. What is the new usb.id? I suspect it is not 0bda:c811 Realtek Semiconductor Corp.

I also suspect that the driver you built is incorrect.

---

