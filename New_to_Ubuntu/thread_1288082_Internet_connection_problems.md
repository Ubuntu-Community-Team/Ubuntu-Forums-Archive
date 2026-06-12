---
title: "Internet connection problems"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by augie2051 on 2009-10-10
Here is an issue that has be perplexed.  I am running a dual boot 9.04 and Vista.  When i connect to the internet with vista i am at a 12 meg download connection.  When i connect with ubuntu i am at 3 and 2 meg. What would cause this and any ideas how to fix?

---

### Post by coffeeaddict22 on 2009-10-11
Hi,
Could be a couple of things.
First up, is it real?  Try downloading a 1MB file from somewhere and check the download time in both systems.  The most likely reason is Windows is reporting MegaBITs, and there's 8 of them to a MegaBYTE.  Lies, damned lies and statistics applies here (seeing as Linux isn't charging you, there's no reason to make you think you've got more speed than you actually have).

If the speed slowdown is real, then it's a network problem.  If you're running Gnome, open a terminal and type in ```
nm-tool
``` The output from that should help identify the problem.  Post back here if you want a hand.

---

### Post by 3rdalbum on 2009-10-11
If you are accessing the internet connection through wifi, your wireless driver might be running at a lower speed. What happens if you connect your machine with an Ethernet cable, or download the "linux-backports-modules-jaunty" package?

---

### Post by augie2051 on 2009-10-11
its not a report problem i can tell a huge difference when downloading and I am connected wireless here is the output: 
Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Maynard:         Infra, 00:22:3F:7B:EA:06, Freq 2462 MHz, Rate 54 Mb/s, Strength 28 WEP
    *WOW!781459:     Infra, 00:15:D0:37:B4:3A, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA

  IPv4 Settings:
    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             64.233.214.34
    DNS:             64.233.214.41

---

