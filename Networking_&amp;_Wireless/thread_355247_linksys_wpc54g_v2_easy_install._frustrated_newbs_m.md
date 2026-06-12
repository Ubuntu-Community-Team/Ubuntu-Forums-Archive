---
title: "linksys wpc54g v2 easy install. frustrated newbs must read"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by tjtansey on 2007-02-07
Ok after much kicking sreaming and even considering using my wireless card as a skipping rock, I finally got it to work.  These are the steps I used and it works great now.  If an extremely dumbed down set of instructions can be found elsewhere I couldn't find them.  If this helps even one person it's worth it.

Download ndiswrapper

download windows driver

open terminal

unzip ndiswrapper

mkdir linksys

unzip driver to linksys

cd linksys

sudo ndiswrapper -i (driver inf file)

cd /
sudo modprobe ndiswrapper
sudo nano /etc/modules
insert line "ndiswrapper" to last line in file then save and exit

****reboot and I was ready to go. (This is the key step that I couldn't find in any direction: when to reboot)

Hope this helps, any question, I'll wrack my brain to remember.  If you're scared to try Linux, just do what I did, wipe out your windows boot sector:D  No looking back now and happy for it.

---

### Post by gradedcheese on 2007-02-07
just a couple of comments: "cd /" here is not needed (that just changes directory to /, but you don't need to do that for any reason).  Also, you don't need to reboot Linux for any reason other than kernel upgrades, though there's nothing wrong with rebooting.  I suspect that you could have inserted the ndiswapper module (sudo modprobe ndiswrapper) and restarted networking (sudo /etc/init.d/networking restart) to accomplish the same thing.  The reason for adding ndiswrapper to /etc/modules was to tell the OS about ndiswrapper, so that it's loaded automatically on bootup, hence rebooting worked.  Anyhow, good job on getting your wireless working!

---

### Post by tjtansey on 2007-02-07
Great info, but I couldn't find it anywhere.  Now that you've put it in this post, maybe I can write the complete idiots guide to installing linksys wireless cards.  It will of course be authored by me :D  I'm sure I'll have follow up volumes as well;)  I have a feeling Wine will be next.

You were a great help if I didn't tell you that earlier.

---

### Post by dmizer on 2007-02-07
the inf files for the linksys driver that i've been using require editing in order to make them work.  if you were not required to do editing, where did you get your driver?  and, are you sure you're card is using the ndiswrapper module to drive it instead of the acx module?

my howto: [http://www.ubuntuforums.org/showthread.php?t=324148](http://www.ubuntuforums.org/showthread.php?t=324148)

---

### Post by gradedcheese on 2007-02-07
Oh, 'glad to help.  There are some things that a lot of guides that you'll read assume.  Don't be intimidated, but basically some stuff is common knowledge, though they should definitely have explained that you need to modprobe at least.  A lot of documentation was written for/by users who are familiar with the usual Linux facilities but I've noticed that this is changing and things are becoming more thorough (especially with Ubuntu documentation).  

Some general info: /etc/modules contains the names of the modules (drivers) to load at boot time.  The 'modprobe' command attempts to insert a module when you run it, also inserting any modules it depends on.  'insmod' just inserts a module and 'rmmod' attempts to remove a module.  'lsmod' gives you a list of the modules that are currently inserted.  

The /etc/init.d/networking script looks at your list of network interfaces (take a look at it, it's /etc/network/interfaces) and initializes them accordingly.  It runs on bootup but you can access it at any time.  It takes 'start', 'stop', and 'restart' arguments ('restart' just stops and then starts).  A stop brings the interface(s) down, a start brings them up.  So next time you need to mess with network interfaces, you'll probably know enough to avoid an unneeded reboot.  This is one of the many advantages over Windows, where it seems that one reboots constantly.

---

### Post by tjtansey on 2007-02-07
> **dmizer said:**
> the inf files for the linksys driver that i've been using require editing in order to make them work.  if you were not required to do editing, where did you get your driver?  and, are you sure you're card is using the ndiswrapper module to drive it instead of the acx module?

my howto: [http://www.ubuntuforums.org/showthread.php?t=324148](http://www.ubuntuforums.org/showthread.php?t=324148)

I downloaded the driver directly from linksys the driver I used is LSTINDS.INF and I didn't have to do any mods to it, although in an earlier attempt I saw that you were supposed to go in and ensure LSTINDS were always caps.  When I looked in mine they all were.

---

### Post by dmizer on 2007-02-07
> **tjtansey said:**
> I downloaded the driver directly from linksys the driver I used is LSTINDS.INF and I didn't have to do any mods to it, although in an earlier attempt I saw that you were supposed to go in and ensure LSTINDS were always caps.  When I looked in mine they all were.

if that's the case, linksys may have updated that driver ... again.  *sigh*.  i'll take another look tonight and see if i need to update my howto again.

again though ... did you blacklist the acx module?

---

### Post by tjtansey on 2007-02-07
No I didn't blacklist the driver.  I intended to as per your howto, but in my frustration forgot to and everything seems to be working fine.  Actually, I've never seen download speeds even close to this when I was running XP.

I wasn't trying to start any controversy, just trying to make life a little less frustrating for the next poor schmo like me that comes along and has no clue what commands to use and what steps to take when.

---

### Post by gwen@trogdor:/ on 2007-02-09
Preface: I am a total newb.  I have used Ubuntu on a desktop for a while, and without any serious challenges. So now that I've installed it on a laptop, and I need it to work with a wireless card, I have encountered my first real problem. So far it's Ubuntu:1, me:0.  I scanned the forums before buying, and chose the linksys because people seemed to be having a lot of success.

I have the WPC54G v3, and I have tried to install the drivers (bcmwl5.sys and bcmwl5.inf, and differently with lsbcmnds.inf-from the driver package I downloaded from the Linksys website.  No matter which set of instructions I follow, I can't seem to get it working. I have blacklisted the drivers as described in the thread above, but there is still a wireless connection listed in my network types, although it is unconfigured.

Each time I try I get to some line in the instructions where a command doesn't work, and i get a bash error. 
I upgraded from Dapper to Edgy to see if doing it in Edgy worked better, but still no success.  Can anyone suggest which version of Ubuntu will work best, and which version of ndiswrapper? I have seen several versions, and downloaded it from the site and via the synaptic package manager, and so far neither way worked.  

Any help or suggestions would be very much appreciated. 
Thanks,
gwen

---

### Post by tjtansey on 2007-02-09
Gwen,
dmizer and I have been woorking on a new how to for the wpc54g.  I have version 2 if you have a different version reference linksys download site and plug appropriate file name in (I hope).
Also before you try to install at all remove any currently installed version of ndiswrapper.

to remove any previously installed drivers, run the following commands after re-installing ndiswrapper.   ndiswrapper -l (will list installed drivers)  sudo ndiswrapper -e (driver name **no ext needed**) this will remove old drivers
 
Here is my how to:
Installation of Linksys WPC54G v2 wireless card
remove card 
in terminal:
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.8

mkdir linksys
cd linksys
wget [ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip](ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip)
unzip wpc54g_v2_driver_utility_v2.0.zip

At this point you have the software you need to install your driver

Now a little housekeeping to ensure you don't any future problems, we are going to convert the following filename to all CAPS this ensures your driver recognizes the file
mv tnet1130.sys TNET1130.sys

Now we are going to install the drivers
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -i LSTINDS.INF
sudo modprobe ndiswrapper

Now we are going to set up your system to initialize on boot-up
sudo nano /etc/modules

add the following line at the end of the file
ndiswrapper
then ctrl-x
y
enter
Now insert your card and enter
ndiswrapper -l

the screen should read:
Installed drivers:
lsbcmnds                driver installed 
lstinds         driver installed, hardware present
Disable your wired network connectio
Now run dmesg and look for the following lines:
ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.18) loaded
ndiswrapper: using irq <irq#>
 wlan0: vendor: 'TNET1130'
wlan0: ethernet device 00:0f:66:d8:a7:88 using NDIS driver lstinds, 104C:9066:1737:0033.5.conf

Now restart networking with the following command:
sudo /etc/init.d/networking restart
configure your wlan in System>Administration>Networking
Good luck I hope this helps

---

### Post by czarjosh on 2007-04-11
I did all of this and had no problems.    Except my card does not seem to be detected.

when I run ndiswrapper -l

the screen reads:
Installed drivers:
lsbcmnds driver installed
lstinds driver installed

Also I believe my wireless card is labels as eth1 instead of wlan0.

i get a green power light on the card, but no link.

---

### Post by tjtansey on 2007-04-12
Did you have your card in when you installed the drivers?  Also did you restart networking?

---

### Post by czarjosh on 2007-04-13
I did have it installed.  I did restart networking

---

### Post by tjtansey on 2007-04-14
Try uninstalling the drivers using ndiswrapper -r (driver) then reinstall but make sure the card is unplugged when you do it.  Also are you using edgy or feisty?

---

### Post by whoKnew on 2007-05-21
i'm almost there!

i got to the end of the instructions, and i think everything worked out ok.
one minor detail

in the 2nd last paragraph, my output reads
> wlan0: ethernet device 00:14:bf:48:da:48 using NDIS driver lstind

instead of 
> wlan0: ethernet device 00:0f:66:d8:a7:88 using NDIS driver lstinds

..i don't know if this makes a difference.

all i know is that some sort of wireless network is detected (for a change), and that the Power light on the card is on (for a change).

now here is the embarassing part:

i'm completely new to linux/ubuntu and i'm not sure how to go about configuring my wireless network settings as per the instructions. the whole process kind of confuses me. i've checked the "enable this connection" checkbox, but i'm not sure what to enter after that. how do i determine what my network name is? my password? do I want manual configuration or DHCP? i installed Edgy from the alternate install cd and deliberately did not configure DHCP settings during installation for reasons of not knowing how.

i know it's a simple question, but i'm clueless and SO CLOSE to getting wireless working! 

thanks!

---

### Post by dmizer on 2007-05-22
well, it should be a network you set up, so you should know these settings.  if it's a hotspot, these settings should be posted somewhere.  otherwise, you can also run this command and post the output if you're still unsure:
```
sudo iwlist wlan0 scan
```

> **whoKnew said:**
> i got to the end of the instructions, and i think everything worked out ok.
one minor detail

in the 2nd last paragraph, my output reads
>  wlan0: ethernet device 00:14:bf:48:da:48 using NDIS driver lstind
instead of 
[quote]wlan0: ethernet device 00:0f:66:d8:a7:88 using NDIS driver lstinds[/quote]
i don't see anything there you'll need to worry about.  the hex numbers (00:14:bf:48:da:48) are your cards mac address. these are unique to every card, so they shouldn't be the same as what was posted in the howto.

---

### Post by tturrisi on 2007-05-22
You don't need ndiswrapper for cards that have an acx chipset!  The acx driver & firmware work just dandy.

---

### Post by whoKnew on 2007-05-22
you're right, at first glance it seems like a stupid question, but here's the situation:

my housemate has a linksys router that provides a wireless hotspot for our house. he is the one who set up the network, although i now realize it was probably kind of flukey. it's set up in windows.

he, too, is kind of confused by wifi and when we both tried to configure my ubuntu connections to hop onto the network we couldn't come up with anything. 

i have the security key and the password for the network, as well as the ESSID (which i got from the
**sudo iwlist wlan0 scan** command you kindly provided me). it lists a few wireless networks within range of my card, all of which are "mode: managed", which i assumes means that they are secure and require a password to connect to. i briefly found one that said "mode: ad-hoc" -- does this mean it is unsecure? i couldn't connect, anyhow.

so that is my dilemma. 
i feel like i have the tools, but i don't know how to use them. kind of pathetic, i know.

fyi, **sudo iwlist wlan0 scan** yields:
> cell 01 - Address: 00:16:B6:E6:54:4C
ESSID:"linksys_SES_10543"
Protocol: IEEE 802.11b
Mode:Managed
Frequency:2.437 Ghz (Channel 6)
Quality:0/100 Signal level:-60dBm Noise level: -256dBm
Encryption key: on
Bit rates: 1Mb/s; 2Mb/s; 5.5 Mb/s; 11Mbps; 6Mbp/s; etc...
Extra: bcn_int=100
Extra:atim=0
IE: WPA Version 1
Group Cipher: TKIP
Pairwise Ciphers (1): TKIP
Authentication Suites (1): PSK

---

### Post by dmizer on 2007-05-24
ad-hoc means from computer to computer (similar to a direct cable connection).  managed is merely a managed network (most are).

looks like you're network has wpa enabled, and i have no ability to enable or test wpa so all i can tell you is to look for howto's on wpasupplicant. for example: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

