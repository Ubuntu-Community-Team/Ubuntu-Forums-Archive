---
title: "wifi connection"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by derekf2 on 2013-11-06
Hello forum,

 I  have downloaded Ubuntu 12.04 LTS and can not get my internet to connect. I have been reading a few threads on how to set it up, but i have no idea what i`m doing.

Also i have to change hard drives on my laptop to be able to download or read stuff, then swap hard drives again. It is a pain but hope to get Ubuntu connected.

My laptop uses the Broadcom Corporation BCM4321 802.11a /b/g/n ( rev 03 ). Any help much appreciated.

---

### Post by varunendra on 2013-11-06
Hello derekf2, Welcome to the forums!

Do you have a wired connection available on Ubuntu? That would make things much easier. While connected to internet via cable (or modem etc.), run the following command in a terminal (can be opened with Ctrl-Alt-T) -
```
sudo apt-get install bcmwl-kernel-source
```

However, if you don't have any way to connect to internet, try this command -
```
apt-get install --print-uris bcmwl-kernel-source
```
This will print the download URIs of required packages at the bottom of the output instead of downloading and installing them itself. Copy these URIs to a text file and use them to manually download the packages.

Copy back all the downloaded packages into a new, empty directory on your desktop (let's name this directory "bcmwl"). Then open the termianl again, and run this command to manually install them -
```
sudo dpkg -i Desktop/bcmwl/*
```
If there are any errors during the process, post back and we may proceed accordingly.

---

### Post by derekf2 on 2013-11-06
varunendra, Thanks for the reply.

No i don`t have a wired connection available on Ubuntu, so i gotta do it the hard way swapping hard drives, but all good.

 In terminal i typed this:
> 
apt-get install --print-uris bcmwl-kernel-source

And this comes up:

> Reading package lists... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by varunendra on 2013-11-07
> **derekf2 said:**
> 
 In terminal i typed this:
```
apt-get install --print-uris bcmwl-kernel-source
```
And this comes up:
```
Reading package lists... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Ugh, this is not good. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

Along with the script, please also post back the output of -
```
dpkg -l | grep bcmwl
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by derekf2 on 2013-11-09
varunenda, i downloaded and run your script as the instrucions said, but when i double click the file and select run and enter my password, it starts to load but it crashes / vanishes.

**```
 **dpkg -l | grep bcmwl

ii bcmwl-kernel-source      6.20.155.1+bdcom-0ubuntu0.0.1
           Broadcom 802.11 Linux STA wireless driver source **
```**

---

### Post by varunendra on 2013-11-09
> **derekf2 said:**
> varunenda, i downloaded and run your script as the instrucions said, but when i double click the file and select run and enter my password, it starts to load but it crashes / vanishes.
After supplying the password, it won't appear to do anything. Just a new file "wireless-info.txt" (or "wireless-info.txt.tar.gz") should be created in the same directory where you placed the script itself.

If it doesn't happen, try running it from terminal. Assuming you have placed the script on your desktop -
```
cd Desktop
./wireless_script
```
(some browsers rename it to "wireless_script.txt" while downloading, if so, also add ".txt in the name - "./wireless_script.txt")
You should get a confirmation message stating that a file was created.

By the way -
```
ii bcmwl-kernel-source      **[COLOR="#FF0000"]6.20.155.1[/COLOR]+bdcom-0ubuntu0.0.1**
```
..is definitely not the latest version. But whether you may try the latest one successfully or not may be dependent on the kernel you are using. The script report is not necessary at this point, but may be helpful later. Try it again, and if having problems, just post back these outputs -
```
uname -mr
lsmod
dmesg | egrep 'eth1|wl'
```

---

### Post by derekf2 on 2013-11-09
wireless_script.txt
```
 derek@derek-Latitude-D531:~/Desktop$ ./wireless_script.txt 
[sudo] password for derek: 

Results saved in "wireless-info.txt". 
```

uname -mr 
```
 3.8.0-29-generic i686 

```

 lsmod 
```
 Module                  Size  Used by 
nls_iso8859_1          12617  1 
usb_storage            48053  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm 
parport_pc             27612  0 
ppdev                  12849  0 
joydev                 17329  0 
snd_hda_codec_idt      64649  1 
snd_hda_intel          38819  3 
snd_hda_codec         118613  2 snd_hda_codec_idt,snd_hda_intel 
kvm_amd                54759  0 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi 
kvm                   384557  1 kvm_amd 
radeon                892298  3 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              28931  2 snd_pcm,snd_seq 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq 
dell_wmi               12601  0 
dell_laptop            17209  0 
snd                    57014  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
sparse_keymap          13658  1 dell_wmi 
wmi                    18744  1 dell_wmi 
ttm                    72088  1 radeon 
pcmcia                 39854  0 
mac_hid                13077  0 
drm_kms_helper         47749  1 radeon 
drm                   233935  5 radeon,ttm,drm_kms_helper 
dcdbas                 14065  1 dell_laptop 
soundcore              12600  1 snd 
i2c_algo_bit           13316  1 radeon 
psmouse                82769  0 
sp5100_tco             13558  0 
serio_raw              13031  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm 
video                  19116  0 
k8temp                 12912  0 
ati_agp                13242  0 
shpchp                 32265  0 
yenta_socket           27427  0 
pcmcia_rsrc            18367  1 yenta_socket 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc 
i2c_piix4              13227  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp 
pata_acpi              12886  0 
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci 
crc_itu_t              12627  1 firewire_core 
pata_atiixp            13058  0 
ahci                   25631  2 
libahci                26336  1 ahci 

```

dmesg | egrep `eth1|wl`
```
 wl: command not found 
eth1: command not found 
Usage: egrep [OPTION]... PATTERN [FILE]... 
Try `egrep --help' for more information 

```


wireless-info.txt
```
 *************** info trace *************** 

***** uname -a ***** 

Linux derek-Latitude-D531 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 athlon i386 GNU/Linux 

***** lsb_release ***** 

Distributor ID:    Ubuntu 
Description:    Ubuntu 12.04.3 LTS 
Release:    12.04 
Codename:    precise 

***** lspci ***** 

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03) 
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a] 
    Kernel modules: ssb 

***** lsusb ***** 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

***** PCMCIA Card Info ***** 

PRODID_1="" 
PRODID_2="" 
PRODID_3="" 
PRODID_4="" 
MANFID=0000,0000 
FUNCID=255 

***** iwconfig ***** 


***** rfkill ***** 


***** lsmod ***** 


***** nm-tool ***** 

NetworkManager Tool 

State: disconnected 


***** NetworkManager.state ***** 

[main] 
NetworkingEnabled=true 
WirelessEnabled=true 
WWANEnabled=true 
WimaxEnabled=true 

***** NetworkManager.conf ***** 

[main] 
plugins=ifupdown,keyfile 
dns=dnsmasq 

[ifupdown] 
managed=false 

***** interfaces ***** 

auto lo 
iface lo inet loopback 


***** iwlist ***** 


***** resolv.conf ***** 


***** blacklist ***** 

[/etc/modprobe.d/blacklist-ath_pci.conf] 
blacklist ath_pci 

[/etc/modprobe.d/blacklist-bcm43.conf] 
blacklist b43 
blacklist b43legacy 
blacklist ssb 
blacklist bcm43xx 
blacklist brcm80211 
blacklist brcmfmac 
blacklist brcmsmac 
blacklist bcma 

[/etc/modprobe.d/blacklist.conf] 
blacklist evbug 
blacklist usbmouse 
blacklist usbkbd 
blacklist eepro100 
blacklist de4x5 
blacklist eth1394 
blacklist snd_intel8x0m 
blacklist snd_aw2 
blacklist i2c_i801 
blacklist prism54 
blacklist bcm43xx 
blacklist garmin_gps 
blacklist asus_acpi 
blacklist snd_pcsp 
blacklist pcspkr 
blacklist amd76x_edac 

***** modinfo ***** 


***** udev rules ***** 

***** dmesg ***** 


****************** done ****************** 
```

---

### Post by varunendra on 2013-11-10
The driver is installed but not loaded. Perhaps a failed installation issue.
Please try -
```
sudo modprobe -v wl
```
Does it activate the wifi? Any error messages? Post back the message if there is any.

---

### Post by derekf2 on 2013-11-10
sudo modprobe -v wl

```
 FATAL:Module wl not found. 

```

---

### Post by varunendra on 2013-11-10
> **derekf2 said:**
> sudo modprobe -v wl

```
 FATAL:Module wl not found. 

```

Yep, indeed a failed installation. Please do -
```
sudo apt-get update
sudo apt-get install --reinstall linux-headers-generic build-essential
```

Then check -
```
apt-cache show bcmwl-kernel-source | grep Version
```
If it shows version 6.30.223.141+bdcom-0ubuntu1 in the output lines, then try -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source=6.30.223.141+bdcom-0ubuntu1
```

If that version does not appear in the outputs, try manually downloading it from [here]("http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/"), then install by simply double-clicking on it.

---

### Post by derekf2 on 2013-11-10
I can`t do 
**```
 **sudo apt-get update 
**
```**

I have no internet connection, other than windows.

---

### Post by varunendra on 2013-11-10
Oops ! Sorry, forgot that. Please try the "--pring-uris" trick again -
```
apt-get install --print-uris liunx-headers-generic build-essential
```

It will give you the download URIs of the linux-headers and build-essential packages and their dependencies at the bottom of the output. Use them to manually download the packages on another computer > copy back to an empty folder on the desktop > install with "dpkg -i *" as mentioned previously.

Once these dependencies are installed, purge the previously installed version of the driver-
```
sudo apt-get purge bcmwl-kernel-source
```

Then manually download the actual driver package (version 6.30...._i386.deb) from [here]("http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/"), and install by double-clicking it.

I'm not expecting it to be all smooth, so post back if there are any further problems, or if you need a detailed step-by-step description of the above.

---

### Post by derekf2 on 2013-11-10
print-uris

```
 apt-get install --print-uris linux-headers-generic build-essential 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Package build-essential is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 

E: Unable to locate package linux-headers-generic 
E: Package 'build-essential' has no installation candidate 
```

Can you post a link for the linux-headers-generic ?

---

### Post by varunendra on 2013-11-11
The linux-headers-generic package is actually just a metapackage. It depends and installs the actual header which should be of same version as your kernel. That is easy, but dependencies of build-essential may be tricky a bit. In fact it is the version of the dependencies of both that make it harder than a simple "download & install".

So, let's try the standard way once more. Please follow the instructions from the official wiki to install the "STA" driver without internet connection -
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access)

I hope it is up-to-date, but if you face any issues following it, please let me know.

---

### Post by derekf2 on 2013-11-11
When i follow that guide in your link, i get to ```
 cd /cdrom/pool/main/d/dkms 
``` in terminal i type ```
 cd /media/pool/main/d/dkms 
``` it says No such file or directory.

media is my cd drive.

---

### Post by varunendra on 2013-11-11
> **derekf2 said:**
> media is my cd drive.

It can't be, unless you manually mount it there. To see where it is mounted, see the output of -
```
mount
```
If unsure, post the output here.

Sorry for the late responses, this never needed to be dragged like this. But right now I have to 'hunt' down opportunities to post here.. :)

---

### Post by derekf2 on 2013-11-11
mount 

```
 /dev/sda1 on / type ext4 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
none on /sys/fs/fuse/connections type fusectl (rw) 
none on /sys/kernel/debug type debugfs (rw) 
none on /sys/kernel/security type securityfs (rw) 
udev on /dev type devtmpfs (rw,mode=0755) 
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
none on /run/shm type tmpfs (rw,nosuid,nodev) 
gvfs-fuse-daemon on /home/derek/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=derek) 
/dev/sr0 on /media/Ubuntu 12.04.3 LTS i386 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks) 
```

That`s ok about your late responses, happy your helping me.

---

### Post by varunendra on 2013-11-11
> **derekf2 said:**
> ```
 
/dev/sr0 on **/media/Ubuntu 12.04.3 LTS i386** type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks) 
```

..so the address is -
```
cd "/media/**Ubuntu 12.04.3 LTS i386**/pool/main/d/dkms"
```
Make sure the address is within double quotes as above, since it contains blank spaces.

---

### Post by derekf2 on 2013-11-11
This is what i have done so far,

                        ```
 cd "/media/Ubuntu 12.04.3 LTS i386/pool/main/d/dkms" 
