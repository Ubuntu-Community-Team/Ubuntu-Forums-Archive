---
title: "Wireless connection - fine in Windows, but not on Linux?"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-04-01
Hi all - another wireless query to add to the list - I've searched a few threads but haven't seen anything similar.

I recently moved house - Ubuntu (8.10) was happily working away via wireless on my old network in the old house, so I'm fairly sure my network adapter is supported.

In my new house, when I boot in Windows, the network shows up with 4 out of 5 bars signal strength and connects straight away.

Ubuntu however doesn't seem to think there are any wireless networks to connect to?! i've made sure wireless is enabled, I've tried creating a wireless network with the correst SSID, I;ve turned off all security etc - nothing is working.

Please help! I'd almost made the complete switchover but this is a dealbreaker. No net = no more ubuntu :(

---

### Post by lkraemer on 2009-04-01
You need to find what Wifi hardware is installed by using a
Terminal Window and executing:

```

lshw -C network
ndiswrapper -l 

```

Then post the output, or search this forum for HOWTO: & WIFI_INFO
where WIFI_INFO is 4318 for example of Broadcom, or AR242x for Atheros.

I am sure you will find a good guide.

lkraemer

---

### Post by mikechant on 2009-04-02
Did you bring your old wireless router with you, or is this a new one? If they're different, what are the router models? I've come across one router that wouldn't work reliably with Linux even though it worked with Windows, and it seemed to be a problem with the router software not properly implementing protocols and instead coding to Window's quirks.
Also, have you (say) changed from Cable to DSL or anything?


Finally, some people find they have more sucess using the alternative to Network Manager - Wicd.

---

### Post by TpyKv on 2009-04-02
Definitly try Wicd, I have had endless problems with network manager

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

scroll down to 

Installing Wicd in Ubuntu

Could not be easier and might solve it - simply! let us know how you get on....

---

### Post by aquascrotum on 2009-04-02
To answer the above posts and update the situation...

I am using a different router now than I had in my old location. The old location was a BT Voyager modem router (unsure of model number). The new router is a Netgear DG834G.

I removed my PCI wireless card and installed a USB wireless stick that I could mount at a high level - and now am able to connect to the network in Ubuntu.

However, again, in XP my network strength with the current setup is 99%. In Ubuntu it is 17% and fairly unreliable. Is this now a router issue?

To ldskraepr - the output to the commands you recommended is now as follows:

*-network                                        
       description: Ethernet interface             
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation                   
       physical id: 8                              
       bus info: pci@0000:03:08.0                  
       logical name: eth0                          
       version: 01                                 
       serial: 00:13:72:d3:1b:04                   
       width: 32 bits                              
       clock: 33MHz                                
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes           
  *-network:0 DISABLED                                                          
       description: Ethernet interface                                          
       physical id: 2                                                           
       logical name: pan0                                                       
       serial: 12:cb:42:51:9b:7d                                                
       capabilities: ethernet physical                                          
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes                                                                  
  *-network:1                                                                   
       description: Wireless interface                                          
       physical id: 3                                                           
       logical name: wlan1                                                      
       serial: 00:18:4d:bd:58:00                                                
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=IEEE 802.11bg

No idea what any of this means. Ubuntu is saved for another day though...

---

### Post by lkraemer on 2009-04-03
Please post the output of these commands:
```

lshw -C network
ndiswrapper -l
iwconfig
lsmod

```

Your previous post showed wlan1 as the Wifi and is most likely Intel.
Find the essid of your router. Then try this in a Terminal window:
```

sudo iwconfig wlan1 essid "youressidofrouter"
sudo iwconfig wlan1 mode Managed
sudo ifconfig wlan1 up
iwconfig

```
Try to surf via Firefox!

If you boot the LiveCD of Ubuntu does your Wifi work?
Did you use ndiswrapper and the Windows Wifi Driver on your previous
test, when it worked good?  Or, did it just work out of the box when
you booted the LiveCD?

What about trying another distro's LiveCD, like PCLinuxOS 2009.1, to see
what it does.  You would need to just click on
Control Center -> Network Setup, and it will work out of the box.
That would be a good test to see what Driver PCLinuxOS uses, then use
the same for Ubuntu.

lkraemer

---

### Post by aquascrotum on 2009-04-03
> **lkraemer said:**
> Please post the output of these commands:
```

lshw -C network
ndiswrapper -l
iwconfig
lsmod

```

