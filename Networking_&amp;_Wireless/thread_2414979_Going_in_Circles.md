---
title: "Going in Circles"
date: 2019-03-18
forum: Networking &amp; Wireless
---

### Post by mel-blanc on 2019-03-18
I need to install the drivers for an Alfa AWUS036ach WiFi device on
an 18.04 install of Ubuntu. The internal WiFi device of the box is a
Broadcom product and have been unable to get the Broadcom network
NIC, and WiFi to work. So I opted to install the Alfa WiFi device.

Since I have no network connectivity I downloaded the RTL8812AU
debian package from the Ubuntu repository. Shoeleather expressed 
the file to the 18.04 Ubuntu box on a USB thumb drive. From their
I type:
                           sudo apt install ./rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu8_all.deb

The routine starts and then balks with an error message that 'dkms'
is missing.

Located dkms on the Ububntu repository, download, shoeleather
expressed it to the Ubuntu box. Then typed

                          sudo apt install ./dkms_2.3-3ubuntu11_all.deb

Another fail with an error message that there are dependencies 
which need to be met.

I locate the dependencies, shoeleather express them to the Ubuntu
box, attempt to install only to receive more messages that other 
dependencies need to be met. 

Is there a way to install the Alfa drivers without network connectivity
and not keep chasing my tail trying to solve the seeming never ending
dependencies list?

TIA

Mel

---

### Post by jeremy31 on 2019-03-18
With the wifi plugged in, post results from terminal for ```
lsusb; uname -r
```

---

### Post by mel-blanc on 2019-03-18
foghorn@foghorn-Precision-M4800:/media/foghorn/Kali Live$ lsusb; uname -r


Bus 002 Device 003: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor

Bus 002 Device 002: ID 8087:8000 Intel Corp. 

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 002: ID 8087:8008 Intel Corp. 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 004 Device 007: ID 0951:1666 Kingston Technology DataTraveler G4

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 003 Device 003: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter

Bus 003 Device 002: ID 18d1:4ee7 Google Inc. 

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

4.18.0-10-generic

Thanks for reviewing and the direction.

Mel

---

### Post by jeremy31 on 2019-03-18
Is this Kali or Ubuntu?
Also post results for ```
lspci -nnk | grep -iA3 net
```

---

### Post by mel-blanc on 2019-03-18
foghorn@foghorn-Precision-M4800:/media/foghorn/Kali Live$ lspci -nnk | grep -ia3 net
    

        Subsystem: Dell Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1028:aab0]
    
        Kernel driver in use: snd_hda_intel
    
        Kernel modules: snd_hda_intel

03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    
        Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter [1028:0017]
    
        Kernel driver in use: bcma-pci-bridge
    
        Kernel modules: bcma

11:00.0 SD Host controller [0805]: O2 Micro, Inc. SD/MMC Card Reader Controller [1217:8520] (rev 01)

Again thanks.

---

### Post by jeremy31 on 2019-03-18
Moved to Networking

Boot into the installation ISO and use driver manager to install the broadcom proprietary bcmwl module, then go to /lib/modules/4.18.0-10-generic/kernel/updates/dkms and copy the wl.ko file.  Find your hard drive for the installed 18.04 under devices in file manager and see if you can paste the wl.ko in /home/your username.  Then reboot into the installed and try ```
sudo cp wl.ko /lib/modules/4.18.0-10-generic/kernel/drivers/net/wireless
sudo depmod -a
```

Also check ```
mokutil --sb-state
```
If it says secure boot is enabled, it will need to be disabled when you reboot

---

### Post by mel-blanc on 2019-03-18
OK, progressed to a point.

Booted from ISO on thumb drive.

Did not find a 'driver manager' in the GUI so used a terminal.

First checked the /lib/modules/4.18.0-10-generic/kernel/updates/dkms directory to see if a wl.ko already existed.
The directory existed down to 4.18.0-10-generic/kernel/ but the directory updates did not exist. That seemed positive at
this point.

At the prompt entered  'sudo ubuntu-drivers devices'

The return was:

== /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 ==
modalias : pci:v000014e4000043b1sv00001028sd00000017bc02sc80i00
vendor   : Broadcom Ltd
model     : BCM4352 802.11ac Wireless Network Adaptor
driver     : bcmwl-kernel-source - distro non-free

