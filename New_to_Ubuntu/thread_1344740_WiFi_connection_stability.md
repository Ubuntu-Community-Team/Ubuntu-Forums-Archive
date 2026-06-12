---
title: "WiFi connection stability"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-12-03
I recently upgraded to karmic, and after fixing a few minor issues, all seemed well, Until i went to the library and used their WiFi...after trying to connect for about 30 minutes(wifi problem, not computer) i manage to start browsing, but every 10 minutes...almost without fail..i load a page, and it connects, reads, then waits...for about 5 minutes, then continues...now is this just another connection issue from the libraries side, or more of a computer issue.

Im using an NC10 samsung netbook running karmic.

---

### Post by ukripper on 2009-12-03
symptoms of an atheros card present on ubuntu 9.10.

can you run this command and post output of below command:
```
lspci
```

---

### Post by JamesParnell on 2009-12-03
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

---

### Post by ukripper on 2009-12-03
This problem can occur for many reasons.

let us see if your library router supports ipv6. In firefox do this if your network is not slow anymore then it will prove ipv6 was the reason. We go from there. Follow below steps:

Disabling ipv6 in Firefox

1. Type about:config in your address entry bar (in firefox)
2. Type "ipv6" in the filter
3. Change the value of "network.dns.disableIPv6" to true 

and start browsing

---

### Post by JamesParnell on 2009-12-03
i'll give it a shot. my battery is pretty much dead, so if it doesnt happen before it dies, i probably wont have an update until tomorrow
 
EDIT: don't know if this makes a difference, but under connection setting for this AP, under ivp6 or whatever it is, it is set to "ignore"

---

### Post by JamesParnell on 2009-12-03
Nope....still doing it.

---

### Post by ukripper on 2009-12-03
so ipv6 is ruled out. Now let us look at your iwconfig;
post output of below:
```
iwconfig
```

```
lshw -C network
```

have you got any other conection you can try home or office? This will isolate our problem area.

---

### Post by JamesParnell on 2009-12-03
IWCONFIG

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"DCCWireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:56:CE:0E:01   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



LSHW -C NETWORK


WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2c:87:ac:56
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.9.182 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:fa:7d:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:26 memory:f0200000-f0203fff ioport:2000(size=256)

---

### Post by JamesParnell on 2009-12-03
and my battery is pretty much dead...critical. any further commands can probably 
be crammed in after i reboot it...maybe. if not, it will be later on tonight

---

### Post by ukripper on 2009-12-03
i think most probably it is your library conection playing up. How is your signal strength? Can you ask if soemone else is having same problem in your library?

---

### Post by JamesParnell on 2009-12-03
Sitting about 10m away from the router, it is about 86-90%...even when it is hanging, still stays on 86-90% I havent asked anyone before. and most people dont bother using their portables and such anymore*****, as 9 times out of 10 it takes about 30 mintutes to connect (im usually the one thats lucky).
 
*either that or i never see them

---

### Post by ukripper on 2009-12-03
in terminal can you ping and post output here:
```
ping -c 20 ubuntuforums.org
```

this will ping ubuntuforums 20 times and return or drop packets.

---

### Post by JamesParnell on 2009-12-03
It's dead now(netbook), i will be able to do it first thing tomorrow when i come back to the library.

---

### Post by ukripper on 2009-12-03
> **JamesParnell said:**
> as 9 times out of 10 it takes about 30 mintutes to connect (im usually the one thats lucky).


Doesn't that mean library conenction is at fault as only you manage to connect to it? Has anyone complained to them?

---

### Post by JamesParnell on 2009-12-03
it comes and goes...sometimes people get on first time..others dont get on at all. ive had it happen to myself many times, So i know its not just a windows thing. I have told the library about it and all they said was "take one of these sheets", which showed you how to connect to it in XP and Vista, via start > connect to...etc (which is, 1: not helpful to me on linux, 2: means they are totally unaware of what im telling them in the first place)..and as they have no access to the WiFi whatsoever, all they can do is give out sheets and look at the box to see if the "little blue light is on"...

---