Your previous post showed wlan1 as the Wifi and is most likely Intel.
Find the essid of your router. Then try this in a Terminal window:
```

sudo iwconfig wlan1 essid "youressidofrouter"
sudo iwconfig wlan1 mode Managed
sudo ifconfig wlan1 up
iwconfig

```
Try to surf via Firefox!

If you boot the LiveCD of Ubuntu does your Wifi work?
Did you use ndiswrapper and the Windows Wifi Driver on your previous
test, when it worked good?  Or, did it just work out of the box when
you booted the LiveCD?

What about trying another distro's LiveCD, like PCLinuxOS 2009.1, to see
what it does.  You would need to just click on
Control Center -> Network Setup, and it will work out of the box.
That would be a good test to see what Driver PCLinuxOS uses, then use
the same for Ubuntu.

lkraemer

Tried your code...no idea what it did but the wireless signal strength indicator shows no strength.

Previously the wireless just worked perfectly straight out of the box when I installed it.

Will try the other distro later.-

---

### Post by Papa-san on 2009-04-03
Don't get frustrated enough to quit, please! You already know how to use the terminal, so you are further ahead than I was at first!

There IS a solution. This situation is why 'WICD' was developed, and I have only heard of a few people that it didn't work for. (Most of that was operator error, anyways.) 

When you have a bit of time to devote to fixing this, start with the commands that have been posted. Do them one at a time, and post the results here. All of that data means something to us, and will allow us to help you solve the issue. You will find that the people in here will bend over backwards to help. (If they managed to stick with me through it, helping you will be a breeze! LOL)

I also want you to understand that helping you correct this allows some of the programmer types to write the scripts that will eventually make all of these transitions seamless... Believe it or not, you banging your head against the wall for a bit makes the whole Operating System better! We don't have a big corporation behind this O.S. YOU are part of the development team! Many of the wireless cards out there are now basically plug-and-play in Ubuntu... Eventually they all should be. 

Hang tough!

BTW- I have found that the wireless strength indicator isn't too accurate. I can pick up a signal over a quarter of a mile away, and it reads like 97%, and when I am in the same room as my wireless router, it can say 12%. We'll eventually get that worked out too.

---

### Post by aquascrotum on 2009-04-09
I need to resurrect this - I thougth I'd found a workable solution but it's just too unstable to persist with.

So to recap - I have a Belkin PCI wireless network card that worked out-of-the-box in Ubuntu on a previous home network.

When I moved house and connected to a new network I was unable to find any network connection using Ubuntu (in network manager or Wicd). The same setup in Windows shows 90%+ signal strength and connects immediately.

I removed the Belkin adapter in order to use a USB adapter which I could use on an extension cable in order to find a signal. I could now connect but only get a signal strength of 15% and the connection is extremely intermittent - cuts out every 5mins or so (again tried using both network manager and Wicd).

I've installed the windows wireless drivers program and tried to install the windows driver for the Belkin PCI card, but got a message saying it doesnt recognise the hardware. 

I want to get the Belkin card working again as having an unreliable USB connection draped over various bits of furniture is not workable. As I understand it, I need to run the following commands: 

lshw -C network
ndiswrapper -l
iwconfig
lsmod

...while the Belkin card is installed? Am assuming doing them while I'm using the USB dongle will be no good. This seems like an insane amount of hassle - turn off PC, uninstall USB dongle, install Belkin card, boot to Ubuntu, run commands, save to text file, restart and boot to Windows so I can use the net, post results, ..etc etc etc.

---

### Post by lkraemer on 2009-04-10
If you have a wireless available inside your house, it tells me that you
also have a Cable Modem (Hardware), or DSL Modem (Hardware) in your house,
and possible even a Router.  In which case, you also have a hardwired
Ethernet port present on your hardware that can be used to access this
Forum.  Why not just plug in a patch cord (Ethernet cable) and cut/paste
the results of your testing until you get the wireless working?  You don't
need your wireless working to do iwconfig etc......if you're hardwired.

REMEMBER: Every Wifi driver that you have previously installed will
either have to be removed, or blacklisted to get you where you can
reinstall your Belcan Wifi Hardware, install those drivers, and then get
it running.

