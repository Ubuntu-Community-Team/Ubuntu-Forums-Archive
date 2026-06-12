---
title: "How to install linux driver"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by johnfrith on 2010-03-20
Am on Ubuntu 9.10 (64bit), and have been trying to get wireless working (RTL811/RTL8186B with 10ec:l8168 chipset). I'm an absolute beginner, and have been trying to get a driver working with ndiswrapper, but have just noticed that Realtek have just released a unix driver for this chipset. So have questions:

1) Could it be that the problem is with me using 64 bit Ubuntu? I saw a site that said this driver was supported in kernal 2.6.25, and I have 2.6.31. (For some reason I can't get the 32 bit to download).

2) If I just want to install the new unix driver, do I need to de-install ndiswrapper, and unblock the default drivers. If so how?

3) The Unix driver download from the manufacturer produces a tar (which I presume is a compressed file format). I've copied the readme notes below, but I get lost on "unpack the tarball". I hate to be so helpless, but I've tried hard to sort these issues out on my own.

4) Does anyone know how I can find out if the unix driver is included in Ubuntu 10.4 (short of installing it and seeing if it works)? Are all drivers in the kernal, or do Ubuntu add some on top?

Any help appreciated.

John

"<Linux device driver for Realtek Ethernet controllers>

    This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D, RTL8168DP/8111DP, and RTL8168E/8111E Gigabit Ethernet controllers with PCI-Express interface.

<Requirements>

    - Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
    - For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
    - Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
    Unpack the tarball :
        # tar vjxf r8168-8.aaa.bb.tar.bz2

    Change to the directory:
        # cd r8168-8.aaa.bb

    If you are running the target kernel, then you should be able to do :

        # ./autorun.sh    (as root or with sudo)

    You can check whether the driver is loaded by using following commands.

        # lsmod | grep r8168
        # ifconfig -a

    If there is a device name, ethX, shown on the monitor, the linux 
    driver is loaded. Then, you can use the following command to activate 
    the ethX.

        # ifconfig ethX up

        ,where X=0,1,2,...

<Set the network related information>
    1. Set manually
        a. Set the IP address of your machine.

            # ifconfig ethX "the IP address of your machine" 

        b. Set the IP address of DNS.

           Insert the following configuration in /etc/resolv.conf.
        
            nameserver "the IP address of DNS"

        c. Set the IP address of gateway.

            # route add default gw "the IP address of gateway"

    2. Set by doing configurations in /etc/sysconfig/network-scripts
       /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
       /ifcfg-ethX for SuSE. There are two examples to set network 
       configurations.

        a. Fixed IP address:
            DEVICE=eth0
            BOOTPROTO=static
            ONBOOT=yes
            TYPE=ethernet
            NETMASK=255.255.255.0
            IPADDR=192.168.1.1
            GATEWAY=192.168.1.254
            BROADCAST=192.168.1.255

        b. DHCP:
            DEVICE=eth0
            BOOTPROTO=dhcp
            ONBOOT=yes    

