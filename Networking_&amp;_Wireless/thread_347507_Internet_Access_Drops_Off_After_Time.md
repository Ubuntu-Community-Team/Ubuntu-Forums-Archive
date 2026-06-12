---
title: "Internet Access Drops Off After Time"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by Burgresso on 2007-01-27
My internet connection has starting to go down for some reason - I'll work on the net fine, for hours, then I'll leave the computer for an hour or two, and the connection is out. Other computers at get on fine, so I can confirm that the network is still there. I've only been able to get it back by restarting :neutral: 

I've been researching this in the forums and found that running 
```
sudo /etc/init.d/networking restart
```

May do the trick. I does not seem to work, though; here's the output:

```
There is already a pid file /var/run/dhclient.ra0.pid with pid 3374
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:12:17:8c:a4:d5
Sending on   LPF/ra0/00:12:17:8c:a4:d5
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:12:17:8c:a4:d5
Sending on   LPF/ra0/00:12:17:8c:a4:d5
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

After running it, there is no access. Before running this it would "think" - firefox would "pretend" that its connecting and the connection would time out. This makes it throws a "page not found" error.

Here is my  /etc/network/interfaces:

```
auto lo
iface lo inet loopback

##To disable ethernet on startup
##iface eth0 inet dhcp

##auto eth1
##iface eth1 inet dhcp

##auto eth2
##iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





iface ra0 inet dhcp
wireless-essid [network]
wireless-key [passcode]