I'd suggest running from a LiveCD, and testing your wireless to see if
it works when the LiveCD is finished booting.  Then, if it works, either
do a clean install, or REVERSE everything you have done with all
the previous Wifi Drivers and testing.

Either way, you are still going to have to post to this forum to get
the information so others know what is going on, unless you are lucky and
it works fine.

And don't forget, you can test other Distro's (like PCLinuxOS 2009.1)
to see if your hardware works from their LiveCD.  If it doesn't I'd wager
that within five left mouse clicks it would be up and running, if you
start from their Control Center, then progress to Networking, Wifi, etc.

Or try Knoppix 6.1, or Mandriva2009.1.........Most of these work right
from bootup on my machines.

lkraemer

---

### Post by aquascrotum on 2009-04-12
> **lkraemer said:**
> If you have a wireless available inside your house, it tells me that you
also have a Cable Modem (Hardware), or DSL Modem (Hardware) in your house,
and possible even a Router.  In which case, you also have a hardwired
Ethernet port present on your hardware that can be used to access this
Forum.  Why not just plug in a patch cord (Ethernet cable) and cut/paste
the results of your testing until you get the wireless working?  You don't
need your wireless working to do iwconfig etc......if you're hardwired.


The fact that I'm desperate to get a wireless connection going would be enough to suggest that I don't have ready access to a wired connection to the router...

> **lkraemer said:**
> REMEMBER: Every Wifi driver that you have previously installed will
either have to be removed, or blacklisted to get you where you can
reinstall your Belcan Wifi Hardware, install those drivers, and then get
it running.

How do I do that?

> **lkraemer said:**
> I'd suggest running from a LiveCD, and testing your wireless to see if
it works when the LiveCD is finished booting.  Then, if it works, either
do a clean install, or REVERSE everything you have done with all
the previous Wifi Drivers and testing.

Wireless performance booting from LiveCD is identical to my install - ie rubbish.

> **lkraemer said:**
> Either way, you are still going to have to post to this forum to get
the information so others know what is going on, unless you are lucky and
it works fine.

And don't forget, you can test other Distro's (like PCLinuxOS 2009.1)
to see if your hardware works from their LiveCD.  If it doesn't I'd wager
that within five left mouse clicks it would be up and running, if you
start from their Control Center, then progress to Networking, Wifi, etc.

Or try Knoppix 6.1, or Mandriva2009.1.........Most of these work right
from bootup on my machines.

lkraemer

Will try PCLinux Live Cd. Though if other distros are able to sort out wireless, why cant Ubuntu?

---

### Post by Paddy Landau on 2009-04-12
As your wireless works properly for Windows, and not for Linux, I suspect that you have a wireless card specifically designed to work with Windows and not any other OS.

If that's the case, then ndiswrapper would be your answer. It worked like a charm for one of my computers that has a Windows-only wireless card.

Here are the instructions; follow them carefully.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
You also may have to reboot your computer after completing the instructions.

---

### Post by lkraemer on 2009-04-12
I'll say it again, so you don't miss it the second time.
Please open a Terminal window and execute these commands, 
then post the output:
```

lshw -C network
ndiswrapper -l
iwconfig
lsmod
cat /etc/modprobe.d/blacklist

```

It's very hard for folks to know what you might have tried, or
installed and these commands will give them an idea.

lkraemer

---

### Post by Paddy Landau on 2009-04-13
> **Paddy Landau said:**
> ... ndiswrapper would be your answer...
Since writing the above, I discovered [Auto ndiswrapper]("http://easylinuxwifi.org/"). I haven't tried it, but it looks much easier. Caveat: It's still in very early stages of development.

---

### Post by aquascrotum on 2009-04-13
> **lkraemer said:**
> I'll say it again, so you don't miss it the second time.
Please open a Terminal window and execute these commands, 
then post the output:
```

lshw -C network
ndiswrapper -l
iwconfig
lsmod
cat /etc/modprobe.d/blacklist

```

It's very hard for folks to know what you might have tried, or
installed and these commands will give them an idea.

lkraemer

lkraemer - thanks for your patience. Sorry but this is pretty frustrating. 

I''ve removed my USB wireless and reinstalled bmy PCI wireless card, which is ultimately the one I want to use long term. I ran the commands you suggested and the outputs are as follows:

**lshw -C network**
```
 kyle@KyleDell:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wmaster0
       version: 01
       serial: 00:11:50:14:1b:92
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:13:0e:0f:72:a0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

**ndiswrapper -l**...did nothing (no output)

**iwconfig**
```
kyle@KyleDell:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SOMERVILLE"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
 
```

**lsmod**
```
kyle@KyleDell:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1      
radeon                342816  2      
ppdev                  15620  0      
drm                    96296  3 radeon
bridge                 56340  0       
stp                    10500  1 bridge
bnep                   20224  2       
vboxnetflt             91016  0       
vboxdrv               117544  1 vboxnetflt
input_polldev          11912  0           
video                  25360  0           
output                 11008  1 video     
nls_iso8859_1          12032  1           
nls_cp437              13696  1           
vfat                   18816  1           
fat                    58272  1 vfat      
lp                     17156  0           
parport                42220  2 ppdev,lp  
snd_hda_intel         435636  3           
snd_pcm_oss            46336  0           
snd_mixer_oss          22656  1 snd_pcm_oss                                     
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss                       
arc4                    9856  2                                                 
iptable_nat            13700  0                                                 
ecb                    10752  2                                                 
snd_seq_dummy          10756  0                                                 
nf_nat                 25876  1 iptable_nat                                     
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat                              
snd_seq_oss            37760  0                                                 
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4            
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
rt2500pci              23936  0
snd_seq_midi           14336  0
rt2x00pci              15616  1 rt2500pci
iptable_mangle         10880  0
rt2x00lib              37888  2 rt2500pci,rt2x00pci
snd_rawmidi            29696  1 snd_seq_midi
iTCO_wdt               19108  0
led_class              12036  1 rt2x00lib
iptable_filter         10752  0
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
mac80211              217208  2 rt2x00pci,rt2x00lib
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               23044  2 iptable_nat,ip_tables
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0
intel_agp              34108  0
agpgart                42696  2 drm,intel_agp
cfg80211               38032  2 rt2x00lib,mac80211
dcdbas                 15264  0
ndiswrapper           193436  0
serio_raw              13316  0
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
eeprom_93cx6           10240  1 rt2500pci
pcspkr                 10496  0
usbhid                 42336  0
usb_storage            82880  1
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit 
```

**cat /etc/modprobe.d/blacklist**
```
cat: /etc/modprobe.d/blacklist: No such file or directory
```

No idea what any of that is or does. Complete noob, sorry.

---

### Post by lkraemer on 2009-04-13
OK,
Well first of all try the following commands again, just use lowercase
characters in place of the uppercase I have typed.  It is best to just
cut/paste then you won't have errors. (ALL CAPS will avoid confusion.)
Just make sure you use lowercase in the Terminal window.
```

NDISWRAPPER -L
CAT /ETC/MODPROBE.D/BLACKLIST

```
Then repost the output.

From what you have posted it appears that your Wifi (wlan0) is connected
to essid "SOMERVILLE" and is in "Managed" Mode, with TX power on.
Is "SOMERVILLE" the Access Point you are trying to connect to?
Your AP is not linked

Mine looks like this for a functional Wifi, but yours may be ath0, wlan0,
etc......:
```

iwconfig

```
You should see something like this:
```

[larry@localhost ~]$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"AirlinkRouter"  Nickname:"localhost"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:A5:81:A0:D4
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-43 dBm  Noise level=-96 dBm
          Rx invalid nwid:9451  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```
From my display we know my Wifi is ath0, ESSID, and TX power is "ON" and
Mode is Managed

Your Laptop's LED's might not come on, and that is "OK"! If you see the above
you should be able to surf. BE SURE to "TURN ON" your Wifi if your
computer has a SWITCH or uses CNTL F2 or some other keystrokes to
enable the Wifi.

If your essid isn't assigned you can do (but remember to use your wlan0, ath0,
or what is displayed by iwconfig in place of ath0 below):
```

sudo iwconfig wlan0 essid "nameofyourwifirouter"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up

```
So, try the above three commands with the information you get from Windows XP
connection's data.  Then try to surf with your browser. (Make sure that your
browser doesn't have OFFLINE selected in the File -> Offline menu.)

lkraemer

---

### Post by aquascrotum on 2009-04-13
> **lkraemer said:**
> OK,
Well first of all try the following commands again, just use lowercase
characters in place of the uppercase I have typed.  It is best to just
cut/paste then you won't have errors. (ALL CAPS will avoid confusion.)
Just make sure you use lowercase in the Terminal window.
```