Then entered:                                 sudo apt install bcm and tabbed the line.
This resulted in the completed line:     sudo apt install bcmwl-kernel-source

The terminal after about 15 seconds exited with no errors reported.

Then entered:         cd /lib/modules/4.18.0-10-generic/kernel/updates/dkms/       at the prompt
to go to the directory and verify the file wl.ko had been created. To my changrin
this returned an error message there was no such directory or file. That seemed
quite odd as the command:    sudo apt install bcmwl-kernel-source   ran and exited 
with no error. The command also exited with the message it was installing to:

   /lib/modules/4.18.0-10-generic/updates/dkms

Went back and rechecked the command   that was used to cd into the 
directory was entered correctly. It matched what you specified and what
appeared when the command    sudo apt install bcmwl-kernel-source 
produced upon exit. Single stepping down the directory tree I reached
kernel but 'updates' was not present.

Knowing that the file had been produced and the command ran without
reporting an error I then ran:

sudo find -iname wl.ko         from the root directory.

This returned there were two places where the file wl.ko existed. They are 
displayed below:[INDENT]
./lib/modules/4.18.0-10-generic/updates/dkms/wl.ko
[/INDENT]
and[INDENT]./var/lib/dkms/bcmwl/6.30.233.271+bdcom/4.18.0-10generic/x86_64/module/wl.ko
[/INDENT]

I am a bit confused why the '.' is prepended to the search results. In any event I 
tried to cd into the ./lib/modules/4.18.0-10-generic/updates/dkms/ directory
and produced an error the directory did not exist. WTH. I also tried again to
cd to /lib/modules/4.18.0-10-generic/updates/dkms/   but no joy.

Finally I copied and pasted the  /lib/modules/4.18.0-10-generic/updates/dkms/
text on the screen which produced an error earlier when typed in and suddenly
the directory appears.

I thought I was going nucking futz and repeated the same procedure again and
duplicated the exact same result. I can run the command to produce the wl.ko
file and manually type in the path to reach it but an error is returned. Then I copy 
and paste the path and suddenly the path is there with the file in the directory.
After that I can exit the directory, go back and type in the original path
manually, and suddenly it goes to the directory without the error. 

Whatever. In any event I mounted the hard disk which was listed as sda1
and copied the wl.ko to my /home/foghorn/ directory. At that point I 
execute a 'shutdown -r restart' and after the prompt to remove the
thumb drive the system reboots. I move the wl.ko file to the directory 

-                       /lib/modules/4.18.0-10-generic/kernel/drivers/net/wireless/
from my /home/foghorn directory. Then  I cd into the /home/foghron directory 
to verify the presence of the file.

I still have no wireless devices that are active.

I have been into the bios and verified WiFi is allowed to run. Also I have verified the
hardware switch on the side of the computer which turns the WiFi and bluetooth devices
on and off is 'ON'.


Short of sticking a stick of dynamite under this box are there any suggestions of 
which way to go?

Thanks

---

### Post by jeremy31 on 2019-03-18
Do a ```
sudo modprobe -v wl
```
See if any errors show

---

### Post by mel-blanc on 2019-03-18
None returned for 'wl'

---

### Post by jeremy31 on 2019-03-18
If no errors, check ```
rfkill list; iwconfig
```

Might want to check ```
iwlist scan
```
See if wifi can find anything

---

### Post by mel-blanc on 2019-03-18
rfkill list reports:

1: dell-wifi: Wireless LAN
                 Soft Blocked: no
                 Hard Blocked: no

2: dell-bluetooth: Bluetooth
                 Soft Blocked: no
                 Hard Blocked: no

3: hci0: Bluetooth
                 Soft Blocked: no
                 Hard Blocked: no


iwconfig
     lo    no wireless extensions

Booting from the Hard Disk produces the info displayed above. Bluetooth
which also did not work is now working. ?

Now for the wierd part
The ISO on the thumb drive when booted  sees the wireless Dell device and activates it.
Running the ISO I can connect to the internet and surf.

---

### Post by jeremy31 on 2019-03-18
If you are on ISO, post results for ```
sudo parted -l
```

---

### Post by mel-blanc on 2019-03-18
sudo parted -l

Model:  ATA ST500LX025-1U717 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start        End        Size       Type      File system    Flags
   1       1049kb      500GB    500GB     Primary  ext4             boot