<Modify the MAC address>
    There are two ways to modify the MAC address of the NIC.
    1. Use ifconfig:

        # ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

       ,where X is the device number assigned by Linux kernel, and
          YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

    2. Use ip:

        # ip link set ethX address YY:YY:YY:YY:YY:YY

       ,where X is the device number assigned by Linux kernel, and
          YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

    1. Force the link status when insert the driver.

       If the user is in the path ~/r8168, the link status can be forced 
       to one of the 5 modes as following command.

        # insmod ./src/r8168.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

        ,where
            SPEED_MODE    = 1000    for 1000Mbps
                    = 100    for 100Mbps
                    = 10    for 10Mbps
            DUPLEX_MODE    = 0    for half-duplex
                    = 1    for full-duplex
            NWAY_OPTION    = 0    for auto-negotiation off (true force)
                    = 1    for auto-negotiation on (nway force)
        For example:

            # insmod ./src/r8168.ko speed=100 duplex=0 autoneg=1

        will force PHY to operate in 100Mpbs Half-duplex(nway force).

    2. Force the link status by using ethtool.
        a. Insert the driver first.
        b. Make sure that ethtool exists in /sbin.
        c. Force the link status as the following command.

            # ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

            ,where
                SPEED_MODE    = 1000    for 1000Mbps
                        = 100    for 100Mbps
                        = 10    for 10Mbps
                DUPLEX_MODE    = half    for half-duplex
                        = full    for full-duplex
                NWAY_OPTION    = off    for auto-negotiation off (true force)
                        = on    for auto-negotiation on (nway force)

        For example:
        
            # ethtool -s eth0 speed 100 duplex full autoneg on

        will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
    Transmitting Jumbo Frames, whose packet size is bigger than 1500 bytes, please change mtu by the following command.

    # ifconfig ethX mtu MTU

    , where X=0,1,2,..., and MTU is configured by user.

    RTL8168B/8111B supports Jumbo Frame size up to 4 kBytes.
    RTL8168C/8111C and RTL8168CP/8111CP support Jumbo Frame size up to 6 kBytes.
    RTL8168D/8111D supports Jumbo Frame size up to 9 kBytes.
"

---

### Post by cariboo on 2010-03-20
There is a r8169 module going back to at least Jaunty, you could try that. Open a terminal and type:

```
sudo modprobe r8169
```

The above command inserts the module.

---

### Post by patchwork on 2010-03-20
EDIT:  Try Cariboo's suggestion first, it can potentially save some hassle

If you got it from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2"), it says it will support both 32 and 64 bit distributions.  

I'm not sure about the ndiswrapper question (I've never had the pleasure...)

