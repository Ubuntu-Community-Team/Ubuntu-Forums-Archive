---
title: "Setting up Wireless on Centrino"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by kingleer on 2006-12-27
I need help setting up my wireless connection. It think everything is working, but I don't know how to use ubuntu to connect. 

When I type iwconfig I get: 

lo   no wireless extensions 

eth0 no wireless extensions 

eth2 IEEE 802.11b ESSID: off/any  
       Mode:Auto Channel=0 Access Point: Invalid 
       Sensitivity=0/200 
       Link Quality:0 Signal level:0 Noise level:0 
       Rx invlid nwid:0  Rx invalid crypt:0 Rx invalid frag:0 
       Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

sit0 no wireless extensions. 

When I type ifconfig I get 

lo Link encap:Local Loopback 
    inet addr:127.0.0.1 Mask:255.0.0.0 
    inet6 addr: ::1/128 Scope:Host 
    UP LOOPBACK RUNNING MTU:16436 Metric:1 
    RX packets:353 errors:0 dropped:0 overruns:0 frame:0 
    TX packets:353 errors:0 dropped:0 overruns:0 carrier:0 
    collisions:0 txqueuelen:0 
    RX bytes:26232 (25.6 KiB) TX bytes:26232 (25.6 KiB) 

When I type route I get 

Kernel IP routing table 
Destination              Gateway               Genmask      Flags Metric Ref        Use Iface 

I am using ubuntu 6.10 (i386) on a centrino laptop. 

Right now I'm trying to follow: 

[http://www.ubuntuforums.org/showthread.php?t=325518](http://www.ubuntuforums.org/showthread.php?t=325518) 

and this: 

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) 

and this: 

[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

I think my card can't detect mywireless access point ...But I have a windows machine connected right now to my wireless network. My router is a linksys Wrt45g and its using wep encryption...

I try this command to see if my card can detect any wireless access point :

sudo iwlist eth2 scan

It asks me for a password, but when I try to enter a password my laptop freezes up. 

Someone who had a similair problem to mine said they had had Wireless connection unchecked in Network Settings. 

When I go to Network settings I see 

Wireless Connection 
The interface eth2 is not active 

Ethernet connection 
The interface eth0 is not active 

Modem connection 
The interface ppp0 is not configured 

Under interface properties of eth2 (my wireless card) 

I see 

A check mark beside - enable this connection 

Wireless Settings 

Network name (ESSID): My ESSID 
Key Type                      Hexadecimal 
Wep Key:                      my password 


Connection settings 

Configuration DHCP 

IP address       blank 

Subnet mask   blank 

Gateway address  blank 

When I try to click Activate on my wireless card a pop shows up saying 

Activating interface "eth2" 

And it says "The interface eth2 is active" under "Wireless connection" 


I then set my "Default gateway device: eth2" 

and I click "OK" 

BUT WHEN I GO BACK TO NETWORK SETTINGS IT SAYS 

"THE INTERFACE ETH2 IS NOT ACTIVE" UNDER WIRELESS CONNECTION 

And I'm all out of ideas, but I'm patient and willing to spend some time. If I've posted this in the wrong place than I'm sorry. 

Any help or trouble shooting procedures or advice or solutions any one answers would be much appreciated. I'm new to linux, but determined to get away from windows.

---

### Post by Thenotsowyzewun on 2006-12-27
Hi,

I'm pretty new too and setup my new Centrino laptop on Ubuntu 6.10 a few days ago (and I didn't even know what my ESSID was, just my key (only that parts written on the outside of my router).

Here's how I did it, I understand your computer froze when you tried to type in your password but maybe (hopefully that won't keep happening...).

1. I opened Applications | Accessories | Terminal
2. Tapped in apropos wireless (apropos tells you about commands related to a keyword ;) )
3. Played around with the various wireless tools, eventually discovered that
4. Tapping in 'iwlist eth1 scanning' discovered all available WiFi networks in the vicinity (there's a few) and gave me my ESSID too :).
5. Went into System | Administration | Networking and
6. unticked Wired Connection, since I didn't want to use it, and ticked Wireless Connection.
7. Then I clicked on Wireless Connection and then properties just to the right of it.
8. Made sure the tick box in the corner ("enable this connection") was on and then copied and pasted the ESSID from Terminal, changed "Password Type" to "Plain (ASCII)" because my password contains letters other than just 0-9 and a-f (e.g. x and s) and so was clearly not a Hexidecimal password.
9. Checked "Automatic Configuration (DHCP)" was selected from the drop-down and hit OK.
10. Clicked the Save icon up the top (the floppy disc) and saved the details as Ed's Flat (I'm living at my friend's flat whilst he's in OZ for a few months, that's why I didn't know the ESSID).
11. Pressed Close, opened up Firefox and it was working.