auto ra0
```

I've commented out the ethernet connection, obviuosly :)

Thanks so much for any advice and help!

regards,

burgresso

---

### Post by Dr. Nick on 2007-01-27
Sometimes setting a static IP address has cleared up similar situations, not sure if it would work in your case or why yours is messing up.

---

### Post by Burgresso on 2007-01-27
Thanks Dr. Nick! (said like it would be said in the Simpsons :) )

Well, how do you set up or find a static IP?

---

### Post by Dr. Nick on 2007-01-27
when the internet is working find out what ip you have, use

ifconfig eth0

from a console to see it, leave the window open so you can refer to it later.

If you are in gnome go to the network control panel or find the network control under kde if you use that. If you dont use either or want to do it by hand it will be set in the /etc/network/interfaces: file you posted, I forgot the exact syntax but would be similar to this, You may have to look up the exact variables you need to set


##auto eth1
##iface eth1 inet static
ip address xxxx
subnet xxxx
gateway xxxx

That cured a similar problem I had in windows, basically when teh computer went to renew the ip if couldnt get it, setting a static stops the auto renew

---

### Post by RandomJoe on 2007-01-27
Interesting coincidence - I just installed Edgy on a spare laptop, and plugged a D-Link 54G PCMCIA card in, which I was pleased to discover got recognized and set up.  As I recall, it is using the "ath-pci" driver, which gives me an 'ath0' connection like yours.

My connection also goes away after inactivity, although in my case it's more like 1-2 minutes (say, I'm reading a long webpage or something) and it will come back automatically if I initiate some network traffic (which will fail, but it evidently kicks something into gear to reconnect).  When I look at 'ifconfig' and 'iwconfig', everything looks perfectly fine except on 'iwconfig' the AP MAC switches between the appropriate MAC when connected and "Not Associated" when it's down.

I have found if I open a terminal window and ping my gateway every few seconds, it is _far_ less likely to drop the connection, but will still do it every once in a while.

Haven't had a chance to dig for a solution, just got this running this evening...

My first thought was, I seem to recall some WLAN cards had "power saving features" to disassociate and turn off the transmitter on inactivity to save battery?  My Nokia 770 "tablet" does this - annoying as all get-out!  At least the OS is aware of this fact on that device.

---

### Post by wyeknot108 on 2007-02-01
This happens to me now as well.  Linksys wireless router that works fine with another laptop running Edgy, 24-7 connectivity.  But a fresh Edgy install on a near-identical Toshiba laptop (ATI wireless) finds wireless OK upon reboot.  Then wireless may drop after 5 minutes or 5 hours, as if the IP address expired.  Same/similar iwconfig, etc as above.  If I reboot, everything is back up and running.  Now other line commands seem to help.

No encryption - moot point anyway as the laptop wireless works some of the time.  This laptop worked fine with Dapper.

What gives?  I see similar posts on ubuntuforums but no definitive "whoops, that's a bug."

Thanks.

---

### Post by wyeknot108 on 2007-02-01
That should be "ath0 wireless" - atheros chipset I assume.

And after my wireless drops, if I run sudo dhclient I get a multi-line console message ending with:

No DHCPOFFERS
No working leases in persistent database - sleeping 



Which makes me think router....except the router is working perfectly with the other laptop and this problem only introduced after a fresh Edgy install.

---

### Post by Dr. Nick on 2007-02-01
> **wyeknot108 said:**
> That should be "ath0 wireless" - atheros chipset I assume.

And after my wireless drops, if I run sudo dhclient I get a multi-line console message ending with:

No DHCPOFFERS
No working leases in persistent database - sleeping 



Which makes me think router....except the router is working perfectly with the other laptop and this problem only introduced after a fresh Edgy install.

Did you try setting a static Ip for the interface? I know you shouldnt have to but its worth a shot, not sure what causes the drops to happen. I got a new router and mine stopped, but cant find anything wrong with the old one that would have caused it, I had trouble in windows aswell.

---

### Post by wyeknot108 on 2007-02-01
I haven't tried a Static IP since DHCP from this router has worked flawlessly since I bought it 4 years ago, it's working flawlessly on another Toshiba laptop w/Edgy, and it works flawlessly on this (problem) laptop (also Toshiba running Edgy) upon boot-up (i.e. DHCP gives it an IP address, wireless is working), but then loses the DHCP offer/address, maybe upon re-subscribing.  Just re-boot the laptop and, voila, DHCP/wireless is working again.

Ugh.

---

### Post by JediDuck on 2007-02-05
I have a similar problem and I'm running AMD64 Edgy.  I couldn't get my wifi working with DHCP at all, so I swapped to static IPs and now the wifi works, but again the network just seems to drop off after a random amount of time (anywhere from 5 minutes to an hours).

```
sudo /etc/init.d/networking restart
```

Does the trick for me, but obviously I'd prefer not to have to keep typing this in every so often.  Anyone found the solution (or even identified the problem) yet?

---

### Post by flauros on 2007-12-22
Hi!
I've been tring to fix up this problem for days but still can't find a solution.
Any good news?

```
sudo /etc/init.d/networking restart
```
works fine for me too, but it's so boring: the connection drops down after just 5 minutes of inactivity.

Anyway... a few details of my software - hardware if it can give any help:
Ubuntu 7.10
notebook Hp Pavilion zv5000
wireless connection with Broadcom BCM4306 using broadcom's drivers installed with ndiswrapper
connection shared by a modem/router
static ip address
wpa encryption
wpa supplicant (network manager completely removed)

By the way: sorry for my bad English, thanks in advance for any help and Merry Christmas :)

---

### Post by cyclo on 2007-12-22
I am having the same problem with a intermittent getting dropped from the internet.  I have a Dell 1521 laptop and I am waiting to see if this is a Linux Bug as it seems to hit a lot of people.  I found that changing the connection setting and then resetting it back fixes it but it is annoying

---

### Post by gilf on 2007-12-22
I have a growing suspicion that many problems of this type are occurring not because of DHCP leases but because of power management software. This would tend to create a situation where one computer could stay connected and another couldn't on the same router.

I'm wondering if ACPI software is putting the NIC chips to sleep inappropriately.

It seems to me that a test could be performed  by temporarily turning off ACPI  -- and I suggested it to one user in the thread I wrote. In his case the card itself would turn off completely, your problems here are more like sleep mode. ACPI bios kernals in some laptops are known to be buggy, and in combination with some special Linux chip drivers might be problematic -- just a guess, so far. I could be totally off base.

Anyway the relevant thread and posts are number 72 and number 77 on page 8, here:

[http://ubuntuforums.org/showthread.php?t=603154&page=8](http://ubuntuforums.org/showthread.php?t=603154&page=8)

Unforunately the person I was trying to help never reported back.

If someone here wanted to test this, I'd greatly appreciate the information. Turning off ACPI is strictly temporary, by the method shown, and it will return after a reboot. Post 77 has the community doc reference and the method for turning it off.

hope this helps.

---

### Post by flauros on 2007-12-23
IT WORKS! :biggrin:

First of all let me say that I'm almost sure it's not because of DHCP simply because on my router is disabled: we all use static ip addresses and so we don't need it.

Reading lots of posts in these days on this and other forums I realized it could depend on some power management settings me too. It was almost obvious: it always worked fine from start up until I switched off the pc, but if I didn't use the connection for just 5 minutes I had to use "...networking restart".

In another topic I found out that adding "apm=off pci=noacpi" on kernel's boot line in grub's menu may do the trick. After first try I had to delete "pci=noacpi" because I had big problems with sound (beggining of the startup sound looping continuosly).
Leaving just "apm=off" didn't solve the problem.

Now I tried adding "acpi=off" as gilf said in the topic he linked and now I'm writing you after leaving my laptop without using the connection and even with the screen close for more than 1 hour.
No networking restart needed. \\:D/

**A few details for newbies like me: :p**
To apply this change permanently just edit the /boot/grub/menu.lst file.
Your kernel line should look like like this more or less
> kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=09ade1d6-eb60-4199-bbea-f0fec689abaf ro quiet splash
Just add at the end a space and 
> apm=off

Don't forget to check if it works first, by editing the boot command line at start up: when you are on grub menu select the kernel you want to boot and press "e". Now select the kernel line (usually the second one): it just starts with "kernel" and press "e" again. Go to the end of the line and add " apm=off". Press enter and then, with the kernel line selected press "b" to boot using the changes you just applied. If the system starts and you don't notice any problems you can change it in the menu.lst file as described above, so you don't have to edit it at each start up.
I'm not sure but probably you will have to do this each time a new kernel will be installed.

Hope it will work for everyone with the same problem!
Thanks a lot to gilf who solved this big big problem (at least on my pc).

---

### Post by gilf on 2007-12-23
> A few details for newbies like me:
To apply this change permanently just edit the /boot/grub/menu.lst file.
[COLOR="Red"]Several warnings, however!
[/COLOR]
I meant this as a test to try to discover a possible cause. 

**That's why I suggested the temporary test.**

1.) Making it permanent will disable ACPI which is your advanced power management software. 

2.) APM is an older power management scheme. Turning both off may not be necessary -- this would depend on the individual computer. I didn't mention APM because I have reason to believe that ACPI is the real problem. However if this doesn't work alone, you can test it out with APM turned off alone or in combination with ACPI.

But in both cases you are disabling power management functions. Now it may well be that you don't want to control power management with ACPI, (or APM) but frequently laptop users may find that its features are valuable to them.

The best workaround is going to be to try to correct the software which interfaces with ACPI and card drivers. Not eliminating power management software.

These fixes may already exist for a particular computer model or NIC.

You should actually try to research ACPI or NIC driver updates for your combo, IF, and only if, the above temporary test works for you.

I'd like to hear feedback from others as well here about this test -- successfull or not? Along with a description of your computer and network card/chips.

If a pattern emerges, we need to write a bug report with repeatable steps to reproduce.

Thanks

---

### Post by oraknabo on 2007-12-23
I have an ASUS F3T that works perfectly on a direct ethernet line and will run for weeks without a single network problem, but if I switch to wifi, I'm lucky if I get 3-4 hours before it drops out. After that there's nothing that I can do short of rebooting to bring it back. It drops out even faster if I do any FTPing or transfering files across my LAN.

lspci identifies my card as "01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)". I've seen a number of threads about wireless problems on ubuntu with certain chipsets, but most are about the wireless not working at all. I'm pretty sure there are no router problems because it works on the line and none of my other computers have any problems with wifi.

I can only assume that there's something wrong with the restricted HAL driver. Would it help for me to switch to ndiswrapper? I'm going to try switching to a static IP and see if there's any difference, but I'm finding even trying to use wifi very frustrating.

---

### Post by gilf on 2007-12-23
> **oraknabo said:**
> I have an ASUS F3T that works perfectly on a direct ethernet line and will run for weeks without a single network problem, but if I switch to wifi, I'm lucky if I get 3-4 hours before it drops out. After that there's nothing that I can do short of rebooting to bring it back. It drops out even faster if I do any FTPing or transfering files across my LAN.

lspci identifies my card as "01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)". I've seen a number of threads about wireless problems on ubuntu with certain chipsets, but most are about the wireless not working at all. I'm pretty sure there are no router problems because it works on the line and none of my other computers have any problems with wifi.

I can only assume that there's something wrong with the restricted HAL driver. Would it help for me to switch to ndiswrapper? I'm going to try switching to a static IP and see if there's any difference, but I'm finding even trying to use wifi very frustrating.

Have you tried the ACPI turn off  test (above)?

---

### Post by oraknabo on 2007-12-23
I followed your instructions for turning ACPI off and even though I haven't been running for long enough to see a timed dropoff, I moved a few gigs worth of files from my laptop to my server while streaming some music from the server and doing various other LAN activities and surfing the web and the connection hasn't died yet. This alone is a huge step forward.

If this does solve the problem, does this point to a long term solution? I'm don't have any idea of where to go from here.

---

### Post by flauros on 2007-12-23
> **flauros said:**
> IT WORKS! :biggrin:


Unfortunately I have to change it in "It didn't work" :(
I was too happy to notice that my sound card doesn't work any more.
I had to remove the apm=off and so my connection drops again after 5 minutes of inactivity.

Let me say that this sucks :(
I just hope that this will help someone else to find a way to fix it once for all.

---

### Post by gilf on 2007-12-23
Flauros and oraknabo,

Yes, the test proposed is not a cure, but it does explain what what is happening. The more people who can confirm this test, the greater the chance that a real solution can be developed.

Turning off ACPI and/or APM naturally affects other power management functions which may depend upon it -- that is why it was proposed as a temporary measure.

But it seems highly likely that some network cards on some computers are being shut down by power management software.

It would be helpful if you would indicate your computer type and network card type here. There may already be specific drivers developed for you to handle these problems.

If not, this information can be used to file a bug report, once it is a little clearer that it is a common occurrence. Two computers already is a good start.

Edit:

This launchpad bug report looks like it may be applicable here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/40125](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/40125)

---

### Post by flauros on 2007-12-23
> **gilf said:**
> It would be helpful if you would indicate your computer type and network card type here. There may already be specific drivers developed for you to handle these problems.

Already wrote in my post above, but you know... "repetita iuvant" :)

Ubuntu 7.10
notebook Hp Pavilion zv5000
wireless connection with Broadcom BCM4306 using broadcom's drivers installed with ndiswrapper
connection shared by a modem/router
static ip address
wpa encryption
wpa supplicant (network manager completely removed)

For the Broadcom BCM4306 and other Broadcom network cards is also available an open source driver ([http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)) but I can have a working connection only if I'm close to the router. 10 meters far from the router is enough to don't have any connection... that's why I'm using again the driver with ndiswrapper.
Maybe I should try it just to be sure if the connection drops or not with the open source one but I'm not sure how to completely remove the driver installed with ndiswrapper :(

Edit: 
> **gilf said:**
> This launchpad bug report looks like it may be applicable here:

[https://bugs.launchpad.net/ubuntu/+s...ger/+bug/40125](https://bugs.launchpad.net/ubuntu/+s...ger/+bug/40125)
Personally I think they are different problems: it talks about network manager, sleep and hibernate but I don't use anyone of them.
I removed the network manager and I never use sleep or hibernate.
Really can't understand the right way to fix it. If I don't download anything for 5 minutes my connection doesn't work anymore even though I'm using the pc. For example if I write an e-mail or a post in a forum (and I take more than 5 minutes) I have to restart the network to be able to use the connection. The same happens if I switch on the pc and I don't type username and password immediately: the system will start up showing the connection as it's working but no way to download anything.

Should we try to report the bug on launchpad?

---

### Post by gilf on 2007-12-29
One thing you can do if you have identified one of the power management schemes as problematic with your hardware and Ubuntu is to make sure that you have updated your computer's BIOS to the latest version.

APM and ACPI are directly linked to your BIOS. Many BIOS updates have historically included corrections to power management functions.

If you have to disable a power management function, it may affect other aspects of your computer -- battery indicators, for example, sleep mode, etc. There's a report here of a sound problem.

I found in my own case with an earlier Kanotix install on a Thinkpad 600E with both ACPI and APM disabled that the battery indicator was gone. I downloaded a linux app that provided a battery indicator and was back in business. If  memory serves I also had to alter something in ALSA drivers to get sound working.

These are workarounds, but they may or may not allow you to use Ubuntu on your machine.

The best solutions would be BIOS updates that corrected the problem, or elimination of a bug in Ubuntu if there is one. 

A bug report can be filed by you, if you can provide steps to reproduce the problem with a full hardware description, and you are sure it isn't already filed.

---

### Post by oraknabo on 2007-12-30
This was specific to my hardware, but I found this Gentoo page today:[http://gentoo-wiki.com/HARDWARE_Asus_F3T#Wireless](http://gentoo-wiki.com/HARDWARE_Asus_F3T#Wireless) - and I think it has helped with my problems. I had to run these modprobe commands to fix ACPI for my Asus notebook:
```
 modprobe ath_rate_sample
 modprobe wlan_scan_sta
 modprobe wlan_tkip
 modprobe ath_pci
```
I'm not very experienced with modprobe so I can't explain what these commands are doing, but I've been on my wifi connections for hours now without any dropoff.

---

### Post by alecspoons on 2008-01-22
Total beginner here...

I'm having this exact same problem.
Restarting the network doesn't work.

Oddly, it is only internet access that drops off. I can still access my Linksys router's admin in the normal way, so it can't be something that is affecting all network access.

Same issue? Or am I barking up the wrong tree here?

---