Warning:  The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel?

---

### Post by mel-blanc on 2019-03-18
I chose ignore

Model: Sandisk Ultra (scsi)
Disk /dev/sdb: 123GB
Sector size (logical/physical):  2048B/512B
Partition table:  mac
Disk Flags:

Number-----Start-----End-----Size_-----File system-----Name-----Flags
1 _________2048B____6143B__4096B_________________Apple
2 ________1960MB___1963MB_2523kb________________EFI

---

### Post by mel-blanc on 2019-03-18
If I select Cancel then

Model: SanDisk Ultra (scsi)
Disk /dev/sdb  30.8 GB
Sector size (logical/physical): 512B/512B
Partition table: unknown
Disk Flags:

---

### Post by jeremy31 on 2019-03-18
Lets try
```
sudo mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/proc
mount --bind /run /mnt/run
sudo chroot /mnt
apt update
apt install bcmwl-kernel-source
exit
```

If there were no errors, you should be able to boot into the install and have working wifi

---

### Post by mel-blanc on 2019-03-19
Thank you for your patience in making this work. Unfortunately I
am still hitting a wall.

The lines listed below run with no errors returned other than the 
commands beginning with 'mount',  squawk if I do not use 'sudo' 
at the beginning:

sudo mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/proc
mount --bind /run /mnt/run
sudo chroot /mnt

Then when I run the line: apt update the below is returned:


root@ubuntu:/# apt update

Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) cosmic InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) cosmic-updates InRelease 
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) cosmic-backports InRelease  
  Temporary failure resolving 'us.archive.ubuntu.com'

Reading package lists... Done
Building dependency tree       
Reading state information... Done

All packages are up to date.
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/cosmic/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/cosmic/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/cosmic-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/cosmic-updates/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/cosmic-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/cosmic-backports/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/cosmic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/cosmic-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.


After looking at the output I went back and prepended the command with sudo

The results were different. I am cluelessas to which is the proper way to
run the command. The results appear below:

root@ubuntu:/# sudo apt update


sudo: unable to resolve host ubuntu: Resource temporarily unavailable

Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) cosmic InRelease  
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease  
  Temporary failure resolving 'security.ubuntu.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) cosmic-updates InRelease  
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) cosmic-backports InRelease  
  Temporary failure resolving 'us.archive.ubuntu.com'

Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/cosmic/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/cosmic/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/cosmic-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/cosmic-updates/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/cosmic-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/cosmic-backports/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/cosmic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/cosmic-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.



rfkill indicates all are unblocked

---

### Post by mel-blanc on 2019-03-19
Bad went to worse about 30 minutes ago. Walked in and the
screen was just a morass of color blocks. I was unable to
recover and powered down the box. Upon reboot the error
message No Boot Sector Found appeared. <sigh>

Grabbed a virgin copy of the ISO and flashed it to a thumb
drive using DD. Then walked it over to the box and installed
a fresh copy of 18.04.

Once the install had booted I checked to see if 'wl.ko'
appeared at any place and 'find -iname wl.ko' was unable
to locate such a named file from the root directory.

Also went directly to:   
/lib/modules/4.18.0-10-generic/kernel/drivers/net/wireless

and verified it was not there.


I performed a 'shutdown -h now' and exited, then rebooted
with the thumb drive used as the boot device.

At that point I ran:

  ubuntu-drivers devices

which returned the string:    driver     : bcmwl-kernel-source - distro non-free

I then ran sudo apt install

Did a search for the 'wl.ko' file and moved it to my home
directory /home/foghorn/ after mounting the hard disk.

Once done there I rebooted and from my home directory I
moved the wl.ko file to the:

/lib/modules/4.18.0-10-generic/kernel/drivers/net/wireless

Then ran: sudo depmod -a

That ran and exited without error.

Shutdown the system again and restarted using the hard disk
install.

Run:   sudo modprobe -v wl      which momentarily thinks
about it and returns to a new prompt with no output.

'rfkill list' displays two devices, Dell Wifi and Dell Bluetooth.
Both have soft and hard blocks listed as "no"

iwconfig simply returns:     lo   No wireless extensions

---

