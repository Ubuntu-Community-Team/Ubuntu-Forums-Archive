---
title: "wireless adapater N150 install"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by feralfinds on 2011-03-23
hello! thanks for reading. 
 
i am running ubuntu 9.10 on a dell latitude d610 laptop. 
i'd love to use wireless, and bought a netgear n150 usb adapter for another laptop, and now would like to use it with ubuntu...
 
i found a thread for my specific question, but i am afraid that my *extremely* limited knowledge leaves me needing a bit more help. 
 
thread is here: [http://ubuntuforums.org/showthread.php?t=1447592&highlight=wireless+netgear+150](http://ubuntuforums.org/showthread.php?t=1447592&highlight=wireless+netgear+150)
 
basically, i read the advice, and wasn't sure where to start. 
 
i also read that i should probably upgrade to a newer version of ubuntu..should do this first? 
 
many thanks, jennifer

---

### Post by grahammechanical on 2011-03-23
In a few more weeks we will see the result of 18 months development of Ubuntu since 9.10 was released. It may be that issues with your type of hardware have been fixed. Then, again may be not. This is why some recommend upgrading to the latest version. It is your choice.

The steps are the same for every wireless device or adapter. If it works from the moment your plug it in and load up Ubuntu then you are happy (for a little while at least). If it does not work then you have to follow certain steps to identify the problem.

Do you know how to establish a wireless connection when Ubuntu recognizes the wireless adapter? Is it possible to get a connection using ethernet cable? You will need this if Ubuntu does not recognize your wireless adapter.

Here is a link to the community documentation. Just in case you have problems.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

If you go to System>Help and Support>Internet and Networks you will find information on how to proceed.

Other than this, I suggest that you plug the thing in and boot the machine and see what happens. If getting it working proves too difficult you can ask for help to get around the specific problem. Please provide information about what is going wrong. It will give us a clue.

Regards.

---

### Post by feralfinds on 2011-03-23
grahammechanical
 
thank you! 
 
i am hooked to the internet through ethernet currently. 
and, 
i made an assumption that this would be an arduous task (the wireless adapter) 
as i was having major issues previsouly. definitely, i should have played around a bit more! 
 
but, once i have finished updating the system to 10.0 (running right now), 
i will see if there are more specific questions i can ask regarding the wireless. 
and maybe, it will just work.....
 
thanks! jennifer

---

### Post by jennyyin on 2011-03-24
hello again! 

i have upgraded my system to 10.04 LTS, 
and 
the wireless adapter i have is not automatically read. 
adapter: Netgear N150 Wireless USB (WNA1100) 
(i should mention that, i have not yet used this adapter at all on a linux computer....) 

i found the following thread regarding this specific device, but i don't understand all the steps: 
[http://ubuntuforums.org/showthread.php?t=1447592](http://ubuntuforums.org/showthread.php?t=1447592)

i did poke around, and see that ndiswrapper is installed on my system.

the following portion of the thread i refer to above seems most relevant (to my uninformed eyes.) 
i have the driver cd in my computer now, but i am unsure about where to go from here? 

"I use a netgear WPN111 at my studio - not same as yours but could  work...ndisgtk is available in the synaptic and is very easy to use.  When ndisgtk asks you for the .inf file it needs to come with another  file, .sys or something, in the same directory. I'm not sure of the  exact name as I'm not at that computer at the moment. If it's not clear  which one you need, just copy the entire folder  C:\Program_files\NETGEAR\WNA110\Driver\ from windows to your ubuntu  partition, there should only be about 45 or 5 files in it."  (quoted from thread i referred to above.) 


also:
here is what i have done/looked at, based on suggestions on this forum: 

entered lsusb into terminal: my computer is reading the adapter: 
bus 001 Device 002: ID 0846:9030 NetGear, Inc. 

entered nm-tool into terminal : the wireless adapter is not connecting: 
Sate: unavilable

if anyone is interested in offering ideas, i am definitely interested in trying them! 
please just let me know what additional info is needed, 

many thanks, 
jennifer

---

### Post by Hippytaff on 2011-03-24
Thats pretty much it. If your using the windows driver (has to be XP driver) I'd use Ndisgtk (sudo apt-get it). Put the .inf and .sys files in a folder on your desktopn. Open ndisgtk, point it at the .inf file and you should be good to go

---

### Post by jennyyin on 2011-03-24
hippytaff,
thanks
and
i attempted your suggest:

I'd use Ndisgtk (sudo apt-get it)

and got this message in the terminal:

E: invalid operation ndisgtk

i know ndisgtk is installed, as i just checked the package manager....

what am i doing wrong? thanks! 
jennifer

---

### Post by Hippytaff on 2011-03-24
Sorry, I wasn't at all clear. if you have it installed open it by typing```
ndisgtk
```

---

### Post by jennyyin on 2011-03-24
duh thanks, i should have gotten that myself.

i typed in ndisgtk and it came back with an error message: 
root or sudo privileges required

usually, i am just prompted for a root passcode when it is needed. how to proceed? 

thanks!
 j

---

### Post by Hippytaff on 2011-03-24
try```
gksudo ndisgtk
``` or just```
sudo ndisgtk
``` though the first one is probably the correct way to open it :-)

---

### Post by jennyyin on 2011-03-24
ok! so the gksudo command worked just fine

but now i am confused about my disk!! 
i dont see any .inf .sys files....

sorry to be such a dork! jennifer

---

### Post by Hippytaff on 2011-03-24
No probs. You need to open the disc and extract the inf and sys files to a folder on your desktop (or somewhere I always use th edesktop for this kind of stuff)

---

### Post by jennyyin on 2011-03-24
is it a problem if there is only an .inf file, no .sys? 
i looked everywhere on the disk.....

---

### Post by jennyyin on 2011-03-24
it seems to have worked, driver installed......i'll play around a bit more and report back. thanks!

---

### Post by Hippytaff on 2011-03-24
Ok...let us know how it goes.

---

### Post by jennyyin on 2011-03-24
ok, it went, not so well! 
the driver was installed, but when
 i look at by doing the gksudo ndisgtk,
it has a nice big red x over the icon for the driver, and says "Invalid Driver". 

thanks !

---

### Post by Hippytaff on 2011-03-24
you need the XP driver...and obviously the right one for your wireless device.

---

### Post by jennyyin on 2011-03-24
thanks...its definitely the right one for this device. and, the box states it is for windows 7, xp, and vista....
i'll look around a little more and see if i can try something else.

---

### Post by Hippytaff on 2011-03-24
Can I see the full output of```
lspci
``` and ```
lshw -C Network
```

Edit ->actually can you run and post the wireless-results.txt of the attached script? If you have trouble running it let me know...some people don't like running scripts and if you don't want to thats fine...but there is nothing malicious in the script.

---

### Post by Hippytaff on 2011-03-24
And I've just found [this thread]("http://ubuntuforums.org/showthread.php?t=1594592") which looks promising

---

### Post by jennyyin on 2011-03-25
Edit ->actually can you run and post the wireless-results.txt of the attached script? If you have trouble running it let me know...some people don't like running scripts and if you don't want to thats fine...but there is nothing malicious in the script.

hey hippytaff,

thanks for your instructions, but i am having trouble. 
i have never run a script before, so i read elsewhere on the forum how to do so....but no luck. 
here is the thread i used for help: 
[http://ubuntuforums.org/archive/index.php/t-83910.html](http://ubuntuforums.org/archive/index.php/t-83910.html)

i saved the file you attached to my desktop first...

if you could let me know how to do this, i would much appreciate it! 

thanks, jennifer

---

### Post by Hippytaff on 2011-03-25
ok....right click on the file and in permissions choose executable or open a terminal and cd to the Desktop```
cd Desktop
``` Capital D ;-) then do```
chmod +x wireless_script.sh
``` then do ```
./wireless_script.sh
``` and press enter. It will generate a wireless-results.txt. If you can post that in code tags that would be awsome :-)

---

### Post by wep940 on 2011-03-25
Try getting the .inf and .sys for Atheros ath9k driver.  When I looked on the net for the manufacturer and device (the xxxx:xxxx that shows on your lsusb) it comes back as an Atheros device.  Be sure to find XP only files if at all possible.  Also, assuming you just downloaded the 32-bit version of Ubuntu (the default download) then the driver must be 32-bit.  I question whether a driver that works in Windows 7 is actually downward compatible with 32-bit Windows XP - that's why I'd specifically look for an XP driver.

---

### Post by wep940 on 2011-03-25
Also, you may want to look at this thread:
 
[http://ubuntuforums.org/showthread.php?p=9553406#post9553406](http://ubuntuforums.org/showthread.php?p=9553406#post9553406)

---

### Post by jennyyin on 2011-03-26
ok! i am pasting results below, appearing exactly as it appears in the .txt file. 
jenn


************************************
        Ubuntu release 
************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

************************************
        Kernel
************************************

Linux jenno 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux

************************************
        pci wireless devices
************************************


************************************
        usb wireless devices
************************************


************************************
        List of network devices
************************************

  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:b8:d3:49
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.29a ip=10.0.0.15 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:dfdf0000-dfdfffff

************************************
          List of drivers
************************************

Module                       Size  Used by
isofs                        29250  1 
udf                           78785  0 
crc_itu_t                    1371  1 udf
binfmt_misc               6587  1 
fbcon                       35102  71 
tileblit                         2031  1 fbcon
font                           7557  1 fbcon
bitblit                         4707  1 fbcon
softcursor                1189  1 bitblit
vga16fb                  11385  0 
vgastate                   8961  1 vga16fb
snd_intel8               25652  3 
snd_ac97_codec 100646  1 snd_intel8x0
ac97_bus                 1002  1 snd_ac97_codec
snd_pcm_oss        35308  0 
snd_mixer_oss      13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy     1338  0 
joydev                      8740  0 
snd_seq_oss         26722  0 
snd_seq_midi           4557  0 
snd_rawmidi           19056  1 snd_seq_midi
snd_seq_midi_event6003  2 snd_seq_oss,snd_seq_midi
pcmcia                    30784  0 
snd_seq                  47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_even
snd_timer                19098  2 snd_pcm,snd_seq
snd_seq_device      5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                   1793  0 
snd                         54180  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket         20408  1 
i915                       287458  2 
rsrc_nonstatic        10015  1 yenta_socket
dell_laptop                6888  0 
psmouse                63245  0 
drm_kms_help      29329  1 i915
soundcore              6620  1 snd
intel_agp               24375  2 i915
dcdbas                   5422  1 dell_laptop
serio_raw               3978  0 
pcmcia_cor         32964  3 pcmcia,yenta_socket,rsrc_nonstatic
drm                    162345  3 i915,drm_kms_helper
snd_page_alloc     7076  2 snd_intel8x0,snd_pcm
ppdev                    5259  0 
agpgart                31724  2 intel_agp,drm
i2c_algo_bit           5028  1 i915
video                   17375  1 i915
parport_pc          25962  1 
output                    1871  1 video
lp                           7028  0 
parport                32635  3 ppdev,parport_pc,lp
tg3                     109324  0 

************************************
           network info
************************************

eth0      Link encap:Ethernet  HWaddr 00:14:22:b8:d3:49  
          inet addr:10.0.0.15  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feb8:d349/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:219368238 (219.3 MB)  TX bytes:9551603 (9.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


************************************
 Wireless specific network info
************************************

lo        no wireless extensions.

eth0      no wireless extensions.

************************************
 Rfkill Blocks
************************************


************************************
Fri Mar 25 17:47:38 EDT 2011

---

### Post by jennyyin on 2011-03-26
wep940,
thanks for your thoughts on this! 

i am running the 32 bit ubuntu, that is correct. the wireless device box says it is compatible with both 32 and 64 bit.....

going to check out the thread you posted now, thanks, 
jennifer

> **wep940 said:**
> Try getting the .inf and .sys for Atheros ath9k driver.  When I looked on the net for the manufacturer and device (the xxxx:xxxx that shows on your lsusb) it comes back as an Atheros device.  Be sure to find XP only files if at all possible.  Also, assuming you just downloaded the 32-bit version of Ubuntu (the default download) then the driver must be 32-bit.  I question whether a driver that works in Windows 7 is actually downward compatible with 32-bit Windows XP - that's why I'd specifically look for an XP driver.

---

### Post by jennyyin on 2011-03-26
hey hippytaff! 

i just noticed that, when i posted my results, the format got all ****** up and it is 
probably a nightmare to read. 

i realise that when you asked me to use code tags, it was to make it readable, etc.
but, i apologise, i apparently didn't figure that out properly. 
i'll mess around and see if i can do it right, this time. 
thanks for your patience! 
jenn

> **Hippytaff said:**
> ok....right click on the file and in permissions choose executable or open a terminal and cd to the Desktop```
cd Desktop
``` Capital D ;-) then do```
chmod +x wireless_script.sh
``` then do ```
./wireless_script.sh
``` and press enter. It will generate a wireless-results.txt. If you can post that in code tags that would be awsome :-)

---

### Post by Hippytaff on 2011-03-26
```
************************************
        Ubuntu release 
************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

************************************
        Kernel
************************************

Linux jenno 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux

************************************
        pci wireless devices
************************************


************************************
        usb wireless devices
************************************


************************************
        List of network devices
************************************

  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:b8:d3:49
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.102 duplex=full firmware=5751-v3.29a ip=10.0.0.15  latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:dfdf0000-dfdfffff

************************************
          List of drivers
************************************

Module                       Size  Used by
isofs                        29250  1 
udf                           78785  0 
crc_itu_t                    1371  1 udf
binfmt_misc               6587  1 
fbcon                       35102  71 
tileblit                         2031  1 fbcon
font                           7557  1 fbcon
bitblit                         4707  1 fbcon
softcursor                1189  1 bitblit
vga16fb                  11385  0 
vgastate                   8961  1 vga16fb
snd_intel8               25652  3 
snd_ac97_codec 100646  1 snd_intel8x0
ac97_bus                 1002  1 snd_ac97_codec
snd_pcm_oss        35308  0 
snd_mixer_oss      13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy     1338  0 
joydev                      8740  0 
snd_seq_oss         26722  0 
snd_seq_midi           4557  0 
snd_rawmidi           19056  1 snd_seq_midi
snd_seq_midi_event6003  2 snd_seq_oss,snd_seq_midi
pcmcia                    30784  0 
snd_seq                  47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_even
snd_timer                19098  2 snd_pcm,snd_seq
snd_seq_device      5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
dell_wmi                   1793  0 
snd                         54180  15  snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_   oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti  mer,snd_seq_device
yenta_socket         20408  1 
i915                       287458  2 
rsrc_nonstatic        10015  1 yenta_socket
dell_laptop                6888  0 
psmouse                63245  0 
drm_kms_help      29329  1 i915
soundcore              6620  1 snd
intel_agp               24375  2 i915
dcdbas                   5422  1 dell_laptop
serio_raw               3978  0 
pcmcia_cor         32964  3 pcmcia,yenta_socket,rsrc_nonstatic
drm                    162345  3 i915,drm_kms_helper
snd_page_alloc     7076  2 snd_intel8x0,snd_pcm
ppdev                    5259  0 
agpgart                31724  2 intel_agp,drm
i2c_algo_bit           5028  1 i915
video                   17375  1 i915
parport_pc          25962  1 
output                    1871  1 video
lp                           7028  0 
parport                32635  3 ppdev,parport_pc,lp
tg3                     109324  0 

************************************
           network info
************************************

eth0      Link encap:Ethernet  HWaddr 00:14:22:b8:d3:49  
          inet addr:10.0.0.15  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feb8:d349/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:219368238 (219.3 MB)  TX bytes:9551603 (9.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


************************************
 Wireless specific network info
************************************

lo        no wireless extensions.

eth0      no wireless extensions.

************************************
 Rfkill Blocks
************************************


************************************
Fri Mar 25 17:47:38 EDT 2011
```

I've amended the script to automatcally include code tags now. I'm a bit pushed for time but it looks as though the wireless device is not being recognised for some reason...might be worth giving ndisgtk another go. sorry to be brief...not much time today :-)

---

### Post by jennyyin on 2011-03-26
not a problem, the time you have already spent is very helpful. 
i think i will look more closely at the other poster's suggestions and the thread he linked to, as that looks like it speaks specifically about ubuntu and the device i have. 

thanks for all your help, !!! 
jenn

---

### Post by walt.smith1960 on 2011-03-27
I have this adapter. I've used it on 10.04 & 10.10 64 bit.  The simple and reliable (for me at least) way is to get this installer from sourceforge:

[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)  The installation is a two step process. Running the .deb file installs the installer.  Then go to Applications -> system tools and find ath9K_htc-installer.  Click on it and wait.  If you upgrade the kernel you'll lose the wireless adapter. Rerun the ath9k installer and you're back in business.

I don't know if this will conflict with what you've already done with NDISwrapper or not. I did NDISwrapper initially but the adapter seemed unstable so I uninstalled NDISwrapper & did the installer from sourceforge. The good news is that Natty recognizes my WNA1100 without any tinkering, run the LiveCD and it's there :D.

Edit: If you're using 10.10, you need the updated installer.  Here's the one for Maverick, I expect it'd work in Lucid as well.  [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer-Ubuntu%20Maverick%2010.10-fixed/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer-Ubuntu%20Maverick%2010.10-fixed/)

---

### Post by jennyyin on 2011-03-27
hey walt.smith...
thanks so much for this information! im working on understanding it, and possibly getting some assistance. 
looks very promising though! 
jennifer

---

### Post by matt_symes on 2011-03-28
Hi

> i'm a bit pushed for time but it looks as though the wireless device is not being recognised for some reason...

IIRC, that generally happens when the driver is not loaded for some reason. I would ditch ndswrapper if possible and try to find native drivers.

[http://wireless.kernel.org/en/users/Drivers](http://wireless.kernel.org/en/users/Drivers)

Kind regards

---

### Post by feralfinds on 2011-03-31
((sorry about switching user names!))

hey walt,
your suggestions worked! i did have to get some real-time help from a local ubuntu fellow. 

i clean-installed 10.10 maverick, then the appropriate installer from here: 
[http://sourceforge.net/projects/ath9...2010.10-fixed/]("http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer-Ubuntu%20Maverick%2010.10-fixed/")

didn't take any more messing around after that! 

many thanks, and thanks to everyone for the assistance. 

jennifer

\\:D/

---

### Post by walt.smith1960 on 2011-04-01
> **feralfinds said:**
> ((sorry about switching user names!))

hey walt,
your suggestions worked! i did have to get some real-time help from a local ubuntu fellow. 

i clean-installed 10.10 maverick, then the appropriate installer from here: 
[http://sourceforge.net/projects/ath9...2010.10-fixed/]("http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer-Ubuntu%20Maverick%2010.10-fixed/")

didn't take any more messing around after that! 

many thanks, and thanks to everyone for the assistance. 

jennifer

\\:D/

Thanks Jenfifer.  The real kudos go to Vagrale13 who created that .deb package.  It really does help we noobs.

---

### Post by Need_your_Advice on 2011-11-13
I have tried unsuccessfully to get the Net Gear Wireless USB n150 WNA110 working.

I am using Linux Mint 9 'Isadora' whice, I am told, is like Ubuntu 10.04 'Lucid'.
kernel
  Code:
            uname -a
            Linux horace-laptop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 GNU/Linux

I downloaded ath9k_htc-installer_1-0-3.deb
Installed it and ran it (see attached Notes.gz)
Rebooted my PC
Inserted the Netgear Wireless USB n150 wna1100

No light, Nothing!

Please tell me what, if anything, I am doing wrong and help me get it working.

NYA

---

