---
title: "installing ndiswrapper"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by tonyfazackerley on 2010-05-19
working with ubuntu 9.04, having problems with wireless connection, trying to install ndiswrapper to work through the prob

have downloaded ndiswrapper-1.56 tar.gz onto a USB key

navigated terminal to the key....detarred the file

then ran sudo make 
– the response was “no targets specified and no makefile found”

could anyone help with this command, i guess i need to target it at a directory where synaptic can find it but don't know which that is and don't know why there is no "makefile"

if some of the above is nonsense then apologies in advance 

thanks

---

### Post by Sealbhach on 2010-05-19
Do you specifically need 9.04? We're at release 10.04 now, why not try that?

To answer your question, you need to extract the contents of the tar.gz file. Just right-click on it and select "Extract Here".


.

---

### Post by anewguy on 2010-05-19
Going to make a couple of assumptions:

- you have a livecd
- you have the wireless driver for your adapter (both the .inf and .sys files)
- you know you need to use ndiswrapper

The easiest way to install it is via the LiveCD.  If you navigate to the /pool/main/n folder on the LiveCD you'll find a folder for ndiswrapper.  Open it and click on ndiswrapper common first to install it, then click on the ndiswrapper utilities to install it.  Lastly, navigate to the /pool/main/n folder and you will see the folder for ndisgtk.  Go to that folder and click on the file there to install it.

Once you've done that, just go to System/Adminnistration/Windows Wireless Drivers and when it starts up do an add and point in to the driver file for your wireless.

Dave ;)

---

### Post by Drenriza on 2010-05-19
> then ran sudo make
is when you install from source.

when installing from source always read the ReadME file.

but this is what you need to do

```
./configure
```

```
make
```

```
sudo make install
```

```
clean install
```

---

### Post by 3rdalbum on 2010-05-19
> **anewguy said:**
> Going to make a couple of assumptions:

- you have a livecd
- you have the wireless driver for your adapter (both the .inf and .sys files)
- you know you need to use ndiswrapper

The easiest way to install it is via the LiveCD.  If you navigate to the /pool/main/n folder on the LiveCD you'll find a folder for ndiswrapper.  Open it and click on ndiswrapper common first to install it, then click on the ndiswrapper utilities to install it.  Lastly, navigate to the /pool/main/n folder and you will see the folder for ndisgtk.  Go to that folder and click on the file there to install it.

+1. I'd especially make sure that you need to use ndiswrapper. Sometimes certain wifi cards won't work out-of-the-box because the wrong driver has taken control (but this can be fixed), and Ndiswrapper won't work because the wrong driver is still in control.

Also, sometimes the correct driver is working as it should (it connects and you can ping your router) but the router hasn't passed along the DNS information that Ubuntu needs to turn a name such as [www.google.com](www.google.com) into an IP address. This can be fixed by manually specifying the DNS, and changing the driver will not help. For more information on this, see [www.chrislees.info/ubuntu/opendns.shtml](www.chrislees.info/ubuntu/opendns.shtml)

---

### Post by lkraemer on 2010-05-19
Before you install ndiswrapper...............

Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
If you are requesting help, post the output of each command........

Then make a decision about ndiswrapper.

lk

---

### Post by tonyfazackerley on 2010-05-19
Thanks for all the replies (after being mired in XP it's a bit overwhelming)

My basic problem is an inability to connect to my wireless router, I have been following up threaded  suggestions for about one week now and am getting nowhere, WPA security is on and I have disabled MAC filtering but although the SSID is seen, connection attempts simply generate repeated requests for a password. 

My latest attempt involved working through troubleshooting with the ndiswrapper hence my post re installing it.  As you can probably tell, I don't know if I need ndiswrapper or not.

I have run the commands suggested by lk (many thanks) and this is what I get

lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) 
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


lsusb
Bus 001 Device 003: ID 0930:6532 Toshiba Corp. 256M USB Stick 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 


lshw -C network
 *-network:0             
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       logical name: eth0 
       version: 10 
       serial: 00:c0:9f:92:8c:e4 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network:1 
       description: Wireless interface 
       product: PRO/Wireless 2200BG [Calexico2] Network Connection 
       vendor: Intel Corporation 
       physical id: 4 
       bus info: pci@0000:02:04.0 
       logical name: eth1 
       version: 05 
       serial: 00:12:f0:4b:30:8f 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 96:34:e3:02:42:66 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