NDISWRAPPER -L
CAT /ETC/MODPROBE.D/BLACKLIST

```
Then repost the output.

From what you have posted it appears that your Wifi (wlan0) is connected
to essid "SOMERVILLE" and is in "Managed" Mode, with TX power on.
Is "SOMERVILLE" the Access Point you are trying to connect to?
Your AP is not linked

Mine looks like this for a functional Wifi, but yours may be ath0, wlan0,
etc......:
```

iwconfig

```
You should see something like this:
```

[larry@localhost ~]$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"AirlinkRouter"  Nickname:"localhost"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:A5:81:A0:D4
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-43 dBm  Noise level=-96 dBm
          Rx invalid nwid:9451  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```
From my display we know my Wifi is ath0, ESSID, and TX power is "ON" and
Mode is Managed

Your Laptop's LED's might not come on, and that is "OK"! If you see the above
you should be able to surf. BE SURE to "TURN ON" your Wifi if your
computer has a SWITCH or uses CNTL F2 or some other keystrokes to
enable the Wifi.

If your essid isn't assigned you can do (but remember to use your wlan0, ath0,
or what is displayed by iwconfig in place of ath0 below):
```

sudo iwconfig wlan0 essid "nameofyourwifirouter"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up

```
So, try the above three commands with the information you get from Windows XP
connection's data.  Then try to surf with your browser. (Make sure that your
browser doesn't have OFFLINE selected in the File -> Offline menu.)

lkraemer

Just to confirm before I start doing the above - I'm using a desktop PC (not laptop); however the wifi light on the back of the PCI card is on.

in Ubuntu using the current hardware, neither standard Ubuntu Network Manager or Wicd can see or connect to any wireless network (have tried them both, I have Wicd at present after getting rid of Network Manager.

The router I'm trying to connect to's SSID is SOMERVILLE. Will repost output to your commands in next post.

---

### Post by aquascrotum on 2009-04-13
Output from commands:


ndiswrapper -l
-No output

cat /etc/modprobe.d/blacklist
```
- cat: /etc/modprobe.d/blacklist: No such file or directory
```

iwconfig
```
kyle@KyleDell:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SOMERVILLE"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


sudo iwconfig wlan0 essid "nameofyourwifirouter"

```
kyle@KyleDell:~$ sudo iwconfig wlan0 essid SOMERVILLE
[sudo] password for kyle:
kyle@KyleDell:~$
```

sudo iwconfig wlan0 mode Managed, and sudo ifconfig wlan0 up - no output.

Still no network connection and no available networks in Wicd.

[IMG]http://i636.photobucket.com/albums/uu89/kylesom/Screenshot-WicdManager.png[/IMG]

---

### Post by lkraemer on 2009-04-13
Well, I have never seen this happen before.  I am at a loss.

I will be traveling for the next three days and won't have access.

I'll check in as soon as I can.

In the meantime have a look at this information.
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Maybe someone else has seen this before and is willing to help.

lkraemer

---

### Post by coffeeaddict22 on 2009-04-14
Hi,  
Haven't seen it before, but...
It looks like you might have a couple of drivers at least.  ndiswrapper shows up in your lsmod; I haven't played with it for a while but it looks like you're using the Linux drivers so you can ditch it (modprobe is the terminal command that removes kernel modules; try ```
man modprobe
``` for more information).

That might solve the problem. wmaster is a kernel fix for wireless networking, that should show up in some lists but shouldn't be seen as the network interface- where its showing up on your system.  looking at your lsmod, ndiswrapper is possibly the driver causing the glitch, and deleting that may fix the problem.

On the other hand, ndiswrapper should be wrapping a windows driver, and that's what ndiswrapper -l is supposed to show... so I'm not 100% sure.

---