The instructions provided with the driver are pretty straight forward.  Open a terminal and type the commands provided (the commands are after the # sign) ```
tar vjxf blah blah
``` When you go to run the installation script, you will need to type```
sudo ./autorun.sh
``` and enter your superuser password.  

Best of luck, and post back if you need further help.

---

### Post by johnfrith on 2010-03-20
Thanks cariboo - tried it but no change.
Thanks patchwork - will give it a try.

---

### Post by johnfrith on 2010-03-20
Ok, so presumably the tar file needs to be in a certain directory? Or is there something I'm missing about the path as seen from the terminal? 

Me so far:
john@john-laptop:~$ tar vjxf /home/john/IT Docs/r8168-8.017.00.tar.bz2
tar: /home/john/IT: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Docs/r8168-8.017.00.tar.bz2: Not found in archive
tar: Exiting with failure status due to previous errors

Thanks in advance. John

---

### Post by johnfrith on 2010-03-20
Also, anyone know why the (not working) driver is still installed after blacklisting? (I have rebooted):

john@john-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
net8187b : driver installed
    device (0BDA:8189) present (alternate driver: rtl8187)

blacklist.conf lists:
# This file lists those modules which we don't want to be loaded by
<snip>
# really needed.
blacklist amd76x_edac
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist net8187b

---

### Post by patchwork on 2010-03-21
The shell does not like whitespace in directory or filenames.  Either enclose you directory in quotes like this```
/"IT Docs"/
```or place a \ in front of the space (this tells the terminal to ignore the space behind it) ```
/IT\ Docs/
```

Not sure why the module is still loading, you could remove the module....
```
sudo rmmod net8187b
```  ...load your new driver, and see if the new driver will preempt the wrong one.

---

### Post by johnfrith on 2010-03-21
Many thanks patchwork.

First I tried to unload driver:

john@john-laptop:~/r8168-8.017.00$ sudo rmmod net8187b
[sudo] password for john: 
ERROR: Module net8187b does not exist in /proc/modules

Could the failure to unload be something to do with me having downloaded / installed it rather than it being part of Ubuntu? Or could some special characters have gotten into the filename?

I did manage to unpack the tar file, though, and got this on install:

john@john-laptop:~/r8168-8.017.00$ sudo ./autorun.sh

Check old driver and unload it.
rmmod r8169
Build the module and install
/home/john/r8168-8.017.00/src/r8168_n.c: In function ‘rtl8168_close’:
/home/john/r8168-8.017.00/src/r8168_n.c:8732: warning: unused variable ‘ioaddr’
/home/john/r8168-8.017.00/src/r8168_n.c: In function ‘rtl_get_eeprom’:
/home/john/r8168-8.017.00/src/r8168_n.c:1806: warning: ‘ret’ may be used uninitialized in this function
[: 48: r8168: unexpected operator
Backup r8169.ko
rename r8169.ko to r8169.bak
Depending module. Please wait.
load module r8168
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Completed.

Despite the "unexpected operator" message and reference to r8169 (not sure where that comes from) I was hopeful this had worked, but it seems the old driver is still installed, and no sign my system is even looking for a wireless connection:

john@john-laptop:~/r8168-8.017.00$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
net8187b : driver installed
    device (0BDA:8189) present (alternate driver: rtl8187)

---

### Post by patchwork on 2010-03-21
What is the output of ```
lsmod
```
You should see the r8168 module loaded there.

You shouldn't need ndiswrapper with the new driver (it is used to 'wrap' Windows wireless drivers for use in linux, but is not useful for linux drivers).  In fact, I would probably try to remove ndiswrapper completely.


You also might need to do this:```
sudo update-initramfs -u
```

---

### Post by johnfrith on 2010-03-21
Thanks again patchwork.
 

 So I managed to de-install ndiswrapper (though I note it's mentioned in the lsmod list below), which hopefully removed the possibility that there's a conflict of drivers.  
 

 Lsmod produced:


john@john-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
joydev                 13088  0 
snd_hda_codec_si3054     5856  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  3 
snd_hda_codec          87584  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
uvcvideo               65260  0 
snd_mixer_oss          18976  1 snd_pcm_oss
videodev               43360  1 uvcvideo
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
snd_pcm                93160  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
ndiswrapper           245248  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
psmouse                57124  0 
serio_raw               6596  0 
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
led_class               5256  1 sdhci
jmb38x_ms              11300  0 
memstick               12528  1 jmb38x_ms
snd                    77096  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
i915                  252424  3 
drm                   194400  3 i915
i2c_algo_bit            7076  1 i915
r8169                  38884  0 
mii                     6368  1 r8169
intel_agp              33040  2 i915
video                  23612  1 i915
output                  3680  1 video

john@john-laptop:~$ sudo update-initramfs -u
[sudo] password for john: 
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic


Am going through the linux driver installation instructions (reproduced in post #1 of this thread), and have got as far as

[B]<Set the network related information>
1. Set manually
a. Set the IP address of your machine.

# ifconfig ethX "the IP address of your machine" [/B] 
 

 So what's my IP, DNS and gateway addresses?
 

 ifconfig currently produces:
 

 eth0      Link encap:Ethernet  HWaddr 00:90:f5:97:68:09   
           inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::290:f5ff:fe97:6809/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:654 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:712 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:458244 (458.2 KB)  TX bytes:158826 (158.8 KB) 
           Interrupt:29 Base address:0x8000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 
 

 Do I really need to go through the rest of the instructions? It's really over my head, and I'd need a lot of help to even understand the instructions.
 

 Maybe I should go out and buy Windows. :(
 

 John

---

### Post by patchwork on 2010-03-21
Your lsmod output shows the r8169 module loaded.  This was supposed to be unloaded when you installed your driver:> ohn@john-laptop:~/r8168-8.017.00$ sudo ./autorun.sh

Check old driver and unload it.
**rmmod r8169**
Build the module and install
/home/john/r8168-8.017.00/src/r8168_n.c: In function ‘rtl8168_close’:
/home/john/r8168-8.017.00/src/r8168_n.c:8732: warning: unused variable ‘ioaddr’
/home/john/r8168-8.017.00/src/r8168_n.c: In function ‘rtl_get_eeprom’:
/home/john/r8168-8.017.00/src/r8168_n.c:1806: warning: ‘ret’ may be used uninitialized in this function
[: 48: r8168: unexpected operator
Backup r8169.ko
rename r8169.ko to r8169.bak
Depending module. Please wait.
**load module r8168**

Try ```
sudo rmmod r8169 && sudo modprobe r8168
```

On the IP adressing:

eth0 is probably your wired ethernet.

Try ```
 sudo ifup -a
```
and run ifconfig again.  If all goes well, you should see eth1 or wlan0 show up in the ouput as well.

Are you running DHCP on your network?  If so, if wlan0 or eth1 becomes available, run ```
sudo dhclient wlan0 # or eth1
```

---

### Post by johnfrith on 2010-03-22
Big up to you patchwork, for helping.

Perhaps the last lsmod output was out of date, as when I tried rmmod r8169 it didn't find it. lsmod now mentions the new driver r8168, so I presume that means that it is now loaded. 
You're right about eth0. When I hover over the icon in the top line it says "Wired network connection 'Auto eth0'  active." 
"ifup -a" didn't produce any output, and didn't manage to invoke any wireless connection.
If eth0 is the wired connection, what is l0?
Not sure what DHCP is. I've not done anything to fix the IP address. It's a brand new laptop with just ubuntu 9.10 on it. The router has 4 ports, and someone else successfully uses it wirelessly.

Here is my session output.

john@john-laptop:~$ sudo rmmod r8169 
[sudo] password for john: 
ERROR: Module r8169 does not exist in /proc/modules

john@john-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
joydev                 13088  0 
snd_hda_codec_si3054     5856  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  3 
snd_hda_codec          87584  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
iptable_filter          3872  0 
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
r8168                 101556  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd_seq_midi            8192  0 
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
led_class               5256  1 sdhci
ndiswrapper           245248  0 
jmb38x_ms              11300  0 
memstick               12528  1 jmb38x_ms
psmouse                57124  0 
serio_raw               6596  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
parport                40528  2 ppdev,lp
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
i915                  252424  3 
drm                   194400  3 i915
i2c_algo_bit            7076  1 i915
intel_agp              33040  2 i915
video                  23612  1 i915
output                  3680  1 video

john@john-laptop:~$ sudo ifup -a

john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:97:68:09  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe97:6809/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3099 (3.0 KB)  TX bytes:5862 (5.8 KB)
          Interrupt:30 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by johnfrith on 2010-03-22
Just noticed that lsmod showed a line with ndiswrapper, despite me having uninstalled it. If I type in "ndiswrapper -l" it says it's not installed.

---

### Post by patchwork on 2010-03-22
lo is the internal loopback address.
DHCP is dynamic IP addressing (automatic IP assigining, instead of static IP)

I'm not a network guru, and don't know all of these commands as well as I should.  It may be worth creating a new thread specifically for bringing the wireless adapter up to get an IP address, now that the driver is loaded.  

Maybe something along the lines of:

[B]Can't Bring Wireless Interface up (driver module loaded).

[/B]I'll look some more into this, but I don't have much experience past this.
Just a note, what I tried to do with the ifup command was bring the interface up, and the dhclient command would request an IP.  This, unfortunately, did not happen and I am now out of my league...sorry I couldn't be of more help.

---

### Post by johnfrith on 2010-03-23
Thanks patchwork, I'll start a new thread as you suggest. I've been trying to get this up for a couple of months now - on my own 'till recently. Good of you to help, as I've been pretty close to giving up.

Regards, John.

---

### Post by johnfrith on 2010-03-25
[SIZE=3]Footnote: I got a cd with 32bit Ubuntu 9.10, booted from it and voila, I have wireless network, with driver r8168 automatically loaded! 

After 2 months of trying to get it to work, it looks like it some sort of incompatability with 64bit Ubuntu. It seems that the 64bit version loads r8167b instead of r8168.

Anyone know where I report a bug (that should be easy to fix)?

[/SIZE]

---