lsmod
Module                  Size  Used by 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat 
usb_storage            82880  1 
isofs                  39844  0 
udf                    87716  0 
crc_itu_t              10112  1 udf 
i915                   65540  2 
drm                    96296  3 i915 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge 
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp 
pcmcia                 44748  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0 
ac97_bus                9856  1 snd_ac97_codec 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
intel_agp              34108  1 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket 
psmouse                61972  0 
agpgart                42696  3 drm,intel_agp 
ipw2200               150984  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic 
pcspkr                 10496  0 
serio_raw              13316  0 
video                  25360  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
ieee80211              38344  1 ipw2200 
ieee80211_crypt        13444  1 ieee80211 
shpchp                 40212  0 
soundcore              15200  1 snd 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm 
output                 11008  1 video 
usbhid                 42336  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp 
fbcon                  46112  0 
tileblit               10752  1 fbcon 
font                   16384  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 

ndiswrapper -1
The program 'ndiswrapper' is currently not installed.  You can install it by typing: 
sudo apt-get install ndiswrapper-common 
bash: ndiswrapper: command not found 

 cat /etc/modprob.d/blacklist.conf 
cat: /etc/modprob.d/blacklist.conf: No such file or directory 

iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions.

---

### Post by lkraemer on 2010-05-19
You now need to Google search for:
HOWTO: Intel Corporation PRO/Wireless 2200BG
and search this forum to see what's next.

Maybe the first part of this will apply:
[http://ubuntuforums.org/showthread.php?t=13576](http://ubuntuforums.org/showthread.php?t=13576)

or
[http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)


lk

---

### Post by tonyfazackerley on 2010-05-19
Thanks for that ik
does this mean that my 2200BG wireless card is not activated ? or has no drivers ?  I read that since Ubuntu Dapper, ipw2200 drivers are included in the standard kernel

tf

---

### Post by lkraemer on 2010-05-19
From what I read, you have the drivers included....in fact I forgot to
mention that the driver appears to be loaded as it shows in the listing
in lsmod.  ie. ipw2200 150984 0 

So, if it were me I'd try downloading the firmware, untar it, and
copy it to where the previous posting states, and then try to go to
SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and enable them.  See if
that works.  The information on the Google finds seems kinda sketchy to me.
Maybe that is all you need to do.  OH, I'd reboot too!.

Also, everything else you posted from the initial commands looks as I would 
expect it to be.

lk

---

### Post by anewguy on 2010-05-19
The lshw -C network shows:

driver=ipw2200 driverversion=1.2.2kmprq

as part of the output for your wireless adapter.  As best as I understand that means it is using the ipw2200 driver that is installed already.  Without a little more looking I'm not sure what your pan0 network is.

But, even more importantly, the fact that you can see your router but can't connect means the wireless is definitely working, so I think we can ignore anything that has to do with loading a driver - this includes ndiswrapper.

What you are having problems with is actually connecting when using WPA to your router 

> My basic problem is an inability to connect to my wireless router, I have been following up threaded suggestions for about one week now and am getting nowhere, WPA security is on and I have disabled MAC filtering but although the SSID is seen, connection attempts simply generate repeated requests for a password.

So, are the password requests for the network (wpa) password, or are they for the network keyring password?

The first thing I would do is click on network manager and edit connections.  Then delete any connections that show there from your previous attempts to connect.

Now, start again by clicking on "Create new wireless network".  In the screen that opens, supply your SSID, then be sure to select the correct encryption type.  I usually click on "show password" just so I can see what I am entering, so I would suggest doing that and entering your password.  Then okay it to try to connect.  What happens?  Take a screen shot if it doesn't connect and post it back here so we can see what is happening.

Dave ;)

---

### Post by tonyfazackerley on 2010-05-20
Thanks for that Dave

I now have a connection to the router but no access to the internet. Using "create new wireless network" did the trick rather than clicking the radio button next to the auto identified SSID. A reboot gave a router connection but no internet.

Any Ideas

Thanks

TF

---

### Post by Peter09 on 2010-05-20
Not sure that create new wireless network is going to give you what you want - it configures the device for peer to peer wireless.
 
Try removing the network and attaching as normal again.
 
Also can you post ifconfig now.

---

### Post by anewguy on 2010-05-20
EDIT:  Removed what I had here originally as I was incorrect.  Peter09, I think you're right except that I have used the add function under wireless in edit connections.

tonyfazackerley:

right click on network manager, go to edit connections again, then to the wireless tab, and remove anything dealing with your connection there.  Then use the "Add" function there to create the new connection.

