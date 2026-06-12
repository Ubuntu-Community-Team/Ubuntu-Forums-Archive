---
title: "No WLAN connection (Dual Boot w/Vista)"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Pres B on 2009-04-19
Hey guys..  I'm definitely a noob/novice/beginner or whatever people who are just learning about Linux are called these days.  I am having trouble establishing a WLAN connection?

I am using my laptop - HP Compaq Presario CQ50 Notebook.  AMD Athlon Dual-Core QL-60 1.90 GHz... 1GB RAM. 

Nework Adapters: 
Atheros AR5007 802.11b/g WiFi Adapter
NVIDIA nForce 10/100/1000 Mbps Networking Controller


I installed Ubuntu 8.10 to dual boot with Vista -Home Basic (32 bit) and set up my partitions like this:

/dev/sda1 ntfs 93,200 MB
/dev/sda2 ntfs 10,049 MB
/dev/sda3 swap 1,998  MB
/dev/sda5 ext3 5,996  MB - mount point'/'
/dev/sda6 ext3 8,776  MB - mount point '/home'

(The second primary partition is a D drive..for recovery.  It was already set up when I got the laptop.)

I don't have a lot of space dedicated for Ubuntu still because I am learning.  I set up the home partition because I have a feeling I'll grow to like Linux and use it for a long time and don't feel like "starting over" for every new distro...I can always give it more space when needed.

I didn't set a mount point for my ntfs partition, but I wish I did so that I can access my music.

**Finally, my question:**

What do I do to try to diagnose why I don't have a WLAN connection?  When I open the Network Manager my wireless network is not listed.  I tried to add it, (inputting SSID, etc.) but I don't think I did that correctly.  I am not looking for someone to just find the answer for me per se, but more to direct me as to how to diagnose this issue, and help me figure it out for myself.  

Thanking Everyone in Advance,
Pres B


***If this was covered in depth in another post can someone post the link for me?

---

### Post by Bucky Ball on 2009-04-19
Firstly, is the light on to indicate the card is active? (If there is one.)

You might try downloading:

```
ubuntu-restricted-drivers
```... From System->Administration->Synaptic Package Manager. Reboot and see if you are offered drivers for the card.

To find the card in Ubuntu, open a terminal and type:

```
lspci
```The card should be somewhere near the bottom. What results do you get when you type in:

```
iwconfig
```The Atheros cards are normally picked up automatically now. Go to:

System->Administration->Hardware Drivers

Is there a wifi driver there not being used? What version of Ubuntu?

---