### Post by coffeeaddict22 on 2009-10-11
That all looks OK.  Might be worth checking to see if the slowdown is an encryptation problem; I think it's been fixed but a while back that was causing issues.  Try turning off the security on your router.  If that's no help, what's the output of ```
lshw -C network
```

---

### Post by augie2051 on 2009-10-11
Not sure how to turn the security off of the router and here is the output
 description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:4e:61:ef
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:80:88:eb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.2 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:e6:ab:de:2c:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by coffeeaddict22 on 2009-10-11
The logical name for your wireless suggests you've got some sort of conflict going on.  wmaster0 is a kind of workaround for wireless network drivers; each driver in turn has it's own code, but they talk to the kernel through wmaster0.  It's not supposed to show up at the user interface.
What's the output of lsmod?  In particular, have you got another driver loading?  It's usually ndiswrapper, but there's exceptions to every rule (including this one...)

---

### Post by augie2051 on 2009-10-11
output:
usb_storage            99648  1 
serio_raw              13444  0 
sdhci                  23940  1 sdhci_pci
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
intel_agp              34108  0 
usbhid                 42336  0 
btusb                  19608  2 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
cfg80211               38288  3 iwlagn,iwlcore,mac80211
dcdbas                 15264  0 
agpgart                42696  2 nvidia,intel_agp
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by augie2051 on 2009-10-11
> **3rdalbum said:**
> If you are accessing the internet connection through wifi, your wireless driver might be running at a lower speed. What happens if you connect your machine with an Ethernet cable, or download the "linux-backports-modules-jaunty" package?

I downloaded these three packages whats the next step?

---

### Post by augie2051 on 2009-10-12
Alight so get this.  I upgraded to Karmic Koala and now my speed is up to 11 mbs?!  Don't know how or why any ideas

---

### Post by coffeeaddict22 on 2009-10-12
Without more info, difficult to commment.  The Intel drivers may well have changed; have a look at nm-tool and see if there's any major differences in there as well.  Some people were having fun trying to get some of the wireless security settings to work a while back, and it may have been an improvement in that part of the system.  Also, the wireless drivers are fairly new to the kernel so it's possible that's where the improvements come from.

---

### Post by madeye1 on 2009-10-13
Hello, I'm good at getting around computers in general, and at following directions, but very new to Linux and Ubuntu ....
I jumped into this thread because I have the same problems of this gentleman.  (hopefully not stepping on toe's !! :)) 

I have an enhanced plan via my internet provider, and I'm suppose to have DL speeds of at least 10Mg and UL speeds of at least 2Mg.

My average when I had windows installed was 18Mg DL speed and 3.5Mg Up speed.    Ever since I installed Ubuntu though, I can't break 4.5Mg Download speed !!!
My system is a MD Athlon(tm) 64 Processor 3500+ giving me about 2.2 Ghz w/ 1Gig RAM and I'm running the latest Ubuntu - Karmic Koala.

I ran and I'm including the information the earlier gentleman was asked for:

_nm-tool_:

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:40:CA:AD:8A:F6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             68.87.75.198
    DNS:             68.87.64.150
    DNS:             192.168.0.1

and 

_lshw -c network_:

PCI (sysfs)  

  *-network DISABLED      
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:97:8f:ed:a3:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


Please help .... I have no idea what I need to do or where to even start .... I've started reading up on linux .... but I have a WAY to go to understand all this stuff.

---

### Post by coffeeaddict22 on 2009-10-14
Hi madeye, 
Welcome to Linux!  The ride is at least as much fun as the destination.

You're troubleshooting a wired network, right?

Looking at your output, you're running off the eth0 interface as your network connection.  You haven't posted the relevant bit of lshw -C network, so we need more info.  The line eth0 should show up on is the one with "pan 0 " on it; that's the personal area network, which does some of your interprocess communication (I think, but I've been wrong before :-) ).

The terminal commands appear to be deep magic; they're not.  The terminal, because it's text based, gives you more info if you know what to ask, but you have to ask the right questions, and there's no visual clues like you get with a GUI.  A couple of tips: if you aren't sure of any command, type " man xxxx" and you'll get a number of pages of detailed (often too detailed) info; when you don't know the command to query "apropos xxxx" will come up with a list of commands relating to xxxx.

Occasionally it's your network.  A page I refer back to on troubleshooting networks is [here at Linux journal.]("http://www.linuxjournal.com/content/troubleshooting-network-problems")

Post back if you need a hand.

---

### Post by madeye1 on 2009-10-14
I'm going to read through the link you added, thanks, looks interesting ... i'll either learn alot of my brain will explode ... good times either way.
 
But to respond to your comment :> **coffeeaddict22 said:**
> You haven't posted the relevant bit of lshw -C network, so we need more info. The line eth0 should show up on is the one with "pan 0 " on it; that's the personal area network, which does some of your interprocess communication (I think, but I've been wrong before :-) ).
.... I re-ran "lshw -C network" in the terminal, and got exactly the same thing as I posted above.  I should mention however, that I forgot to include the first line below the command Ishw -C network which was:
"WARNING: you should run this program as super-user."
Which doesn't make any sense because to the best of my knowledge ... I'm ON the main/super-user account !!!   :confused: :)

I'm sure something isn't set up right but have no idea what so I'll try reading through all of the infor on the trouble shooter you linked to and see what happens.

---

### Post by madeye1 on 2009-10-14
btw .... I figured out that when using terminal I need to indicate "su" so get to super user .... but when I do and it asks for Password: ...... its not accepting the password I remember vividly giving it ........ what the heck do I do now ???????!??!?!!! .... i'm sol huh ??!! ... sigh

---

### Post by coffeeaddict22 on 2009-10-14
Madeye,
Ubuntu is designed for people not that familiar with Linux.  A superuser terminal is considered bad form, and the forum moderators tend to get grumpy about people advertising how to get into one.  It's not that you can't, but new users don't** want** to be able to completely trash their system, and root user gives you the keys and lets you go.

The (much) better alternative is to preface the command you want to run as a superuser with "sudo "; if you realise only after you've run it," sudo !!" will replay the last command in superuser mode.  That way you're never running in root without being aware of it, and the protections in the system help you to not gomer up.

You shouldn't be able to start up the system without your password, so I assume you're putting the wrong one in.  try your login pwd.

For all that, the important info in lshw was what your driver is.  Try retyping with a capital C, not a small one.  If you can't see it, what's the output of ```
lspci
``` assuming we're looking at a built in card.  And what sort of network?  Wired or wireless?

---