I believe that just doing a create new wireless network essentially does the same thing, as the network you create becomes an option in network manager/edit connections/wireless, but best to do what I just outlined instead.  Sorry.

I'm going to ignore the problems of not getting to the internet until after you make these changes and try again.

Dave ;)

---

### Post by tonyfazackerley on 2010-05-20
Deleted wireless network connection and reattached using the auto radio button  this put me back into the loop of repeated requests for a WPA key.  Then deleted this connection and created a new connection manually.  This connecting to the router but still with no internet connection

an interesting point is that when the repeated WPA password request comes up the password box is filled in with a Hex password that is not the same as the Hex password derived from the ascii one manually entered during the &#8220;create new wireless network&#8221; routine.


ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:92:8c:e4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:6 Base address:0x3800 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:4b:30:8f  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0 
          inet6 addr: fe80::212:f0ff:fe4b:308f/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:12359 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:21 errors:0 dropped:6 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5209 (5.2 KB) 
          Interrupt:11 Base address:0xc000 Memory:e0401000-e0401fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB) 



After the manual connection was set up there was a connection to the router but no connection to the internet

during the reboot a request for the password for the default keyring was asked for as follows

&#8220;The application 'NetworkManager Applet@ (/usr/bin/nm-applet) wants access to the keyring but it is locked&#8221;  

The password was supplied

A connection to the router was established but any attempt to open any web page returned &#8220;Address not found&#8221;

---

### Post by anewguy on 2010-05-20
This almost sounds like a DNS or DHCP problem.  How do you have your router configured?

Dave ;)

---

### Post by Peter09 on 2010-05-20
This line
 
> inet addr:10.42.43.1 Bcast:10.42.43.255 Mask:255.255.255.0 
 
shows the IP address that the system is working to. Is it what you would expect?

---