### Post by lkraemer on 2009-04-19
Check this out:
[http://ubuntuforums.org/showthread.php?t=996311&highlight=CQ50](http://ubuntuforums.org/showthread.php?t=996311&highlight=CQ50)
[http://ubuntuforums.org/showthread.php?t=988691](http://ubuntuforums.org/showthread.php?t=988691)

It shouldn't take you long......All the work has been done for you.

And your Wifi LED WON'T be "ON".

lkraemer

---

### Post by Bucky Ball on 2009-04-19
See if you can get the restricted hardware drivers to pick up the card first at 'System->Admin->Hardware Drivers'

---

### Post by Pres B on 2009-04-19
Hey everyone, thanks for responding so quickly!  Let me try this stuff and see what happens.

THANK YOU SO MUCH!!

---

### Post by Pres B on 2009-04-19
Okay, tried a few things...

-Downloaded drivers for my Atheros card.

Once I was done with that I booted back into Ubuntu went to system->amdin->hardware drivers and my card has the green light and says "this driver is activated and currently in use."

When I code: iwconfig  I get:

lo    no wireless extensions
eth0  no wireless extensions
pan0  no wireless extensions

Any suggestions?

---

### Post by LinxMan on 2009-04-21
Hah, I should learn to actually look at others forum posts before posting mine... wow. I epic failed.
Anyways, I have basically the Same computer. 2 Slight differences, there is an Intel processor 2.0ghz, and my memory is bumped up to 3gb of memory.
I would look into what Bucky Ball (TY in advance) said, but I can't right now, stupid thunderstorm. ](*,)

---

### Post by ugriffin on 2009-04-21
I've got an Atheros too... here's what worked for me....


Get an ethernet connection up... 
Open Adept, and look for "Windows Wireless Drivers".
Download a .inf driver for your card...
Install it using "Windows Wireless Drivers".
Reboot.

You're good to go.

---

### Post by LinxMan on 2009-04-21
> **ugriffin said:**
> 
Get an ethernet connection up... 
Open Adept, and look for "Windows Wireless Drivers".
Download a .inf driver for your card...
Install it using "Windows Wireless Drivers".
Reboot.

You're good to go.
Tried that, my thing says "Connection Lost". Although it seemed to install the driver correctly, it isn't connected. I use a windows configured network (if that does anything different) and I can't seem to set my settings correctly. Is there somwhere I can figure this thing out?

---

### Post by ugriffin on 2009-04-21
Does it display wlan0 in the Network manager?

---

### Post by Noise... on 2009-04-21
I had wireless issues ALL last week (and ended up having to reinstall Ubuntu because of it), so I learned quite a bit. Hopefully my issues and resolutions can help with your problem.

First, go to System>Administration>Network

Is your wireless device listed there? If you have any sort of option for wireless, IT IS WORKING.

Don't mess with drivers if you see it there. I completely botched my wireless by following the "get Windows drivers!" advice. It wiped out my default drivers, so I had to reinstall.

If it's there, go download wicd. It's a wireless manager, and works great. I got nowhere with the stock one, but Wicd worked right off the bat.

---

### Post by ugriffin on 2009-04-21
Do you have an Atheros? Windows drivers for Atheros are pretty functional on ndiswrapper. Considering I have an atheros and that it's what makes my computer tick, I recommended it.


It depends. If wlan0 appears in the network manager, I recommend getting wicd. Otherwise, there's still something wrong there.

---

### Post by Noise... on 2009-04-21
> **ugriffin said:**
> Do you have an Atheros? Windows drivers for Atheros are pretty functional on ndiswrapper. Considering I have an atheros and that it's what makes my computer tick, I recommended it.


It depends. If wlan0 appears in the network manager, I recommend getting wicd. Otherwise, there's still something wrong there.

Mine is an Intel Wireless adapter. However, I wanted to suggest that he check to see if it's working properly before going and wiping out the default drivers like I did.

I know ndiswrapper has helped quite a few people, and is recommended often with wireless issues. However, there's no need to go to that extent if his wireless device is already functioning.

---

### Post by Bucky Ball on 2009-04-21
I should add to all of this: Plug in an ethernet cable if you have one!

Get online, get updates, that should pick up the Atheros and offer you the appropriate restricted drivers. Accept, install, then you should be asked for the WEP security key and the name of your AP (access point, normally your router). And that should be it.

Avoid ndiswrapper at all costs. That should not be necessary and madwifi is the tool anyhow and if you try this, it *should* work without you having to do any screwing around. I built a machine after christmas and got a wireless card with Atheros and that is what worked for me.

Sorry, just dawned on me. Plug that cable in before doing anything else and establish a cable connection.

---

### Post by LinxMan on 2009-04-22
I will have to check. I will as soon as I can get charging.
(Edit) Updating my Linux now, just waiting for it to finish

---

### Post by LinxMan on 2009-04-23
Hm still nothing... that is weird.  It found my wireless card, but it just wont connect to my wireless network. UGH. Starting to think about re installing Ubuntu. :(

---

### Post by ugriffin on 2009-04-23
Did you install the new drivers? (madddog or ndiswrapper, it doesn't matter).

Have you installed wicd? Sometimes wicd works better than Network Manager, especially in KDE.

---

### Post by Saint_ on 2009-04-23
Yo, I just got done (literally, 10 minutes ago) fixing my Atheros wireless problem. Check out the thread @
[http://ubuntuforums.org/showthread.php?t=1125494&highlight=atheros+ar242x](http://ubuntuforums.org/showthread.php?t=1125494&highlight=atheros+ar242x)

It's a different model, yes, but I believe it should give you quite a bit of insight. Good luck.

---

### Post by LinxMan on 2009-04-23
well I am in the process of getting 9.04 so I have to wait. (Man it's taken at least an hour now, and its only 70% done.:() I wanna make sure that if 9.04 fixes this problem. If it doesn't, then I will just mess around with it.

---

### Post by ugriffin on 2009-04-23
Do you run Kubuntu or Ubuntu? If you run Kubuntu, 9.04's Network Manager really sucks, so wicd's a Must Have.

---

### Post by LinxMan on 2009-04-23
I'm gonna run Ubuntu for a bit until I get used to that.
Maybe later I will run Kubuntu or Mythbuntu, but for right now, Ubuntu is where im headed.
But I found out that WICD is included in their repositories (thanks for the catch ugriffin) in 9.04, so it should be straight-forward, but with ubuntu, i havent had that luck yet :(.

---

### Post by ugriffin on 2009-04-23
Wicd is included in the repositories, not as a default.

---

### Post by Bucky Ball on 2009-04-23
> **LinxMan said:**
> well I am in the process of getting 9.04 so I have to wait. (Man it's taken at least an hour now, and its only 70% done.:() 

You will find downloading the torrent and doing it that way is much quicker and more reliable.

---

### Post by LinxMan on 2009-04-25
Well, ubuntu 9.04 is installed.
Wireless now is working! yay!
But it's not connecting to any secured networks... nay.
Any Ideas?
(PS tried Wicd, it didn't find my wireless card :()

I tried it on an unsecured network while I was in town, and it worked perfectly. :(

---

### Post by Bucky Ball on 2009-04-26
> **LinxMan said:**
> Wireless now is working! yay!
But it's not connecting to any secured networks... nay.


Is it finding any? If it is identifying yours but you are not connecting, you need to set the correct name of your Access Point (AP - router) and the correct security details on your machine. If these are not already set in the router, that is probably why you're not finding your AP and network and you will need to get into the router config and set that up.

Set the router as a DHCP server (so it assigns your machine an IP address). After that, goto System->Admin->Network, unlock with your password, click on Wireless->Propertites, and set that up with the correct details to match the ones you have in your AP. Auto DHCP, AP name and WEP key (security number).

Main thing? Your router/AP should have a name and WEP key set and should be set as DHCP server, your machine should have matching details and be setup to be assigned an IP by the DHCP server.

Hope that all makes sense.

Did you download updates or restricted drivers when you did have it online? When you go System->Admin->Hardware Drivers, what is there and enabled?

---

