---
title: "Help on ndiswrapper guide error"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by SickNick on 2007-04-03
I have a HP DV2000 Laptop with the AMD Processor which contains broadcomm wireless cards. I was recommended to use this guide: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

it all goes good until the mid-end of step 5 when i get these errors:

tsilo@tsilo:~/ndiswrapper-1.34$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done
tsilo@tsilo:~/ndiswrapper-1.34$ sudo apt-get install cabextract unzip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract

instead i do this

tsilo@tsilo:~/ndiswrapper-1.34$ sudo apt-get install unzip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unzip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

tsilo@tsilo:~/ndiswrapper-1.34$ cd ~
tsilo@tsilo:~$ cd bcm4311
tsilo@tsilo:~/bcm4311$ unzip sp33008.exe
Archive:  sp33008.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of sp33008.exe or
        sp33008.exe.zip, and cannot find sp33008.exe.ZIP, period.
tsilo@tsilo:~/bcm4311$ 

So now im stuck nd dont know where to go but ask here. I followed everything exactly as it said. When it says to uncomment those repos all you need to do is add a ## in front correct??

---

### Post by spd106 on 2007-04-03
No, you remove the hash to uncomment. It should look like this ```
$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe

```
Except you'll probably use a us rather than a gb mirror. 

You can grab the package directly from [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fc%2Fcabextract%2Fcabextract_1.1-1_i386.deb&md5sum=87de48b7eb0be982ac8cbb14f293aa96&arch=i386&type=main").

---

### Post by SickNick on 2007-04-03
thanks for the response, yea that did the trick on that part, i downloaded and succusfully went through all the steps with no error again, it said that the files where unzipped with no error... but now i get this at this part:

tsilo@Linux:~/bcm4311$ ndiswrapper -a 14E4:4324 bcmw15
ls: /etc/ndiswrapper/bcmw15/: No such file or directory
driver 'bcmw15' is not installed (properly)!
tsilo@Linux:~/bcm4311$ ls /etc/ndiswrapper
bcmwl5
tsilo@Linux:~/bcm4311$ bcmwl5
bash: bcmwl5: command not found


thanks in advance

---

### Post by spd106 on 2007-04-04
You have typed a '1' instead of an 'l'. This is not your fault, the wiki page is confusing. This step is not necessary if you receive the hardware present message from *ndiswrapper -l* .

---

### Post by SickNick on 2007-04-04
beautiful, ive been trying to get this to work for months now, im on it in school finally working. Hopefully i dont jinx myself nd mess it up lol. Thank you very much for your help i appreciate it

---

### Post by SickNick on 2007-04-06
Just as everything was good, i duno what happenned i turned on my laptop, nd there was an error symbol on my wireless. And all that was happenning was baisically i would see wlan when i went to properties, then when i hit configure, it said that the interface dosent exist. When i do iwconfig, all the connections are no extensions. lspci, i see my broadcom there tho, what the hell is going on???

---

### Post by spd106 on 2007-04-06
To check that the module/driver is being loaded, try this```
lsmod | grep ndiswrapper
```
You may need to add ndiswrapper to the /etc/modules file.

---

### Post by SickNick on 2007-04-06
i ran it nothing hapenned tho, heres what i saw in the terminal, i appreciate you helping me out with this:

tsilo@Linux:~$ lsmod | grep ndiswrapper
tsilo@Linux:~$ lsmod
Module                  Size  Used by
nls_utf8                3840  1 
nls_cp437               8704  1 
vfat                   17920  1 
fat                    65456  1 vfat
usb_storage            89792  1 
libusual               21544  1 usb_storage
ipv6                  334432  10 
binfmt_misc            16012  1 
rfcomm                 51360  0 
l2cap                  31744  5 rfcomm
powernow_k8            16576  1 
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  1 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sbs                    20928  0 
sony_acpi               7704  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
hotkey                 14536  0 
dev_acpi               17540  0 
button                  9888  0 
battery                14088  0 
container               6656  0 
ac                      8328  0 
asus_acpi              21924  0 
sbp2                   29448  0 
parport_pc             43560  0 
lp                     16584  0 
parport                49932  2 parport_pc,lp
af_packet              29452  2 
joydev                 14208  0 
tsdev                  11136  0 
snd_hda_intel          23452  1 
snd_hda_codec         219392  1 snd_hda_intel
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
sg                     44584  0 
hci_usb                21268  2 
snd_pcm               108168  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
sdhci                  22796  0 
mmc_core               40456  1 sdhci
bluetooth              64644  7 rfcomm,l2cap,hci_usb
nvidia               5444468  20 
snd_timer              31112  1 snd_pcm
psmouse                51088  0 
serio_raw              10244  0 
evdev                  14592  2 
shpchp                 49068  0 
pcspkr                  5248  0 
pci_hotplug            38912  1 shpchp
i2c_core               29312  2 i2c_ec,nvidia
snd                    79016  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              14112  1 snd
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
ext3                  164880  1 
jbd                    74024  1 ext3
ohci1394               40776  0 
ohci_hcd               25988  0 
ieee1394              387704  2 sbp2,ohci1394
ehci_hcd               40456  0 
usbcore               167840  6 usb_storage,libusual,hci_usb,ohci_hcd,ehci_hcd
forcedeth              37644  0 
ide_generic             2944  0 
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
generic                 7940  0 
sd_mod                 25728  5 
amd74xx                17712  0 [permanent]
sata_nv                13572  2 
libata                 88984  1 sata_nv
scsi_mod              181424  5 usb_storage,sbp2,sg,sd_mod,libata
thermal                19472  0 
processor              38280  2 powernow_k8,thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit
tsilo@Linux:~$

---

### Post by spd106 on 2007-04-06
Lsmod tells you which modules are currently loaded, as ndiswrapper wasn't listed it wasn't loaded so the card won't work. To get it working you have to run *sudo modprobe ndiswrapper*.

Back in the guide you mentioned previously, at step 8 you need to add a line to the /etc/modules file to ensure that ndiswrapper is loaded at startup.

---

### Post by SickNick on 2007-04-07
yup that was the problem, it wasnt working at first i had to play arround with things, nd then i put network manager on, nd everything seems to be workign good now. It started off a little glitchy but it started connecting now

---

### Post by SickNick on 2007-04-09
well, here we go again, this is the problem now, it was the problem in the beginning that i referred to as glitchy in my last post. Baisically what happens, is that it dosent always connect, most times it dosent connect. I just restarted 4 times in order for it to connect. It just attempts to connect for 2 mins nd then stops nd is not connected, i do iwconfig to see if everything is right, nd it is. My last restart i did iwconfig b4 to see what essid is thre nd there was none which was right, nd then when i clikced the one i wanted on network manager it showed on iwconfig, all good, nd then it connected... Why is it having a mind of its own??

---

### Post by spd106 on 2007-04-09
Try looking the the /var/log/syslog file for errors.

---