### Post by Paddy Landau on 2009-04-14
> **coffeeaddict22 said:**
> On the other hand, ndiswrapper should be wrapping a windows driver, and that's what ndiswrapper -l is supposed to show... so I'm not 100% sure.
As I understand, ndiswrapper will wrap the Windows driver only if you actually tell it to do it. (Well, that's how it worked for me.)

Have you tried ndiswrapper yet? See [post 12]("http://ubuntuforums.org/showthread.php?p=7057632#post7057632").

---

### Post by lkraemer on 2009-04-14
I searched with GOOGLE for RaLink RT2500 and found these sites:
[http://ralink.rapla.net/](http://ralink.rapla.net/)
(You might want to get the latest Drivers, and compile them, but
without a wired connection it isn't going to be easy.

and (Post #2 in the URL below)
[http://ubuntuforums.org/showthread.php?t=99186](http://ubuntuforums.org/showthread.php?t=99186)

[http://ubuntuforums.org/showthread.php?t=884247&highlight=howto+RT2500](http://ubuntuforums.org/showthread.php?t=884247&highlight=howto+RT2500)
[http://ubuntuforums.org/showthread.php?t=784031&highlight=howto+RT2500](http://ubuntuforums.org/showthread.php?t=784031&highlight=howto+RT2500)
[http://ubuntuforums.org/showthread.php?t=563547&highlight=howto+RT2500](http://ubuntuforums.org/showthread.php?t=563547&highlight=howto+RT2500)
[http://ubuntuforums.org/showthread.php?t=241565&highlight=howto+RT2500](http://ubuntuforums.org/showthread.php?t=241565&highlight=howto+RT2500)

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)


[http://www.nabble.com/Wifi-Ralink-RT2500-td15712181.html](http://www.nabble.com/Wifi-Ralink-RT2500-td15712181.html)
(The last weekend i got wired internet connection for my pc, then updated gutsy, and ran 

sudo dhclient -q wlan0

sudo iwconfig wlan0 essid ...

sudo dhclient wlan0

and it just worked! 

As i didn't follow a proper experimental procedure i am not sure if the success was the result of updating or of the command "dhclient -q wlan0". Now i am a bit curious and would like to know it, but in any case it works.)


The following looks the best to me.  I've used bmartin's HOWTO's before.
[http://ubuntuforums.org/showthread.php?t=525833](http://ubuntuforums.org/showthread.php?t=525833)

Since you're booting Xp, downloading, booting to Ubuntu....etc.....
You might want to have a look at this:
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

It should make it easy.

BUT, probably the easiest thing to do is blacklist the current driver,
and then use ndiswrapper to install the windows drivers (*.inf, & *.sys
for the Ralink RT2500 as you should already have them since XP works).

lkraemer

---

### Post by Lazy-buntu on 2009-04-14
Ubuntu wireless has come a long way. I've been fine since 8.10. I install Ubuntu, get a wired connection to update, enable my restricted drivers, go into preference > network connections, then set up my connection.

Prior to 8.10, wireless was a nightmare for me on Ubuntu. I used Fedora 9 I believe and PCLOS Gnome 2008.

---

### Post by aquascrotum on 2009-04-15
> **Paddy Landau said:**
> As I understand, ndiswrapper will wrap the Windows driver only if you actually tell it to do it. (Well, that's how it worked for me.)

Have you tried ndiswrapper yet? See [post 12]("http://ubuntuforums.org/showthread.php?p=7057632#post7057632").

I tried the automated script that runs ndiswrapper which said it successfully installed the driver - I downloaded the latest RT2500 for my wificard variant so am sure their ok.

I now have a wifi connection but its still very patchy - signal strength is max 45% (90% in Win Xp still) and often simply refuses to connect, hanging at the Validating stage when trying to connect using Wicd. Also, using Wicd, when I go into preferences for the connection and select the "Supplicant Driver", the only option I can successfully get a connection on is "wext". There is an option in there to use an ndiswrapper but it refuses to connect using it.

How can I tell what user is definitely being used now?  Thanks for the continued advice btw. Don't want to run any more commands until I'd updated the situation...I don't want to jeopardise the patchy connection that I'm currently relying on.

---

### Post by coffeeaddict22 on 2009-04-17
There's two types of terminal commands.  One gives you information about your system; the second modifies the system.  You'll learn a lot more if you play around with the ones that query your system and output the response.  If you want more info (and as a rule for any command you don't recognise) type man XXXX into a terminal (where XXXX is the command) for a bit of a look at the detail.

To find out what driver you're using, ```
lshw -C network
``` will provide a whole lot of info, including a line at the bottom starting "configuration:" that includes the driver.

TO identify the network you're on try ```
iwconfig
``` (sudo iwconfig and ifconfig give more info too), and ```
sudo iwlist scan
```

---