This should be all there is to it.
If it's still not working, make sure you PC does not have an external killswitch for turning the WiFi on/off - most laptops do, switch it to the On position. If one of these was present and turned off, you'll likely need to reboot and then follow the above instructions (the relevant ones anyway) from the start.

Hope that helps :)

---

### Post by kingleer on 2006-12-28
THANKS! 

I'll give it a try in the morning. :)

---

### Post by c.dric on 2006-12-28
Do you know which version of centrino wireless card you have ?
if not try the following command : 

lspci | grep Network

u need to know this to check you have the correct driver installed.

---

### Post by kingleer on 2006-12-28
I type in lspci | grep Network and I get 

0000:01:01.0 Network Controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01) 

Still no luck setting up my wireless. The scan reveals nothing and I'm pretty sure the radio switch is on...

---

### Post by kingleer on 2006-12-28
Oh, and can anyone give me a link to a list of wireless cards that work with ubuntu. I think I may have to use ndiswrapper...but I'm hoping my card is supported. 

Also, I ran into some trouble trying to install ubuntu on my desktop. It has an nforce chipset and an amd athalon X2 3800+ 64 bit...

---

### Post by c.dric on 2006-12-28
yep, from what i've found on the forums you'll have to use ndiswrapper with the win xp drivers.

but you'll have to remove and blacklist modules that are loaded automatically for your card and may interfere in the process.

could you post an output of 

lsmod

so we know exactly what has to be blacklisted ?

---

### Post by kingleer on 2006-12-28
Before we go any further I would like to thank you for taking the time to help me out here. 

Yes, I already figured I need to use ndiswrapper. I've been following - 

[http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926) 

and 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) 

and 

[http://ubuntuforums.org/showthread.php?t=35949](http://ubuntuforums.org/showthread.php?t=35949) 

but have only just started to figure out what to do. I downloaded the right windows driver I'll need though. 

OKAY, 


The output of "lsmod" is: 

Module                            Size          Used by 
nls_utf8                           2176         0
nls_cp437                        5888         0 
vfat                                 13440       0 
fat                                   53020       1 vfat 
sg                                   37920       0 
sd_mod                           19984       0
usb_storage                     74176       0
scsi_mod                         139496      3 sg,sd_mod,usb_storage 
ipv6                                 265728     6
rfcomm                            40216       0 
l2cap                                26244       5 rfcomm 
bluetooth                          49892       4 rfcomm, l2cap
ppdev                               9220         0 
i915                                  20608       1
drm                                  73236       2 i915 
cpufreq_userspace             4696         0 
cpufreq_stats                     5636         0 
freq_table                          4740         1 cpufreq_stats 
cpufreq_powersave            1920          0 
cpufreq_ondemand             6428         0
cpufreq_conservative          7332         0 
video                                 16260       0
tc1100_wmi                        6916         0 
sony_acpi                           5644         0 
pcc_acpi                             12416       0
hotkey                                11556       0
dev_acpi                             11140       0 
container                             4608        0 
button                                 6672         0
acpi_sbs                             19980        0 
battery                               9988          1 acpi_sbs
i2c_acpi_ec                         5120          1 acpi_sbs  
i12core                               21904         1 i2c_acpi_ec
ac                                       5252          1 acpi_sbs 
af_packet                            22920        2
dm_mod                              58936        1
md_mod                              72532        0
parport_pc                           35780        0 
lp                                        11844        0
parport                                36296        3 ppdev,parport_pc,lp
pcmcia                                 40508        0 
joydev                                 10048        0
tsdev                                   8000          0 
yenta_socket                        28428        1
rsrc_nonstatic                       13440        1 yenta_socket 
pcmcia_core                         42640        3 pcmcia,yenta_socket,rsrc_nonstatic
islsm_pci                              22152        0
islsm_device                         12040        1 islm_pci 
islsm                                    37644        2 islsm_pci,islsm_device 
ieee80211softmac                 28696         1 islsm 
ieee80211                            37064         2 islsm, ieee80211softmac
ieee80211_crypt                   6272           1 ieee80211 
crc_ccitt                               2304           1 islsm 
via_rhine                             23940          0 
psmouse                              36100         0 
mii                                       5888           1 via_rhine 
serio_raw                             7300           0
snd_intel8x0                         33692          1
snd_ac97_codec                    93088         1 snd_intel8x0
snd_ac97_bus                       2304           1 snd_ac97_codec
snd_pcm_oss                        53664         0 
snd_mixer_oss                      18688         1 snd_pcm_oss
snd_pcm                               89864         3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer                              25220         1 snd_pcm 
pcspkr                                   2180           0 
rtc                                         13492         0
snd                          55268      8     snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe 
r_oss,snd_pcm,snd_timer 
soundcore                              10208         1 snd 
snd_page_alloc                       10632         2 snd_intel8x0,snd_pcm 
shpchp                                   45632         0
pci_hotplug                            29236          1 shpchp 
intel_agp                               22940          1
agpgart                                 34888          3 drm,intel_agp 
evdev                                   9856            2
ext3                                      135688        1
jbd                                        58772          1 ext3 
ide_generic                            1536            0 
ehci_hcd                                34184          0 
uhci_hcd                                33680          0 
usbcore                                  130692       4 usb_storage,ehci_hcd,uhci_hcd 
ide_cd                                    33028         0 
cdrom                                    38560          1 ide_cd 
ide_disk                                 17664          3 
piix                                        11012          1
generic                                   5124           0 
thermal                                  13576          0 
processor                               23360          1 thermal 
fan                                        4868            0 
capability                               5000            0 
commoncap                            7296           1 capability 
vga16fb                                 13704          1
vgastate                                10368          1 vga16fb 
fbcon                                     42784          72 
tileblit                                    2816            1 fbcon
font                                       8320            1 fbcon 
bitblit                                     6272            1 fbcon 
softcursor                              2304             1 bitblit

---

### Post by kingleer on 2006-12-28
Okay, the formatting of my lastpost got a little messed up. Here's the output of lsmod as a .txt file upload.

---

### Post by c.dric on 2006-12-29
ok i would unload the islsm modules like so : 

sudo modprobe -r islsm_device
sudo modprobe -r islsm_pci
sudo modprobe -r islsm

and then add them to the blacklist :

sudo gedit /etc/modprobe.d/blacklist

[...add to the bottom of the listing....]
blacklist islsm_pci
blacklist islsm
blacklist islsm_device

now i would suggest you install ndiswrapper as explained by FrodoB in the 2nd post of this thread : 
[http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper)

if you don't have (wired) net access in ubuntu ... try to get the latest ndiswrapper on an usb or cd media.

if that worked fine you can load the winxp driver using ndiswrapper : 

unpack all the driver files ( .inf, .sys etc ... ) in the same folder (say Desktop) then load them

sudo ndiswrapper -i ~/Desktop/<filename>.inf

check to see if the driver and hardware are installed correctly : 

sudo ndiswrapper -l

then load the ndiswrapper module

sudo modprobe ndiswrapper

if you didn't get an error here, the module is loaded.
do this to get the module loaded at every boot : 

sudo ndiswrapper -m

your card should be running fine now.
if you're using wep (or no encryption at all) you can configure it in the Networking program in the System > Administration menu.

```
Before we go any further I would like to thank you for taking the time to help me out here. 
```

np :)