### Post by ukripper on 2009-12-03
> **JamesParnell said:**
> it comes and goes...sometimes people get on first time..others dont get on at all. ive had it happen to myself many times, So i know its not just a windows thing. I have told the library about it and all they said was "take one of these sheets", which showed you how to connect to it in XP and Vista, via start > connect to...etc (which is, 1: not helpful to me on linux, 2: means they are totally unaware of what im telling them in the first place)..and as they have no access to the WiFi whatsoever, all they can do is give out sheets and look at the box to see if the "little blue light is on"...

what router they have? it is definitely library connection problem nothing to do with your computer.

---

### Post by JamesParnell on 2009-12-03
> **ukripper said:**
> what router they have?
 
i have no idea, and they wont tell me (why????)..i can see it mounted on the wall..i cant see a make/model, but it's dark (navyish) blue and has two aerials coming out the top.
 
EDIT: im gunna take a stab and say some form of Belkin

---

### Post by ukripper on 2009-12-03
are all lights up as green and no orange?

---

### Post by JamesParnell on 2009-12-03
I cant see the lights on it, they are underneath. all i know is they look for a blue light to make sure its online

---

### Post by ukripper on 2009-12-03
ok. Do you use a WEP key or WPA/WPA2 keys to access it?

---

### Post by JamesParnell on 2009-12-03
im actually going to say it might be a netgear..they have a lot of blue things

---

### Post by JamesParnell on 2009-12-03
Its an open network.

---

### Post by ukripper on 2009-12-03
> **JamesParnell said:**
> Its an open network.

that could explain one reason. They might have limted users or might have set priorities therefore, people who not even in library may access from outside atleast 50 m away depending on the router range. hence the slowness. Next time when you are online with your laptop we will see how many are actually connected to your router and are on same network as you.

---

### Post by JamesParnell on 2009-12-03
ok, i will probably be online from about 10-11 tomorrow.

Edit: just asked after the changover...its a cysco systems router

---

### Post by JamesParnell on 2009-12-04
ook then..new day, lets start it with a bump

---

### Post by ukripper on 2009-12-04
ok let's try nbtscan and see if router gives you any decent output to gather how many ips are connected to it.

I assume your ip is still somewhere 192.168.9.x
```
sudo apt-get install nbtscan
```

```
nbtscan 192.168.9.1/24
```

Hope they haven't disabled netbios status query.

---

### Post by JBAlaska on 2009-12-04
If it's a navy blue router, it's prolly a Linksys (Now by Cisco). What is the SSID that shows up "linksys"? (could the collage IT department be that stupid....)

I'm guessing its a traffic shaping / blocking  tool that's causing the problem, like **Cisco NAC Appliance (formerly Cisco Clean Access)**.

[B]When deployed, Cisco NAC Appliance provides the following benefits:
[/B]
* Recognizes users, their devices, and their roles in the network. This first step occurs at the point of authentication, before malicious code can cause damage.

* Evaluates whether machines are compliant with security policies. Security policies can include specific antivirus or antispyware software, OS updates, or patches. Cisco NAC Appliance supports policies that vary by user type, device type, or [COLOR="Red"]operating system[/COLOR].

* **Enforces security policies by blocking, isolating, and repairing noncompliant machines.**

[COLOR="Red"]noncompliant machines = Linux![/COLOR]

Solution, burn down the library!........J/K

---

### Post by ukripper on 2009-12-04
> **JBAlaska said:**
>  What is the SSID that shows up "linksys"? 



SSID is usually changed, they won't leave it as default if they a re using NAC.

---

### Post by JamesParnell on 2009-12-04
IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.9.0    Sendto failed: Permission denied
#192.168.9.255    Sendto failed: Permission denied

---

### Post by ukripper on 2009-12-04
> **JamesParnell said:**
> IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
192.168.9.0    Sendto failed: Permission denied
#192.168.9.255    Sendto failed: Permission denied

yes they are using all secured router. Only way forward i can think is you need to find out if anyone is having the same problem there on windows/mac/linux. social engineering seems to be key here rather than technical assessment.

---