```

                        

sudo dpkg -i dkms*
  ```
 (Reading database ... 143070 files and directories currently installed.)  

 Preparing to replace dkms 2.2.0.3-1ubuntu3.1 (using dkms_2.2.0.3-1ubuntu3.1_all.deb) ...  
 Unpacking replacement dkms ...  
 Setting up dkms (2.2.0.3-1ubuntu3.1) ...  
 Processing triggers for man-db ... 
```

Now when i do the next step
                        ```
 cd "/media/Ubuntu 12.04.3 LTS i386/pool/main/p/patch" 
``` No such file or directory. i had a look and there is no p folder.

---

### Post by derekf2 on 2013-11-14
varunendra, Think i might give up on trying to connect to the internet with ubuntu.

---

### Post by galcrazy321 on 2013-11-14
It is easier then doing it with windows keep trying.

---

### Post by varunendra on 2013-11-14
> **derekf2 said:**
> varunendra, Think i might give up on trying to connect to the internet with ubuntu.

The driver you need works in the live session. So I'm quite sure you should have a working internet in a live session. You may choose enable "Third Party Software" & "Install Updates" during installation (assuming you have a working connection during installation). This will install the required driver automatically, and at the end of installation, you'll have a working wifi.

By the way, this error -
```
 cd "/media/Ubuntu 12.04.3 LTS i386/pool/main/p/patch"
```
..occured because the newer versions don't need that patch, so the installation media doesn't include that "patch" file. As such, the above error can be safely ignored.

**PS:**
I hope to get enough time tonight to make a comprehensive post to cover all possible solutions to the issue. Not a promise though :)

---

### Post by derekf2 on 2013-11-14
varunendra, i`ll wait to see what you post to get this connected.

---

### Post by derekf2 on 2013-11-22
I have given up on ubuntu, and installed pclinuxos and got connected first go. Thanks for your help.

---