---

### Post by kingleer on 2006-12-29
Okay, I did everything you said right up until the part about installing ndiswrapper. I don't have wired internet yet on my ubuntu laptop, but I've downloaded ndiswrapper- 1.32.tar.gz onto a usb key. How do I go about installing it without having access to the internet?

---

### Post by kingleer on 2006-12-29
Oops. I didn't finish reading the rest of the other thread. Sorry. Installing ndiswrapper now.

---

### Post by kingleer on 2006-12-29
Okay, still following - [http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper) 

I am installing ndiswrapper at the moment. Everything is fine up until I enter: 

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 


Which gives me: 


Reading package lists... Done 
Building dependency tree... Done 
Package linux-headers is not installed, so not removed 
E: Couldn't find package 2.6.15- 26- 386 


Or is everything okay and I can proceed?

---

### Post by kingleer on 2006-12-29
Ok, I'm going to assume that 

E: Couldn't find package 2.6.15- 26- 386  

refers to 


Package linux-headers is not installed, so not removed  


And that its okay to continue.

---

### Post by kingleer on 2006-12-29
Yup, I entered: 


user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build 


and got no error so I assume that I'm on the right track.

---

### Post by kingleer on 2006-12-29
Ok, I am the point where I have to enter: 

Make the driver with the commands "make distclean", "make", and "make install":

user@ubuntu:~/ndiswrapper-1.32$ make distclean  


Only problem is when I enter

ndiswrapper-1.32$ make distclean  

I get 

bash:ndiswrapper-1.32$: command not found. 

When I try 

~/ndiswrapper-1.32$ make distclean   

I get 

bash: /root/ndiswrapper-1.32$: No such file or directory 

When I try /ndiswrapper-1.32$ make distclean  

I get 

bash: /ndiswrapper-1.32$: No such file or directory

---

### Post by kingleer on 2006-12-29
Okay, just entering "make distclean" Solves the problem. 


Moving on now.

---

### Post by kingleer on 2006-12-29
and another problem. 

Still following: 

[http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper) 

I'm at: 

user@ubuntu:~/ndiswrapper-1.31$ make 

And I get the following: 


make -C driver 
make[1]: Entering directory `/home/kinglear/ndiswrapper-1.32/driver' 
Can't find kernel build files in /lib/modules/2.6.15-25-386/build; 
    give the path to the kernel build directory with 
    KBUILD=<path> argument to make 
make[1]:*** [prereq_check] Error 1 
make[1]: Leaving directory `/home/kinglear/ndiswrapper-1.32/driver' 
make: *** [all] Error 2 