### Post by JamesParnell on 2009-12-04
a guy came in with his mac the other day, he seemed to have no problems....it not very often you see people in here anymore with portables.

---

### Post by ukripper on 2009-12-04
Were you having the same problem the other day the mac guy was around?

---

### Post by JamesParnell on 2009-12-04
yeah..

Today, i was connected to the network when i turned on the netbook, but still froze up after about 2 minutes...either i havent noticed it ...or it doesnt seem to be doing it much today(about twice in 30minutes)

---

### Post by JamesParnell on 2009-12-04
spoke too soon, its just done it

---

### Post by ukripper on 2009-12-04
i wished at this point you had dual boot windows setup, where you could tell these librarians that they got to have a look at the connection being flimsy. 

Alibi as it is, they would ignore ubuntu or any other distro as it ain't (in their eyes) mainstream.

---

### Post by JamesParnell on 2009-12-04
i told them yeterday... and i mentioned that i didnt use window..the woman i spoke to didnt even know what i was talking about -_-.

I guess i'll just have to live with it..unles windows can be booted in via USB..in which case i can do that now.

---

### Post by ukripper on 2009-12-04
personally i have never used windows in usb. just quick google search gave me this [http://articles.techrepublic.com.com/5100-22_11-5928902.html](http://articles.techrepublic.com.com/5100-22_11-5928902.html). It has been longtime for me to play  with windows. My windows skills are bit rusted now.

---

### Post by JamesParnell on 2009-12-04
i dont use windows and this explanation is for windows user to be able to copy files neded for the installation from the boot file in windows

---

### Post by JamesParnell on 2009-12-04
i will just talk to someone that knows what they are doing in the library later on, and tell them that their network is s*** for people that have a brain and dont use windows

---

### Post by JamesParnell on 2009-12-04
thanks for all your help guys. jut a shame it didnt get fixed

---

### Post by JamesParnell on 2009-12-04
Library centre manager phone call to the IT dept.


result of the phone call: "So bacially it's his machine that has the problem and there is nothing we can do about it"


that is what she said, word for word.

---

### Post by ukripper on 2009-12-04
Can you download ubutnu 9.04 live cd and boot your laptop with it and connect the wifi from within live environment. And let us know if you are having the same issue?

---

### Post by JamesParnell on 2009-12-04
ok i will. give me a few minutes. i havent got the iso on me, i will have to redownload it

---

### Post by ukripper on 2009-12-04
Before you do that i'd like you to try this [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
 - i think ubuntu provided prop. drivers are also causing problem with your **atheros chipset 5001**. Try madwifi drivers instead. it may sort any connection problem from your side.

i have seen number of posts in past relating to atheros chipset stability problems too. therofre, i won't be surprised if problem is fixed following the link above. So combination of WICD and MAdwifi is good. only problem would be kernel updates would want you to re-install driver again.

---

### Post by JamesParnell on 2009-12-04
ok i will try that

---

### Post by ukripper on 2009-12-04
Please read that whole thread (in the link) before trying anything.

---

### Post by JamesParnell on 2009-12-04
i read it all, and tried it, no luck..now i have no connectivity via WiFi or mobile modem.

---

### Post by ukripper on 2009-12-04
post output of follwoing:
```
lshw -C network
```

```
lsmod
```

```
iwconfig
```

---

### Post by JamesParnell on 2009-12-04
this might take a while as i will have to type the result

---

### Post by JamesParnell on 2009-12-04
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       logical name: eth0
       version: 13
       serial: 00:13:77:fa:7d:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:26 memory:f0200000-f0203fff ioport:2000(size=256)
 
LSMOD
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
usb_storage            52576  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
joydev                 10272  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  11856  2 
samsung_backlight       2244  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
psmouse                56500  0 
serio_raw               5280  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
sky2                   46560  0 
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
IWCONFIG
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

---

### Post by JamesParnell on 2009-12-04
im just putting the iso on stick now..i couldnt find the 9.04 iso, but i'd rather have bad acces than no access, so im downloading 9.10 again just incase we cant sort this new and exciting problem

---