### Post by tonyfazackerley on 2010-05-20
Router is configured &#8220;automatic configuration &#8211; DHCP
local ip 192.168 1.1
subnet mask 255.255.255.0
with an IP address range 192.168.1.10 to 192.168.1.59
internet IP address 80.7.183.91
DDNS disabled (don't know what that means)
Security firewall disabled
and the encryption algorithm is TKIP

please stick with it, I really appreciate this after week of gently banging my head against the wall

tf

---

### Post by lkraemer on 2010-05-20
Open a Terminal Window and do:
```

lsmod
iwconfig

```
Post the output.

lk

---

### Post by 3rdalbum on 2010-05-20
Run:.

ping 192.168.1.1

If you start getting lines appearing in your terninal, then you have connectivity to the router. Your next step woyld be to set a DNS, which you can find about here:

[www.chrislees.info/ubuntu/opendns.shtml](www.chrislees.info/ubuntu/opendns.shtml)

---

### Post by Peter09 on 2010-05-20
Well, if you have an IP address in the 10.00.....range it means that your machine is not collecting an IP address from the router (check that you have DHCP) turned on in the router.
 
It may be worth power cycling your router.
 
Also what is the output of the
 
```
route
```
command.

---

### Post by Peter09 on 2010-05-20
Another thought strikes.
 
i have had experience with wireless cards which can get confused and refuse to work (exactly like yours). I have found that sometimes powering of the machine, removing the battery and leaving for 30sec or so will drop the card back to a default position.
 
Removing the battey seems to be a necessity ....

---

### Post by tonyfazackerley on 2010-05-20
ping 192.168.1.1 gave …   Network is unreachable

lsmod gave    …   
Module                  Size  Used by 
ipt_MASQUERADE         10752  1 
xt_state               10112  1 
ipt_REJECT             11136  2 
xt_tcpudp              11008  4 
iptable_filter         10752  1 
nf_nat_h323            14336  0 
nf_conntrack_h323      56648  1 nf_nat_h323 
nf_nat_pptp            11136  0 
nf_conntrack_pptp      14212  1 nf_nat_pptp 
nf_conntrack_proto_gre    13572  1 nf_conntrack_pptp 
nf_nat_proto_gre       10372  1 nf_nat_pptp 
nf_nat_tftp             9600  0 
nf_conntrack_tftp      12308  1 nf_nat_tftp 
nf_nat_sip             14976  0 
nf_conntrack_sip       26260  1 nf_nat_sip 
nf_nat_irc             10240  0 
nf_conntrack_irc       13220  1 nf_nat_irc 
nf_nat_ftp             10752  0 
nf_conntrack_ftp       15652  1 nf_nat_ftp 
iptable_nat            13700  1 
nf_nat                 25876  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat 
nf_conntrack_ipv4      21388  4 iptable_nat,nf_nat 
nf_conntrack           72008  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4 
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4 
ip_tables              19472  2 iptable_filter,iptable_nat 
x_tables               23044  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables 
michael_mic            10496  2 
arc4                    9856  2 
ecb                    10752  2 
ieee80211_crypt_tkip    16896  1 
i915                   65540  2 
drm                    96296  3 i915 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge 
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp 
pcmcia                 44748  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0 
ac97_bus                9856  1 snd_ac97_codec 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
iTCO_wdt               19108  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket 
ipw2200               150984  0 
iTCO_vendor_support    11652  1 iTCO_wdt 
psmouse                61972  0 
soundcore              15200  1 snd 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic 
intel_agp              34108  1 
ieee80211              38344  1 ipw2200 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,ieee80211 
pcspkr                 10496  0 
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm 
video                  25360  0 
agpgart                42696  3 drm,intel_agp 
shpchp                 40212  0 
output                 11008  1 video 
usbhid                 42336  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp 
fbcon                  46112  0 
tileblit               10752  1 fbcon 
font                   16384  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit



iwconfig gave   ...
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11g  ESSID:"Rachael"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:12:F0:30:4A:FD   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=67/100  Signal level=-60 dBm  Noise level=-85 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 


tf

---

### Post by tonyfazackerley on 2010-05-20
power cycled the router - although I am using the router for a wired connection on this my XP desktop

disconnected mains and battery from the laptop with no noticeable change



Route  gave   &#8230;   
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1

---

### Post by Peter09 on 2010-05-20
Your wireless card can see your network
 
> eth1 IEEE 802.11g ESSID:"Rachael" 
 
but cannot link to it. Is it asking for the passphrase, what is it asking and what are you putting in ( not the exact phrase but is it correct?)

---

### Post by tonyfazackerley on 2010-05-20
when I set up the network connection manually via network connections I enter the correct WPA key and hovering the mouse over the signal strength bar chart top line I get "Wireless network connection 'Rachael' active:Rachael 67%

if I use auto connect through the radio button next to Rachael on the list of available networks then it asks for a WPA password.  At this point the password box is already filled in and show password reveals a hex string which is not related to the genuine password

overwriting this hex string prompts the icon to search and this search again generates a request for the WPA password again with the password box filled in with the wrong hex string and so on ad infinitum

it seems as though the os has a wpa password that it prompts me to use that has no relation to the actual password that I set up in my router

having said all that, disabling router security with has the effect of not showing the request for a password but going straight to a disconnected (bar chart+X) icon

tf

---

### Post by Peter09 on 2010-05-20
Don't worry about the HEX string, thats what your password is turned into.
 
Puzzled .....

---

### Post by tonyfazackerley on 2010-05-20
OK but just to be sure I have explained properly

I get two different WPA hex strings 
one when auto rachael tries to connect 
and one when manually set up rachael tries to connect
both generated from the same ascii string

tf

---

### Post by anewguy on 2010-05-20
Here is what I would do first to check things out:

- right-click on network manager and go to edit connections again
- click on the wireless tab
- you should see "Rachael" since that is the ESSID showing in your lists
- click on "Rachael"
- click "Edit"
- click on the Wireless tab
- mode should be infrastructure 
- MTU should be automatic
- click on the Wireless Security tab
- "Security" should be "WPA & WPA2 Personal"
- your password needs to match the password you set at the router.  
- click on the IPv4 tab
- "Method" should be "Automatic (DHCP)"
- click on the IPv6 tab
- "Method" should be "Ignore"

But in reality, I would:
-right-click network manager and remove and connection references under "Wireless"
-change the router temporarily to a completely open network (no encryption, no MAC filtering) and see if you can connect by just clicking on the network name in network manager

Until you can connect with no encryption and no MAC filtering, there is no use in adding more to the equation.

Once you can connect to the open network:

- go to your router configuration page
- add in WEP with a simple password - like "charlie"
- save the configuration
- go back to network manager and try to connect again and use "charlie" when prompted for the WEP password

Once you can connect to the WEP network:

- go to your router configuration page
- change to WPA PSK  (I'm not on my router config page right now, so it might same something slightly different - WPA2 PSK/TKIP or something)
- put in a hex password you make up (write it down also)
- save the configuration
- go back and right-click on network manager
- go to "Wireless" and remove any references to your network
- close out
- click on network manager and select your network again
- enter in the correct encryption type - must match what you put in at the router
- enter in the hex password you wrote down that you entered in the router
- see if you can connect

Once you get that working you can add in MAC filtering at the router for an extra layer of protection if you want to.

Please report back what happens at each step.  If you end up with a failure, take a screenshot (applications/accessories/take screenshot) and post it back here so we can see what it is doing.

Oh, and I think you already know it, but don't confuse the network keyring password with the network password.

Dave ;)

---

### Post by tonyfazackerley on 2010-05-20
following through gave the following exceptions

in NM 
Wireless tab mode was ad-hoc
in Ipv4 tab  method was shared to other computers changing this to automatic(DHCP) allowed an entry into the previously greyed out box &#8220;DHCP Client ID&#8221; which I did not fill in
There is no Ipv6 tab on my system

after doing the above I closed the laptop down for 30 secs and rebooted ( I don't know why but a lot of posts say this makes a difference)
on reboot nm showed &#8220;no network connection&#8221;

after a bit of experimentation I found that changing the mode away from ad-hoc always resulted in disconnection but that setting Ipv4 method to automatic(DHCP) gave a connection to the Rachael network but not to the internet. (and I can't see other computers on the network).


So &#8230; disabling all security on the router

now I can put the mode to infrastructure and the Ipv4 to automatic(DHCP) without suffering a disconnection from the network.


Also the IP4 tab has a Route button available 












































































sorry but I am being forceably removed to visit the family, I will return to this next week


once again lots of thanks for everybodies help this is my first forum experience and even if we don't get a result I think it's fantastic


tf

---

### Post by tonyfazackerley on 2010-05-20
oops I don't know where the screenshots went on the above posting

I've got them here as .png files but can't seem to paste them in

anyway the screen obtained from the routes key shows headings 
Address   NetMask   Gateway   Metrics

with nothing entered underneath

got to go 

tf

---

### Post by anewguy on 2010-05-21
> **tonyfazackerley said:**
> 
So &#8230; disabling all security on the router

now I can put the mode to infrastructure and the Ipv4 to automatic(DHCP) without suffering a disconnection from the network.


Also the IP4 tab has a Route button available 



You do want infrastructure mode when using a router.  Also - when you disabled security on the router and didn't get disconnect after making the changes, were you able to connect to the internet then?

I wanted you to get to where you could at least connect to the internet, then we can work on adding security things back in one at a time.  If you weren't able to connect to the internet, did you have anything listed under routes?

Open a terminal window and try:

- ping [www.yahoo.com](www.yahoo.com) <press enter>

Do you get lines indicating it is pinging (you have to ctrl-c to stop it)?

If not, do you get a line similar to the following:

ping: unknown host [www.yahoo.com](www.yahoo.com)

if so, try:

ping 67.195.160.76 <press enter>



Dave ;)

---

### Post by tonyfazackerley on 2010-05-21
without router security there is a network connection
there is no internet connection
IPv4 routes has nothing listed
ping yahoo does not get lines
ping yahoo returns "unknown host www.yahoo.com"
ping 67.195.160.76 returns "network is unreachable"

tf

---

### Post by tonyfazackerley on 2010-05-21
in my router security setting there is a box titled "group key renewal" which is set to 3600 seconds, is that relevant


tf

---

### Post by tonyfazackerley on 2010-05-21
sorry about the group key red herring I now know it is;

It is the interval in which the client and access points rotate their keys to increase security. It is part of the WPA protocol thus it is automatically. It does not influence your security setting

guess i should try a little harder to answer my questions myself


tf

---

### Post by Peter09 on 2010-05-21
Can you post the output if ifconfig again so that we can check your IP address, it should be 192.168..... etc

---

### Post by anewguy on 2010-05-21
Well, I'm basically out of ideas.  If the router is set as a open network, and you've removed all the previous network defs in network manager/edit connections/wireless, and you have it set to infrastructure and automatic DHCP, I'm a little lost as to why it doesn't work, unless there are more settings on your particular router that I don't know.

Dave ;)

EDIT:  I don't know if it's there or not, and right now I'm not at my router to check, but be sure your router is set to infrastructure and not ad-hoc as well, if that's possible.

---

### Post by tonyfazackerley on 2010-05-25
Solved you said

"unless there are more settings on your particular router that I don't know."

I explored every setting and changing UPnP from disable to enable has allowed the laptop to access the internet through the router.

Thank you to everybody who helped it's been a great learning experience for me

tf

---