So I'm assuming this has something to do with what happened earlier: 


BELOW 


_____________________________________________
I am installing ndiswrapper at the moment. Everything is fine up until I enter:

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`


Which gives me:


Reading package lists... Done
Building dependency tree... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package 2.6.15- 26- 386
_______________________________________________________ 



All right, I assume I'm missing something from the install cd... 

Can you walk me through this problem too? 



Again, thanks for your patience.

---

### Post by kingleer on 2006-12-29
Ok, got past the last problem. 

Installed package 2.6.15- 26- 386 off the install cd. 

moving on.

---

### Post by kingleer on 2006-12-29
BIG PROBLEM 

I delt with all the problems I had before this step. 

I followed all your steps right to 

sudo ndiswrapper -l 

But I get the error: 

prisma00 : invalid driver! 

I'm going to check to see if everything works regardless. 

It looks like I didn't get the right windows driver for my card.

---

### Post by kingleer on 2006-12-29
Or maybe there is no problem at all? 

I enter "sudo modprobe ndiswrapper" and I get no error...

---

### Post by kingleer on 2006-12-29
Yes, we do have a problem. 

I restart my laptop and 

enter - "sudo ndiswrapper -m" to get this module loaded. 

I get the following error. 

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper   ... 
couldn't add module alias:  at /usr/sbin/ndiswrapper line 720. 



To clarify I think I followed your procedure correctly (I restarted from the very beginning when I made mistakes). And I keep think that I've got the wrong windows driver, but I'm certain I have the right one. 


I type in lspci | grep Network and I get

0000:01:01.0 Network Controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)


And following the ndiswrapper wiki found here: 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) 

That takes me to the download here: 

[http://download.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56](http://download.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56)



So, I stumped. 


To help with trouble shooting I would like to add that under network settings I don't see my wireless connection showing up at all. 



But, again, thanks for the help. Anything more you can do will be greatly appreciated. I'm trying to become independent from windows and setting up my wireless would help a whole lot.

---

### Post by c.dric on 2006-12-29
that's the problem i think : 

sudo ndiswrapper -l
prisma00 : invalid driver! 

remember this step ?

sudo ndiswrapper -i ~/Desktop/<filename>.inf

i don't know where you got the driver but usually they come in more  than one file.
you have an .inf file that you load with the command above but in the same folder you have one or more files with the same name but a different extension like .sys or .dat ... 

could u check that ?

if you still have the original cd with the driver you'll have all the file in it, or check the web.
copy all the files in the same folder as prisma00.inf and follow the setps below :

sudo modprobe -r ndiswrapper
sudo ndiswrapper -e prisma00

sudo ndiswrapper -i ~/Desktop/prisma00.inf 
sudo ndiswrapper -l

sudo modprobe ndiswrapper
sudo ndiswrapper -m

i hope this works.

---

### Post by kingleer on 2006-12-29
I enter: sudo ndiswrapper -i ~/prisma00.inf

and I get 

driver prisma00 is already installed

and yes I checked. There are other files besides .inf like PRISMA00.sys and PRISMAPI.dll 
and PRISMA00.cat 

Okay. 

I enter in 

sudo modprobe -r ndiswrapper
sudo ndiswrapper -e prisma00

sudo ndiswrapper -i ~/Desktop/prisma00.inf
sudo ndiswrapper -l

sudo modprobe ndiswrapper
sudo ndiswrapper -m
 

and everything works fine (NO ERROR MESSAGES) 

When I enter "sudo ndiswrapper -m" I get 

module configuration already contains alias directive. 


I don't know if that's good or bad, but where do I go from here? Can I check is my wireless is working and if so how?

---

### Post by kingleer on 2006-12-29
Err slight problem. In the top right hand corner under connection properties: eth2, the status of the device is "Error."  And eth2 doesn't show up under network Network settings at all. 


I think I've got the right windows driver and I think ndiswrapper is working good and is installed, but is it possible that we dissabled something we shouldn't have at this step?: 

[...add to the bottom of the listing....]
blacklist islsm_pci
blacklist islsm
blacklist islsm_device 

Atleast I think the above code disables something...

---

### Post by kingleer on 2006-12-29
More info on the error with eth2. 

I double click on the network icon in Connection Properties: eth2 

I get the message 

"Please contact your system administrator to resolve the following problem: 

SIOCGIFFLAGS error: NO such device"


eth2 being my wireless card.

---

### Post by c.dric on 2006-12-29
what do you get when you do 

sudo ndiswrapper -l

---

### Post by kingleer on 2006-12-29
Nothing. 

I enter ndiswrapper -l 

like so 

root@kinglear-laptop:~# ndiswrapper -l 

and the next line that pops up is 

root@kinglear-laptop:~#

---

### Post by kingleer on 2006-12-29
oops sorry. 

When I enter sudo ndiswrapper -l nothing happens either.  

root@kinglear-laptop:~# sudo ndiswrapper -l

and the next line that pops up is

root@kinglear-laptop:~#

---

### Post by kingleer on 2006-12-29
I can take screen shots if you think it would help. 

Here are some screenshots of the error I get under eth2 (my wireless card) properties and configuration.

---

### Post by c.dric on 2006-12-29
sudo ndiswrapper -l 

should give you something like "prisma00 driver present, hardware present" otherwise it's not installed properly.

could u do the following 

islsm | grep islsm

to check if the modules we blacklisted are really not interfering.
If you don't get anything, i would try the following one last time : 

sudo modprobe -r ndiswrapper

sudo depmod -a 

sudo ndiswrapper -e prisma00

sudo ndiswrapper -i ~/Desktop/prisma00.inf
sudo ndiswrapper -l

(i hope you will get "prisma00 driver present, hardware present" now)

sudo modprobe ndiswrapper
sudo ndiswrapper -m

iwconfig 

i hope this will work out because i'm running out of ideas :neutral:

---

### Post by kingleer on 2006-12-29
sudo ndiswrapper -l gives me nothing. So we've narrowed down the problem - my windows driver may not be properly installed. 


islsm | grep islsm

Gives me 

bash: islsm: command not found 

sudo modprobe -r ndiswrapper 

Gives me nothing 

sudo depmod -a  

Gives me nothing 

sudo ndiswrapper -e prisma00 

Gives me 

couldn't delete /etc/ndiswrapper/prisma00: No such file or directory 

sudo ndiswrapper -i ~/Desktop/prisma00.inf 

Gives me an error but I didn't put prisma00.inf on my desktop (its in a folder in my home folder). 

If i put the contents of that folder on my desktop and enter 

sudo ndiswrapper -i ~/Desktop/prisma00.inf 

I get 

driver prisma00 is already installed 


sudo ndiswrapper -l 

prisma00: invalid driver! 



I'll post a screen shot of what I'm actually typing for you to see. 


And if you've run out of ideas, lets assume I made a mistake following your directions somewhere. 

I'll start over from scratch from the begginning but I'll post screen shots of my steps. 


Pictured below is how I followed the procedure you gave me. 


I can already think of some mistakes I may have made. The actual name of the file is 
PRISMA00.inf and not prisma00.inf. Also, I didn't keep the contents of the windows driver on my desktop, but in another folder. 


Okay, so check out the png below.

---

### Post by kingleer on 2006-12-29
Again thanks for your help. I'll understand if you have other obligations. The procedure you gave me may be perfectly correct, but I screwed it up, because I'm rather new at this. I'll keep trying until I get it. :)

---

### Post by c.dric on 2006-12-29
sorry islsm | grep islsm should have been : 

lsmod | grep islsm

i see you run the command as root ... but did you unpack the driver files in the home folder of root or the home folder of your regular user ? if the later do the following : 

exit

to go back to your regular user and re-try the steps below 

sudo ndiswrapper -e prisma00
sudo ndiswrapper -e PRISMA00
(one of the two should work)

sudo modprobe -r ndiswrapper
(should return nothing)

sudo ndiswrapper -i ~/PRISMA00.inf 
(if files are in your home folder)
sudo ndiswrapper -i ~/Desktop/PRISMA00.inf 
(if files are in your Desktop folder)

sudo ndiswrapper -l 
(should give you "prisma00 driver present, hardware present")

sudo modprobe ndiswrapper
sudo ndiswrapper -m

iwconfig 

```
The procedure you gave me may be perfectly correct, but I screwed it up, because I'm rather new at this. 
```

i'm just explaining the normal procedure to get ndiswrapper up and running, 
but there is not much info to be found on the forum about this card.

```
I'll keep trying until I get it.
```

that's the spirit :)

---

### Post by kingleer on 2006-12-29
NUTS! I think I unpacked the files of the driver in the home folder of my regular user kinglear. 

AND I THINK THAT I'VE BEEN DOING EVERYTHING IN ROOT SINCE THE BEGINNING WHILE MY DRIVER FILES WERE INSIDE MY REGULAR USERS HOME FOLDER (kinglear).!!!!!!!!!! 

Okay, so I exited root, and went into a normal terminal. I run into a problem. I get prompted for my password, but when I try to enter it  I am unable to do so (I click on a key and nothing happens).

---

### Post by c.dric on 2006-12-29
u should type your password and press enter.
it's normal you don't see what you type.

i see lsmod | grep islsm gives nothing which is also good.

just follow the steps in my last post and hopefully you'll be online soon :)

---

### Post by kingleer on 2006-12-29
Ohhhhh, I see. Okay, I was able to enter in my password. 

But still no dice. I'm thinking that maybe I'm using the wrong PRISMA00.inf. When I extracted the archive containing the driver there were several folders - one for windows nt, another for xp, etc. 

Also, I did the entire procedure up until now in root, which is why things might not be working.

---

### Post by kingleer on 2006-12-29
Nuts I forgot the picture. Here's the screenshot of what I did.

---

### Post by kingleer on 2006-12-29
If you've run out of ideas I'll try again soon to start from the very begginning, but I won't do things in root. I think that may be the big problem.

---

### Post by c.dric on 2006-12-29
Being root was only a problem when u tried to install the driver (sudo modprobe -i ...)

I don't think you should re-install ndiswrapper from the beginning.

If you try to install a driver you have to remove the previous one, otherwise  you'll get those "driver prisma00 is already installed" 

Also you have to respect the case and you can't forget the .inf at the end when u install the driver.

what i would do ... go to your home folder ... check that all the files are there and check that they are spelled exactly the same way as below, if not modify my commands : 

**1/ Clean previous attempts **

sudo modprobe -r ndiswrapper

sudo ndiswrapper -e prisma00
or 
sudo ndiswrapper -e PRISMA00

this will remove driver from previous attempts. always do this before attempting to make a new install. if you don't get an error message it worked and u can go to the next step.

**2/ Attempt to install driver**

sudo ndiswrapper -i ~/PRISMA00.inf

this will try to install the driver from your home directory.

**3/ Check installed driver**

sudo ndiswrapper -l 

this will list properly installed driver & hardware.
if that worked go to step 4/ otherwise go back to step 1/ and try installing another driver.

**4/ Loading ndiswrapper **

sudo modprobe ndiswrapper 

this will load the ndiswrapper. you won't get any message.

no need to do sudo ndiswrapper -m, the link is already on your system.

**5/ Checking the wireless interface**

iwconfig

this will list properly set-up wireless interface.

---

### Post by kingleer on 2006-12-29
Okay got an error saying that I have the wrong driver at step 3. See the screenshot for details. As I said there were other prisma00.inf files inside the archive I downloaded. I'm gonna try them now.

---

### Post by c.dric on 2006-12-29
u got an error because u entered the wrong filename ( sudo ndiswrapper -i ~/P ), do 

sudo ndiswrapper -e p

and the error should disappear when u do 

sudo ndiswrapper -l

now, that message about an alternate driver may be another problem. 
could u redo the following and post the output if any 

lsmod | grep islsm

---

### Post by kingleer on 2006-12-29
But the good news is it seems like the problem is that I may not have the right windows driver... (we know what the problem may be specifically).

---

### Post by kingleer on 2006-12-29
Sorry I started, agaun, at

>>1/ Clean previous attempts

No output for 

lsmod | grep islsm

---

### Post by kingleer on 2006-12-29
I think in the mean time I'll try looking up my the card name I got when I entered lsmod

Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

[http://prism54.org/punbb/viewtopic.php?pid=6757](http://prism54.org/punbb/viewtopic.php?pid=6757)

The link above does not refer to ubuntu. 

">02:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow]

Won't work with the Prism54 FullMAC driver. No need to try any further with it. Install islsm." 

and when I do a search for islsm in ndiswrapper driver list I get 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) 


 "   * Chipset: Prism54
    * USBID: Vendor=5041 ProdID=2235 (5041:2235)
    * Driver: I got this working (with WPA-PSK CCMP/TKIP) effortlessly using the ndiswrapper/wpa_supplicant packages bundled on the Ubuntu 6.06 CD. I used the Linksys WUSB54GPv4 1.02.00 driver release here which also includes the WUSB54GPv1 drivers in their own folder. I have not checked if this driver is the same as the one in the seperate WUSB54GPv1 driver release; I just know it works. Also, i had to blacklist the islsm modules ([www.prism54.org](www.prism54.org)) that ship with Ubuntu. "


So I'm checking out [http://www.prism54.org/](http://www.prism54.org/) 

which is a 

The Prism54 project is now made up of three pieces of software : islsm, a Linux driver which supports the new ISL3886/ISL3887-based devices (known as "newmacs" or "softmac" devices), p54u, which is the FreeBSD equivalent of islsm (only USB devices are supported by now, though) and FreeMAC, aimed at writing a GPL-licensed firmware for all Conexant chipsets (no matter whether they are supposed to run SoftMAC or FullMAC firmwares). FreeMAC is currently unusable for non-developers, but islsm and p54u are functional with SoftMAC firmwares. All these projects are done with no help from Conexant, we have to reverse engineer their designs.

---

### Post by kingleer on 2006-12-29
Continued 

islsm
This is the Linux driver for all the new Prism devices with an ISL38xx, even if they are SoftMAC. It supports USB and PCI.
For now, this is located at [http://jbnote.free.fr/](http://jbnote.free.fr/)  


I think there may be a possibility that we are using the wrong driver. I'm going to try and use the drivers I find here IF ALL ELSE FAILS.

EDITED 

Nope, I think I have had the right driver from the beginning.

---

### Post by c.dric on 2006-12-29
prisma00.sys shouldn't be there ... remove it 

sudo ndiswrapper -e prisma00.sys

i found an how-to on the web to get your card working on ubuntu ... 
it's almost the same as what we did but maybe with a different driver. 

[http://patrick.vande-walle.eu/software/intersil-isl3886-linux/](http://patrick.vande-walle.eu/software/intersil-isl3886-linux/)

if you want to try ... you should clean previous attempts like so 

sudo ndiswrapper -e prisma00

make sure you don't mix the new drivers in the same folder as the old.

when you install the new driver with 'sudo ndiswrapper -i ...' 
make sure the folder, the case, the filename and the extension are correct or it won't work.

---

### Post by kingleer on 2006-12-29
SUCCESS!?!?!?!?!!?!?!!?!?!!?!?!!!?!? 


SEE THE ATTACHED SCREENSHOT!!!!!!!!!!! 

But how do I test it?

---

### Post by kingleer on 2006-12-29
Yahooooooooooo!!!!!!!!!! It Works!!!!!!!!!!!!!! :-d :-d :-d :-d :-d :-d

---

### Post by kingleer on 2006-12-29
Yup, it works. 

I'm on google right now. 

THANK YOU SO MUCH! I COULDN'T HAVE DONE THIS WITHOUT YOU! 

I now have no reason to install windows ever again. Next step, get ubuntu up and running on my desktop computer, but thats for another day. DUDE, I OWE YOU SO MUCH!

---

### Post by c.dric on 2006-12-29
NP. I hope u have a lot of wireless fun. :D 

In case it doesn't start automatically when your system boots up 

> 5# For some reason the ndiswrapper module would not load automatically at start-up for me. I added “modprobe ndiswrapper” to /etc/rc.local. Not clean, but it works.

---

### Post by kingleer on 2006-12-29
BEHOLD: the fruit of our labours! 

There is one last question I want to ask you. Ubuntu uses aptget to download programs off the web. But how would I go about saving the installation files offline for if the situation arises where I don't have internet access and want to install something?

---

### Post by c.dric on 2006-12-29
> There is one last question I want to ask you. Ubuntu uses aptget to download programs off the web. But how would I go about saving the installation files offline for if the situation arises where I don't have internet access and want to install something?

I would have to look into it ... I was using Gentoo Linux until 2 weeks ago so i don't know where everything is located in Ubuntu ... yet :???: 

what i wanted to ask you : which drivers did u use and where did you download them from ?
this may be useful for other people in your situation.

---

### Post by kingleer on 2006-12-29
First of all I looked up ndiswrapper on wikipedia.org 

[http://en.wikipedia.org/wiki/Ndiswrapper](http://en.wikipedia.org/wiki/Ndiswrapper) 

There a list here: 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) 

In root, I typed in lspci | grep Network and I got

0000:01:01.0 Network Controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01) 

So I went to the list here: lhttp://ndiswrapper.sourceforge.net/mediawiki/index.php/List  

And did a search for the name of my card. The following download link was recommended for 
my card in particular - 

[http://download.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56](http://download.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56)

And then I just followed your directions. 

The reason why I had so much trouble was because I didn't remove prisma00.sys.

---

### Post by kingleer on 2006-12-29
UHM, one last small problem. Now that I've rebooted I can't seem to be able to connect. :)

---

### Post by kingleer on 2006-12-29
>>For some reason the ndiswrapper module would not load automatically at start-up for me. I added &#8220;modprobe ndiswrapper&#8221; to /etc/rc.local. Not clean, but it works. 

Okay, I'm gonna give that a try. So it should look like - 

# By default this script does nothing.
modprobe ndiswrapper 
exit 0

(done using gedit I assume)

---

### Post by kingleer on 2006-12-29
HELLLLLLLP - Now that I've restarted I can't connect!

---

### Post by kingleer on 2006-12-29
sudo ndiswrapper -m 

This doesn't work for some reason. Do I have to start all over again?

Edited thats what I tried to do. 

sudo ndiswrapper -l gives 

prisma00: driver installed 
                device (1260:3886) present (alternate driver: islsm_pci) 

BUT 

When I enter sudo modprobe ndiswrapper 
FATAL: Error inseting ndiswrapper (/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument. 


I did an update after I connected to the web and that required a restart.

---

### Post by c.dric on 2006-12-29
sudo ndiswrapper -l 

to check if the driver is still installed correctly

lsmod | grep ndiswrapper 
(an output is good)

to check if ndiswrapper is still loaded properly

lsmod | grep islsm 
(no output is good)

to check if the blacklisted modules are not interfering

iwconfig

to check if a wireless interface is up

---

### Post by kingleer on 2006-12-29
Here's a screen shot of everything.

---

### Post by c.dric on 2006-12-29
could u give the output of the commands just after rebooting ...
it looks like you first tried a few commands that may interfere with the results.

---

### Post by kingleer on 2006-12-29
Okay right after reboot (keeping in mind that I also did an upgrade that required a restart): 

I think I may have accidentally typed what the screen shot shows instead of 

sudo ndiswrapper -m

---

### Post by kingleer on 2006-12-29
Is there anyway to roll back changes in ubuntu, kinda like system restore in windows...Probably not, but...

But I have not put anything really important on ubuntu yet and its the only os on my laptop right now. Rather than trouble shooting it would probably be easier to just do a fresh reinstall, and follow the original steps over again. I'm pretty confident I could do it alone now thanks to you. Than I would I added &#8220;modprobe ndiswrapper&#8221; to /etc/rc.local right away with gedit. But how exactly is rc.local suppossed to look like (the code)? 

Look thanks for the help, but I'll go with a reinstall and edit rc.local right after I get wireless working so I don't mess anything up anymore.

---

### Post by kingleer on 2006-12-29
In case you're wondering I got my internet up and running again. I'm fairly certain it was an update I did.

---

### Post by c.dric on 2006-12-30
nice :)

---

### Post by kingleer on 2006-12-30
The thing is I'm able to get my wireless working, but when I restart it stops working. ] (*,)  

And I restart again and magically, its working??????

And now its not working again after another restart. 

I reinstalled Ubuntu, but I used the dvd install image now instead of the cd install image of 6.10. 

using gedit to  add &#8220;modprobe ndiswrapper&#8221; to /etc/rc.local doesn't help. 

Okay see the screenshot below for some analysis I tried doing...

---

### Post by c.dric on 2006-12-30
it looks like ndiswrapper doesn't load properly at boot.
you should do the following, if you haven't already 

**sudo gedit /etc/modules**

Add the word 

**ndiswrapper**

and save it.

---

### Post by kingleer on 2006-12-30
like so? (see screen shot)

and when I reboot what should I do? 

OR should I try to adding “modprobe ndiswrapper” to /etc/rc.local again?

---

### Post by c.dric on 2006-12-30
yep like that.

it should load automatically at boot.

---

### Post by kingleer on 2006-12-30
I still get the same results...should I try a fresh install and attempt the sudo gedit /etc/modules add ndiswrapper  as well as adding “modprobe ndiswrapper” to /etc/rc.local again?

---

### Post by kingleer on 2006-12-31
Yup. Fresh install and sudo gedit /etc/modules add ndiswrapper as well as adding &#8220;modprobe ndiswrapper&#8221; to /etc/rc.local again fixed the problem. 

I restarted once - everything worked. 

I restarted twice, and now it does not. Which I find strange, because I didn't change or do anything between restarts.

---

### Post by kingleer on 2006-12-31
OKKKKAAAAAAY 

This is getting really strange now. 

I restarted again (without making any changes) and everything is working fine again (with out making any changes). 


I'm gonna do a few more restarts - see if I notice a pattern...

---

### Post by kingleer on 2006-12-31
I restart again - Wireless not working. 

I restart once more - EVERYTHING IS WORKING 

Does a few more restarts - A pattern emerges. If wireless is not working and I do a restart it is working again. If wireless is working and I do a restart it is not working. 

I'm interested in ubuntu and want to get away from windows as soon as possible. I can live with this, but I wouldn't mind having an explanation or a solution. 

I'm thinking of making a guide on how to set up my wireless card in ubuntu - aimed specifically at noobs like myself (you would get all the credit). 

This thread is already two cluttered to be a lot of use to anyone. 


One explanation I would like to offer is that lots of things are loading when linux starts up and 
ndiswrapper doesn't get a chance to load in time...

NEVERMIND. 

The pattern is broken if I just do a complete shutdown (wireless always works). I'm typing this on ubuntu right now.

I just did an update and everything is fine. None of my comps are running windows now - don't need it anymore. 

Next step setting dual booting ubuntu on my desktop pc (which is currently a hackintosh). 

AGAIN,  c.dric  THANKS FOR ALL YOUR HELP. Happy new year.  If you ever need help with anything just let me know (I'll update my user profile  with an email). 

I've bookmarked your profile, and added you to my buddy list. I'll write up a concise set of instructions summarizing this thread and your advice to get my particular wireless card working (might be useful for you if you ever encounter someone with the same problem again).

---

### Post by c.dric on 2006-12-31
it's strange ... it can be hard to set-up a wireless connection in linux but usually once you do, it keeps working. a connection that works half of the time is very un-linux like ... 

you don't have to credit me for anything, i'm just passing over what i've found in docs and forums while setting up my computers.

happy new year to you too :)

---

