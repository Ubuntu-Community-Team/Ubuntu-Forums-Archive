---
title: "(Asus PCE-AC68) How to achieve Wireless-AC speeds"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by Harp on 2014-04-23
I've been searching for a solution to this for a while and (surprisingly) haven't come up with anything. If anyone has a link, that would be cool too.

I'm currently running 14.04, though this problem has persisted for me across various releases and wireless cards, both laptop and desktop.

The problem is that I just can't seem to get Wireless-AC speeds out of Ubuntu. For example, the card I'm using right now, the Asus PCE-AC68 ([http://www.newegg.com/Product/Product.aspx?Item=N82E16833320173](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320173)), is usable with the proprietary bcmwl-kernel-source driver installed via Software & Updates > Additional Drivers, but it is EXTREMELY slow. In Windows, this card downloads from my sftp server at about 50MB/s. In Ubuntu, it's downloading at about 3MB/s. 

Some info:
```
lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
```

```
iwconfig
wlan0     IEEE 802.11abg  ESSID:"OMITTED"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: OMITTED   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

I'm not very familiar with this sort of thing, but from iwconfig, it seems that it's trying to use the card as 802.11abg, rather than 802.11ac, which would be consistent with the speeds I'm seeing.

I have tried using ndiswrapper to install the latest windows drivers from Asus. The Windows 7/8/8.1  drivers don't seem to work at all and the Windows XP driver works only partially (I can see my network available but it will not connect, just keeps asking me for the password over and over).

Any suggestions for how to get this working at optimum efficiency would be greatly appreciated. I'm afraid to say that Ubuntu is not very usable to me unless I can increase the wireless speeds, 50MB/s vs 3MB/s is just not an option.

Thank you.

---

### Post by chili555 on 2014-04-23
> wlan0bcmwl-kernel-source usually uses eth1, not wlan0. Which driver are you using?```
lsmod
```

---

### Post by Harp on 2014-04-23
```
lsmod
Module                  Size  Used by
joydev                 17381  0 
snd_hda_codec_hdmi     46207  1 
bnep                   19624  2 
rfcomm                 69160  8 
btusb                  32412  0 
hid_logitech_dj        18581  0 
bluetooth             395423  22 bnep,btusb,rfcomm
usbhid                 52616  0 
hid                   106148  3 usbhid,hid_logitech_dj
binfmt_misc            17468  1 
ip6t_REJECT            12939  1 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18894  8 
nf_defrag_ipv6         34768  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
xt_LOG                 17717  10 
xt_limit               12711  13 
xt_tcpudp              12884  26 
xt_addrtype            12635  4 
nf_conntrack_ipv4      15012  8 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  16 
mxm_wmi                13021  0 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 21798  1 nf_nat_ftp
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack           96976  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
iptable_filter         12810  1 
aesni_intel            55624  0 
ip_tables              27239  1 iptable_filter
aes_x86_64             17131  1 aesni_intel
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_hda_codec_realtek    61438  1 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
snd_hda_intel          52355  10 
serio_raw              13462  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
lib80211_crypt_tkip    17619  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
wl                   4207846  0 
lpc_ich                21080  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
cfg80211              484040  1 wl
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
fglrx                8815330  183 
amd_iommu_v2           19054  1 fglrx
mei_me                 18627  0 
mei                    82274  1 mei_me
ppdev                  17671  0 
parport_pc             32701  1 
mac_hid                13205  0 
intel_smartconnect     12619  0 
wmi                    19177  1 mxm_wmi
video                  19476  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ahci                   25819  2 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169

```

A quick look in /usr/src/ shows the driver as "bcmwl-6.30.223.141+bdcom"

---

### Post by chili555 on 2014-04-24
You are using the latest version of bcmwl-kernel-source and I understand it is supposed to support AC speeds. This is the first time I've ever seen the interface enumerated wlan0. You seem to have no conflicting modules loading.

Frankly, AC is so new that I have seen but a single case confirming those speeds in Linux; unfortunately, on an Intel device. Frankly, the answer I have for you as to how to achieve AC speeds is that I don't know, and I doubt anyone here is more experienced in wireless and particularly Broadcom. I encourage comment from my colleagues if they have better ideas.

Having said that, please be aware that the Broadcom driver is not an Ubuntu creation; it is written by Broadcom. That means that if you decide to try Mint or Suse or Fedora, you will find the same problem because we all only get the driver that Broadcom provides.

You can certainly try to fine-tune the router's settings. You can also file a bug report: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) 

I wish I had a better report.

---

### Post by Harp on 2014-04-24
Well, I've pretty much exhausted my troubleshooting abilities on this.

Here is a breakdown of exactly what I've tried, in case it will give anyone some new ideas or better luck (note: please read through before attempting, these methods were unsuccessful for me. You will also need to connect your pc to the internet via ethernet):

1) bcmwl-kernel-source method

Press the "Super" key and enter "Additional Drivers"

It searches automatically and finds the broadcom driver for me. I select it, click apply, reboot.

This method works. But as stated in my original post, my wireless speeds are severely limited, nowhere near my card's wireless-ac capabilities.

> **chili555 said:**
> bcmwl-kernel-source usually uses eth1, not wlan0.

I remember thinking this was a bit strange as on a different laptop I have it used eth1, but I have purged and reinstalled bcmwl-kernel-source a number of times now and it always uses wlan0 for me.

I do not know how to investigate this further.

2) Ndiswrapper method

Downloaded latest Windows driver from Asus ([http://www.asus.com/Networking/PCEAC68/HelpDesk_Download/](http://www.asus.com/Networking/PCEAC68/HelpDesk_Download/))

```
cd <download directory>
unzip <driver>.zip
cd <unzipped directory>
unshield <filename>.cab
```

```
sudo apt-get install ndiswrapper-common ndiswrapper-source ndiswrapper-dkms ndiswrapper-utils-1.9 ndisgtk
sudo ndisgtk
```

Click "Install New Driver"

Navigate through <unzipped directory> until you find the suitable .inf file (in my case, I had the best luck with the Windows XP version).

After the driver is installed:

```
sudo vim /etc/modprobe.d/blacklist.conf
```

Add "blacklist wl" to the end of the file.

```
sudo reboot
```

This method would list my wireless network as available but would not connect, asking me repeatedly for the password. I had a look around in the config file (/etc/ndiswrapper/bcmwl5/14E4:43A0.5.conf) to see if I could see any obvious problems. Since I'm not an expert on this, maybe someone else could have a look:

```
sys_files|bcmwl564.sys 
NdisVersion|0x50001
Environment|1
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
driver_version|ASUS,02/05/2014, 6.30.223.228
BusType|5
SlotNumber|01
NetCfgInstanceId|{28022A01-1234-5678-ABCDE-123813291A00}

11HNetworks|1
11NPreamble|-1
antdiv|-1
ApCompatMode|0
assoc_recreate|1
AssocRoamPref|0
BadFramePreempt|0
band|0
BandPref|0
BandwidthCap|1
Beamforming|0
BtAmp|1
BTCoexist|3
ccx_rm|1
ccx_rm_limit|300
Chanspec|11
DriverDesc|NDIS Network Adapter
EFCEnable|0
EnableAutoConnect|0
EnableSoftAP|0
frag|2346
FrameBursting|1
HelpText|The ASUS 802.11 Network Adapter provides wireless local area networking.
IBSSAllowed|1
IBSSGProtection|2
IBSSLink|0
IBSSMode|5
Interference_Mode|-1
Intolerant|0
ledbh0|-1
ledbh1|-1
ledbh2|-1
ledbh3|-1
ledblinkfast|-1
ledblinkmed|-1
ledblinkslow|-1
leddc|0
LockWlSettings|0
LOM|0
Managed|1
MixedCell|0
MPC|0
NetworkAddress|
NetworkType|-1
OBSSCoex|-1
PLCPHeader|0
PowerSaveMode|0
PwrOut|100
RadioState|0
Rate|0
RateA|0
RoamDelta|3
RoamTrigger|3
rts|2347
scan_channel_time|-1
scan_home_time|-1
scan_passes|-1
scan_unassoc_time|-1
Service|BCM43XX
ShortGI|-1
SSID|
ssid_auto_promote|0
VHT_Feature|3
vlan_mode|-1
WakeUpCapabilities|0x0000ffff
WEP|
WME|-1
WowlKeyRot|1
WZCCoexist|0
```

Since this method did not work for me, I removed the ndiswrapper driver by removing its components from:

/etc/modprobe.d/ndiswrapper.conf
/etc/ndiswrapper

and commenting out the "blacklist wl" line from /etc/modprobe.d/blacklist.conf to return to the bcmwl-kernel-source driver after reboot.

So here I am at square one. I know that wireless-ac is new (and this card especially) but I can't be the only one having problems with this. It seems I've always had slow wifi speeds with ubuntu+broadcom. The README.txt file with the Broadcom driver here ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) lists my device as supported, yet it is very slow.

If anyone has any other ideas, I'm game to test them out. Otherwise, get on the ball, Broadcom!

---

### Post by chili555 on 2014-04-25
> in my case, I had the best luck with the Windows XP versionThat's what ndiswrapper requires, although it sometimes will accept Win2K. From *man ndiswrapper-1.9*:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Win&#8208;
       dows  XP drivers and kernel module to load the Windows XP drivers. Both
       are called ndiswrapper.> sudo apt-get install ndiswrapper-common ndiswrapper-source ndiswrapper-dkms ndiswrapper-utils-1.9 ndisgtkIf you install -source, you don't need -common nor -utils and vice-versa. If you do install -source, it simply installs the source code in /usr/src. You then need to build a .deb from the source code and install the deb. All is explained in the accompanying README. ```
less /usr/share/doc/ndiswrapper-source/README.Debian
```Unless the source code is built, it is ineffective. It is a pile of parts in cardboard boxes; it isn't yet a driver.

I am sorry that my answer can't be better.

---

### Post by Harp on 2014-04-25
> **chili555 said:**
> If you install -source, you don't need -common nor -utils and vice-versa. If you do install -source, it simply installs the source code in /usr/src. You then need to build a .deb from the source code and install the deb.

Ah, I see. I actually installed it through the Software Center and just typed out the packages here, assuming it would be the same.

---

### Post by asutton13 on 2014-05-08
I figured I might as well chime in on this thread as I'm experiencing the exact same issue with the Asus PCE-AC68 on Arch with kernel 3.14.2 and the proprietary broadcom-wl driver version 6.30.223.141 (the same as the OP). I'm getting a maximum link speed of about 81Mbps as reported by gnome network manager. I actually see a connection of 540Mpbs immediately after connecting to the wireless network, but this quickly decreases to 81Mpbs and stays at this value. Under Windows with the computer in this particular location I am able to get gigabit speeds.

Update: My 81Mbps speed seems to be an overestimate as repeated speed tests show that I'm getting no more than 30Mbps.

Update 2: I came across this thread [http://ubuntuforums.org/showthread.php?t=2220007]("http://ubuntuforums.org/showthread.php?t=2220007") for a macbook air (which has the same BCM4360 wireless chipset) which puts the issue to rest. The current broadcom driver isn't capable of full AC speeds, and is in fact limited to G only. So the maximum speed is 54Mbps. Very disappointed by this, but at least we now know why it's so slow.

---

### Post by blanik on 2014-05-16
I recently purchased an Asus PCE-AC68 wifi card after checking that the Broadcom supplied Linux STA Driver supported this card.  The web site for the Broadcom Linux STA Driver ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) states that the BCM4360 chip set is supported by this driver version (6.30.223.141).  What they don't tell you is that the driver only allows the wifi interface to connect at 802.11G speeds, and not very reliably at that.  

Looks like I now own a very expensive 802.11G WIFI Card.  If the details about supported chipsets and capabilities was honestly reported on the Broadcom web site, I would not have wasted my money purchasing the PCE-AC68 WIFI card, as nobody wants to own an unsupported and unworkable device.  (As an aside - I've tried using an ndiswrapper installed WinXP Driver, but have not had any success so far- only one inf/sys file combinations worked at all under ndiswrapper, and it only provided 802.11n on 2.5 GHz - no 5 GHz.  

So, I wonder how long we'll have to wait before we get come sort of driver that addresses the 802.11AC capabilities of the current crop of WIFI Chip Sets?  Are any of the current crop of AC WIFI chips supported under Ubuntu yet ?

Signed,

Roy

---

### Post by chili555 on 2014-05-16
> Are any of the current crop of AC WIFI chips supported under Ubuntu yet ?In another thread on this forum, a user reports AC speeds with his Intel 7260.

---

### Post by andrew203 on 2015-02-22
> **Harp said:**
> I've been searching for a solution to this for a while and (surprisingly) haven't come up with anything. If anyone has a link, that would be cool too..
 I've Read this post many times while searching solutions to this problem to no avail.

I'm Very new to linux and am Running Mint 17.1, but i've mannaged to be currently Achieving 800mb Connection on 5ghz band with this ASUS PCE-AC68 Wireless Lan Adapter device.
   after extracting the current broadcom driver from site to "hybrid_wl" folder i edited this file --> hybrid_wl/src/wl/sys/wl_iw.c before building and installing wl.ko
on the line for N  i also removed the second argument,
case WLC_PHY_TYPE_N:
                strcpy(cap, "abgn");
            break;
hoping for basic N speeds on 2.4 band but did not work. But the 5ghz band seems to be working instead..


iwconfig reports
eth1      IEEE 802.11abg  ESSID:"Omnibus"  
          Mode:Managed  Frequency:5.805 GHz  Access Point: 10:C3:7B:42:8F:F4   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


Overall this is the best and most solid I've had this device function. 
Basic Installation of kernel-source left me with less then consistent speeds of wireless G. Building Current Broadcom driver had relevantly the same results.

 If you guys need any other info let me know
Hope this helps.

---

### Post by negora on 2015-08-02
What's the situation with the driver nowadays? I was considering purchasing this device, but taking into account the problems that you've been facing, I may change my mind radically.

Thank you.

---

### Post by morrna on 2015-10-02
> **chili555 said:**
> In another thread on this forum, a user reports AC speeds with his Intel 7260.

Could you please post a link to that thread? I am considering purchasing an Intel 7260 adapter, and I'd like to know how he got it working.

---

### Post by chili555 on 2015-10-02
> **morrna said:**
> Could you please post a link to that thread? I am considering purchasing an Intel 7260 adapter, and I'd like to know how he got it working.I think this is the thread I remember. A user reports that with a 3.13+ kernel and the -8 or, I assume, later firmware, that he got AC speeds. Others are unable to confirm.

[http://ubuntuforums.org/showthread.php?t=2178873](http://ubuntuforums.org/showthread.php?t=2178873)

---