### Post by jeremy31 on 2019-03-19
Download [https://www.dropbox.com/s/iy7m54y3e5q6h2z/rtl8812au.ko?dl=0](https://www.dropbox.com/s/iy7m54y3e5q6h2z/rtl8812au.ko?dl=0)
And put that on a SDIO card, USB drive, boot into your installed 18.10 and copy it to /lib/modules/4.18.0-10-generic/kernel/drivers/net/wireless, then do a sudo depmod -a and then reboot into the install and see if the USB card will work

---

### Post by mel-blanc on 2019-03-19
Downloaded the link.
It appeared as:    rtl8812au.ko
Transferred to thumb drive.
Moved to box with hard disk install of 18.04 booted. 
Copied rtl8812au.ko to /lib/modules/4.18.0-10-generic/kernel/drivers/net/wireless/
Ran depmod -a as root
No error messages
Ran shutdown -h now.
Booted machine with Alfa AWUS036ACH plugged into USB

iwconfig reports     lo              no wireless extensions

rfkill lists only Dell WiFi and Bluetooth

lsusb reports   Bus 003 Device 003:  ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter

No Joy  :-(

If I had a weapon I would shoot the box.

---

### Post by jeremy31 on 2019-03-19
What does ```
lsmod | grep cfg
```
Show

Also see the wireless script link in my signature, there is some instructions on how to use it offline by downloading the file and copying it to the offline OS

---

### Post by mel-blanc on 2019-03-19
This is getting more bizarre. I have a Netgear Class One dongle (USBBT100) which I 
can plug into a USB port and it immediately starts to work. Same thing with a no
name USB dongle using the Cambridge Silicon Radio chip. Wierd!

---

### Post by mel-blanc on 2019-03-19
lsmod | grep cfg 

reports

cfg80211                663552               3  wl,b43,mac80211

---

### Post by jeremy31 on 2019-03-19
I forgot about the blacklist
```

echo "blacklist b43" | sudo tee /etc/modprobe.d/blacklist-bcm.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-bcm.conf
```
Reboot

---

### Post by mel-blanc on 2019-03-19
Ran:

echo "blacklist b43" | sudo tee /etc/modprobe.d/blacklist-bcm.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-bcm.conf

Rebooted - No Joy

Ran wireless-info.txt and the return is listed below:

Here is the link to Paste Bin        [https://pastebin.ubuntu.com/p/fzdcnvwj3Z/](https://pastebin.ubuntu.com/p/fzdcnvwj3Z/)

---

### Post by jeremy31 on 2019-03-19
The blacklist didn't update from what I see in the script results
try ```
gedit admin:///etc/modprobe.d/blacklist-bcm43.conf
```
Add the following
```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
```
Plus do
```
sudo sed -i 's/WirelessEnabled=false/WirelessEnabled=true/' /var/lib/NetworkManager/NetworkManager.state
```

Reboot and check ```
rfkill list
```
As when the script was run the wifi was soft blocked

---

### Post by mel-blanc on 2019-03-19
blacklist-bcm43.conf file does not exist. There is a blacklist-bcm.conf file.
Do I need to create a specific blacklist-bcm43.conf file or should I edit the
blacklist-bcm.conf file to include the blacklisted items from above.

---

### Post by jeremy31 on 2019-03-19
Just edit the existing one to include the list

---

### Post by mel-blanc on 2019-03-19
Ok, done.

rebooted


rfkill list is now showing the wlan is soft blocked.

It is also listed as device # 1

Entered rfkill unblock 1 and now shows it is unblocked.

iwconfig is still showing no wireless extensions

---

### Post by jeremy31 on 2019-03-19
On the computer, run ```
./wireless-info
```
Copy the new wireless-info.txt and post it.

Or you could try inserting the USB with the Ubuntu ISO, go into driver manager and see if you can install the broadcom proprietary from there

---

### Post by mel-blanc on 2019-03-20
Morning Jeremy

Read your message this morning and decided to repeat the procedure of loading
the Broadcom drivers. Booted from the flash drive and then ran:

***sudo ubuntu-drivers devices***

The bcmwl driver appeared in the list so entered the following in terminal

***sudo apt install bcmwl-kernel-source***

This completed and returned no error messages.

Looking around immediately afterwards I clicked on the down triangle int he upper
right of the GUI. Behold there was a selection for wireless. Clicking on it I was
presented with a list of Access Points in the area. Wahoo! Selected mine and
it connected. Opened a browser and surfed to Google, then a couple of news
outlets.

Then in a terminal window I entered ***shutdown -r now***. The system prompted me
to remove the flash drive and it continued the shutdown, then started the reboot.

On reboot I went back to the down triangle in the upper right of the GUI but this
time there was no selection for Wireless. In a terminal I entered **rfkill list** and it
displayed the presence of the Broadcom Wireless card but indicated it was softblocked.

Entered ***rfkill unblock 1*** (where 1 is the id of the device in rfkill list) and rechecked 
the status of devices in the list. This time softblock was listed as no. Rechecked
the down triangle and still no indication of a wireless selection.

Ran ***wireless-info.txt*** again and the results are posted at: [https://pastebin.ubuntu.com/p/tqFtXrPNzT/](https://pastebin.ubuntu.com/p/tqFtXrPNzT/)


When I run the device driver installation from the flash driver am I somehow 
installing the drivers to the flash drive instead of the hard disk installation?
I am pretty ignorant relative to Linux and processes so please forgive me if 
my question comes across as unwarranted.

---

### Post by jeremy31 on 2019-03-20
On the version installed on the hard drive, in terminal do
```
sudo sed -i 's/WirelessEnabled=false/WirelessEnabled=true/' /var/lib/NetworkManager/NetworkManager.state
sudo depmod -a
```
Reboot

When you boot using the flash drive, you install only in RAM and it is gone when you reboot unless you do something like using chroot to change into the install but we tried that

I thought at one time that booting to the hard drive, then putting the USB in allowed someone to install using driver manager as all the files needed to install the driver are on the USB somewhere in the /pool directory

---

### Post by mel-blanc on 2019-03-20
> **jeremy31 said:**
> 
When you boot using the flash drive, you install only in RAM and it is gone when you reboot unless you do something like using chroot to change into the install but we tried that

I thought at one time that booting to the hard drive, then putting the USB in allowed someone to install using driver manager as all the files needed to install the driver are on the USB somewhere in the /pool directory

I need to perform a sanity check at my end here.


[LIST]
[*]To install the drivers as discussed do I need 
to boot into the flash drive or the installation 
on the hard disk? 
[*]When I boot to the flash (thumb) drive,  I run
***ubuntu-drivers devices.*** Then the [I][B]
bcmwl**-**kernel-source[/B][/I] 
driver is listed. I then have been running: 
***sudo apt install*** [I][B]bcmwl-kernel-source

[/B][/I]That is the corner case which when completed 
that wireless connectivity is achieved. But I am 
wondering if the procedure is installing to RAM 
disk as opposed to the hard disk installation? 
[*]Do I need to boot to the hard disk and install the
drivers from the flash drive? If so how is that done?
The reason I ask is when I boot to the disk, then
insert the flash with the 18.04 ISO, and run
***ubuntu-drivers devices*** the [I][B]bcmwl-kernel-source
[/B][/I]is not listed.
[*]Alternatively, once the wireless is working once 
the Broadcom driver is installed when booting 
from the flash drive, is there a way to copy the 
ram disk install and save it as a bootable ISO? 
[/LIST]
Thanks

Mel

---

### Post by jeremy31 on 2019-03-20
I would burn the ISO to DVD boot into the hard drive install, insert DVD go into Software & Updates, enable the cdrom, then see if it can be installed in additional drivers

---

### Post by mel-blanc on 2019-03-21
Jeremy

Trudge back through the installation for the umpteenth time and made notes
of each step of the installation procedure for post install review and comparison
of observed behaviors vs installation steps and switches.

During the installation there is a step where you select the type of install.
Below the selection of the type of install is an optional selection for installation
of drivers which Ubuntu determines is needed. 

Long story short I selected the normal install and did not check the option for
the 'OPTIONAL' driver installation. After setting the switch to install drivers and 
rebooting, the system came up with an active wireless device using the 
bcmwl-kernel-souce.

I appreciate all your effort and apologize for spinning your wheels for my 
assertion of a short between my headsets.

Regards

Mel

---

### Post by jeremy31 on 2019-03-21
Ah, third party drivers and software
I have never installed Ubuntu on a laptop with a Broadcom card before, the one actually had an Intel card that I swapped with a Broadcom to do some Bluetooth testing with

---

