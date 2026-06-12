---
title: "Wifi worked in Hoary but not in Breezy"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by TheFifth on 2005-10-16
I have an Inprocomm IPN2220 wireless network adaptor, which worked perfectly under Hoary.  I recently updated my laptop to Breezy and all went well other than the fact that the upgrade hosed all my network access, both the standard ethernet connection and the WiFi adaptor.

I tried everything I could to get it working again and in the end decided to reinstall Breezy from scratch.  Reinstalling has given me back network access through the standard port, however I can not seem to get the WiFi card back up and running.

I've installed ndiswrapper from the repositories and took the following steps:

```

sudo ndiswrapper -i neti2220.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```

Then I configured the connection with my ESSID and WEP key.  These are the exact steps I used in Hoary and everything worked perfectly there.  However, under Breezy I cannot get a connection.  The hardware appears to be working perfectly and the Network Monitor I've added to my panel shows a signal strength of 100%.

I've tried using the network connection applet to configure the connection, manually editing the interfaces file, using a static IP and also using DHCP, nothing seems to work.

ndiswrapper -l reports:

```

Installed ndis drivers:
neti2220        driver present, hardware present

```

iwconfig wlan0 reports:

```

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:0 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:56/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig wlan0 reports:

```

wlan0     Link encap:Ethernet  HWaddr 00:11:E2:02:54:ED
          inet6 addr: fe80::211:e2ff:fe02:54ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:e0207000-e02077ff

```

sudo iwlist wlan0 scanning reports:

```

wlan0     Scan completed :
          Cell 01 - Address: 00:11:95:70:5D:B2
                    ESSID:"my network name here"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-56 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

So the WiFi card is seeing my wireless base station.

The WiFi section of my interfaces config is:

```

# The primary network interface
iface wlan0 inet dhcp
wireless-essid (my network name)
wireless-key (my wep key)

auto wlan0

```

Any help here would be greatly appreciated.  I don't want to go back to Hoary just to get my WiFi adapter working again, especially since I've just wasted a whole weekend installing Breezy and getting it all together.

---

### Post by TheFifth on 2005-10-17
I also have another problem.

For some reason the network at my work does not like the inbuilt network card on my laptop (in Windows and Ubuntu), so I've always used a 3Com PCMCIA card for network access when working.

In Hoary I was able to use the PCMCIA card at work, my WiFi card at home and the internal ethernet port when connecting to other networks.

With Breezy I can't get the PCMCIA card to work or my Wifi.

I'm beginning to think that there is something fundamentally broken with the networking in Breezy, as the problem with the PCMCIA card seems very similar to the problem with my WiFi card.  The hardware seems to be working and the correct modules are all loaded, however I can not obtain an IP via DHCP, or receive any packets when I set the IP manually.

Looking around this forum, it looks like a lot of people are having these problems, but there doesn't appear to be any solution!

---

### Post by knappen on 2005-10-17
Yes that is my experience as well. WiFi under Breezy seems to be a problem for many users, including me.

---

### Post by TheFifth on 2005-10-25
Well it's back to Hoary for me, I've been banging my head against this problem for too long and I need to get some work done!

The strange thing is that I followed the exact steps outlined in the first post in Hoary and everything worked like a charm, so I'm sure that the problem isn't anything I am doing!

Any one have any ideas what's so different about Breezy's networking that's stopping me from getting a simple PCMCIA card, or my WiFi card to work?

---

### Post by Tor M on 2005-10-25
Hi 
I have the same problem with Inprocomm IPN2220.
When I first got my laptop early this summer I tried to install Horary, but gave it up when I couldn`t get anything to work properly.
I hoped that things had gotten better in breezy.
Fiddeling with Breezy I have learnt quite alot.

I have compiled a new kernel and installed the latest ndiswrapper from source.
The only way I get my wifi to work is to connect manually by typing this:

sudo ifconfig wlan0 down
sudo ifconfig eth0 down
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid "XXXXXXXX"
sudo iwconfig wlan0 key open "XXXXXXXXXXX"
sudo ifconfig wlan0 up
sudo dhclient wlan0

This way I get connented, but it`s very irritating to this everytime I log on.
I ofcourse put it in a script, to make it a little easyer.

Another thing that`s annoying is that it takes ages to boot my system without anything connected to eth0.

Maybe I should try Horary again aswell. If everything worked for you guys there, maybe it will for me aswell.

Regards

Tor Martin

---

### Post by MGajh on 2005-10-25
Hi!

I have exactly the same setup on an Acer Aspire 1363 and had no problems using the inbuilt Inprocomm card - installing the current released drivers from Acer's website.

Looking at the iwconfig wlan0 report, the access point Mac address is 00:00:00:00:00:00 so you're not authenticated to the access point. The rest of your output's suggest the card is working OK as the IWlist picks up the router (note the MAC address -this would show on your iwconfig if you were connected).

In my experience, these sorts of problems are usually down to a problem with the encryption key used so I would reinput this in  Network settings making sure that the key type is definately correct (accii or hexadecimal). The other thing to check would be the network name remembering it's case sensitive.

I've no experience with a 3com pcmcia card in Breezy but have used a Netgear one with no problem so perhaps we're talking about the same problem.

Hope this helps!

---

### Post by TheFifth on 2005-10-25
Hi MGajh,

I've noticed that it's not authenticated to the access point, but I just can't get it to do it!  I've checked and double checked the WEP key and all the settings, even tried turning off WEP on the access point and running it open, and it still won't connect.

I've tried using the 'iwconfg ap' command and giving it the address of the base station, but it still will not authenticate.

The ironic thing is that I backed up my interfaces config file when I reinstalled Hoary, copied and pasted the wlan0 section into my new config file, and it works perfectly.  So I can guarantee that the problem was not the WEP key as I'm using the identical configuration in a working Hoary setup.

The 3Com PCMCIA card just works when I plug it in with Hoary (after I've set it to use DHCP or static IP), but with Breezy it's recongised, but will not get an IP via DHCP, or even operate when assigned a static IP.  All very odd!

Tor Martin, it's good to hear that you've managed to get the hardware working (to a fashion) in Breezy, but it does seem like a lot of trouble to go through on every boot!  

One tip for the long boot times though is to lower your DHCP timeout.  This is normally the reason for long boot times when not connected to a network.  On my laptop I have edited the file '/etc/dhcp3/dhclient.conf' and uncommented the line '#timeout 60;' (removed the #) and changed the value to 10.  This lowers the pause on boot to ten seconds instead of a minute.  You may find that you can use a lower value than ten seconds, however it will depend on how quickly your DHCP server responds to requests.  NOTE: I did this in Hoary, but I assume it will also work in Breezy.  Try it at your own risk! :)

Cheers,

Rich

---

### Post by knappen on 2005-10-25
What I discovered, using kubuntu, is that the wep key is just written as stars in the interfaces file. That was one of the reasons why I had problems with my card.

---

### Post by TheFifth on 2005-10-25
Hi Knappen.

I've manually configured the interfaces file and the WEP key is fine.  As I've said, I'm using the same interfaces file in Hoary and it works great.  Very strange!

I'm really tempted to try Breezy again, as I feel that it really SHOULD work and that I'm doing everything right!  But now that I've reinstalled Hoary and spent ages getting everything right, I'm not sure I can be bothered to mess around with it any longer!

---

### Post by TimelessRogue on 2005-10-25
Hey Guys ... it's not just your cards.  I've got the same problem with a Linksys WPC11 v3 that worked from the get-go in Hoary but just will not ... no matter what so far ... work in Beezy.  I reverted to Hoary and all was well again.  It even worked with Beezy Live CD as well as my original install of Beezy Pre-release and with the final release.  It only quit after Beezy updated it self a few times.  So can't figger what's up since the updates.  But I REFUSE to give up ... gonna work on it even though it gripes me to have to do so ... I really have spent a lot of time on it and that's not cool ...

I'll certainly post the info when I do get it up and running ...

---

### Post by TheFifth on 2005-10-25
Hey Timeless,

It would be great if you could post your results, I'd be very greatful.  Perhaps I'll give Breezy another try when others have had a little sucess with this problem.  I just have to use my laptop for work, so I can't afford to be without WiFi for an extended period.

Good luck!

Rich

---

### Post by Tor M on 2005-10-25
[QUOTE=TheFifth]

Tor Martin, it's good to hear that you've managed to get the hardware working (to a fashion) in Breezy, but it does seem like a lot of trouble to go through on every boot!  

One tip for the long boot times though is to lower your DHCP timeout.  This is normally the reason for long boot times when not connected to a network.  On my laptop I have edited the file '/etc/dhcp3/dhclient.conf' and uncommented the line '#timeout 60;' (removed the #) and changed the value to 10.  This lowers the pause on boot to ten seconds instead of a minute.  You may find that you can use a lower value than ten seconds, however it will depend on how quickly your DHCP server responds to requests.  NOTE: I did this in Hoary, but I assume it will also work in Breezy.  Try it at your own risk! :)

Cheers,

Rich[/QUOTE]

Hi Rich!

Thanks for the tip, I`ll try that.

Regards

Tor Martin

---

### Post by TheFifth on 2005-10-26
No problem! Hope it works for you in Breezy!

---

### Post by TimelessRogue on 2005-10-26
[QUOTE=TheFifth]Hey Timeless,

It would be great if you could post your results, I'd be very greatful.  Perhaps I'll give Breezy another try when others have had a little sucess with this problem.  I just have to use my laptop for work, so I can't afford to be without WiFi for an extended period.

Good luck!

Rich[/QUOTE]


Yes, I'll do exactly that ... unfortunately it won't be 'til later this evening before I can dedicate the time to hopefully finally solve this problem.  And if it can help anyone else, that's great.  Will post the process and any results immediately thereafter.  

Later, guys (and gals) ...


And later is now ... for the moment ...

So here I am ... back again online via wireless and the Breezy Final Release Live CD.  Now I need to do some checking to find out just what the difference is between this setup and my installed setup.  I'll post back here with what I find out what's what.  

Of course that will be later when later is actually later ...


And later is now as it turns out ...

Whether or not this is a key, it seems it just may be ... at least it was in my situation:  For wireless to be setup from the get-go, install Beezy while your are at a location that has wireless access and with your wireless card in place.  I reinstalled the Beezy final release at home with only DSL access and all went well except it failed to recognize and install my Linksys WPC11 or wireless access.  I fiddled and tweaked as I had done before with no luck.  I reinstalled this morning over a couple of lattes at the Coffeeworks where I had access to their wireless system and here I am ... with my Linksys WPC11 recognized and installed with no problems.  Perhaps it's related to downloading the right drivers from the repositories, who knows.  At this point, all is well ... I have not, however, updated Beezy or tried using DSL (which is my access at home).  When I do that, it will be in increments that will allow me to detect exactly which update caused the problem of uninstalling my wireless or at least making it unaccessible.

So ... I would suggest that those that are having problems with wireless access to give this method a try and let us know if it works for you too.

As things progress, I will update this thread with more info.   Good luck all!


Okay then ... here we are so far:  As of this evening all seems well with networking.  I am now at home and have plugged in and set up my DSL connection on eth0.  Wireless is on eth1 and seems to still be working okay (finding the Linksys card anyway) but obviously is not finding a system to log into.  NOW ... I am going to leave things as is 'til morning when I will sacrifice some more time over another double latte at the Coffeeworks making sure everthing is copacetic with the wireless connection.

This is a copy of my /etc/network/interfaces :

     # This file describes the network interfaces available on your system
     # and how to activate them. For more information, see interfaces(5).

     # The loopback network interface
     auto lo
     iface lo inet loopback

     # This is a list of hotpluggable network interfaces.
     # They will be activated automatically by the hotplug subsystem.
     mapping hotplug
        	script grep
	        map eth1

     # The primary network interface
     iface eth1 inet dhcp
	     # wireless-* options are implemented by the wireless-tools package
	     wireless-mode managed
	     wireless-essid any

In case anyone is wondering why I am using this method to work this wireless thing out, I'm trying to accomplish all of this using the simplest of procedures without getting into any "programming" so to speak.  The goal is to come up with something that even the newest of newbies can handle without getting into the more esoteric methods.

At this point, it would seems that the surest way to make sure you have wireless configured from the get-go is to install Breezy with the card inserted and at a site where you can access a plain vanilla (no WEP) wifi system.  I encourage some of you that have also been having problems to give it a shot and let us know if this system works for you.  Or not.

In any case, I'll post again in the morning ...


And now it's morning coming up on afternoon ...

I've just logged on using the wifi connection and all appears to be well with networking.  The following was added to my /etc/network/interfaces:

auto eth1

iface eth0 inet dhcp

auto eth0


The following is the output of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"kayak"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:42:B5:5C
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/92  Signal level=-54 dBm  Noise level=-141 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions


And this it the oupbut of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:D0:59:A1:A7:28
          inet6 addr: fe80::2d0:59ff:fea1:a728/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8c00

eth1      Link encap:Ethernet  HWaddr 00:06:25:A9:FD:4B
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:25ff:fea9:fd4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:980015 (957.0 KiB)  TX bytes:232977 (227.5 KiB)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6829 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:565671 (552.4 KiB)  TX bytes:565671 (552.4 KiB)


Sooo ... all appears to be well with my network setup at this point ... aside from not having my modem setup (which would sort of be nice to have in the case that I am not around either of the other two).  I still plan to continue monitoring any updates/upgrades in an attempt to verify whether or not this is what caused my wireless connection to be dropped.  I kinda doubt it now though ...

I guess that's it, guys and gals ... success!  Finally!  It's nice, to say the least, to have Beezy up and running and the ONLY problem I've encountered has been solved.  I do have to say that setting up this Linksys wireless connection really was no more complicated than it was when I set it up in Win2000 Pro way back when.

Good luck to the rest of you ... and if any of this helps that's great.  I would definitely suggest, as a result of all of this, that to avoid problems installing your wireless card/connection you try to do you installation  with your card inserted and in the presence of a wifi connection ... that seems to be what turned the trick for me, anyway.

---

### Post by knappen on 2005-10-26
[QUOTE=TimelessRogue]Hey Guys ... it's not just your cards.  I've got the same problem with a Linksys WPC11 v3 that worked from the get-go in Hoary but just will not ... no matter what so far ... work in Beezy.  I reverted to Hoary and all was well again.  It even worked with Beezy Live CD as well as my original install of Beezy Pre-release and with the final release.  It only quit after Beezy updated it self a few times.  So can't figger what's up since the updates.  But I REFUSE to give up ... gonna work on it even though it gripes me to have to do so ... I really have spent a lot of time on it and that's not cool ...

I'll certainly post the info when I do get it up and running ...[/QUOTE]

Agree with 100%

---

### Post by TheFifth on 2005-10-26
Cheers Timeless.

Good Luck! :)

---

### Post by herot on 2005-10-26
also some of yall need to try ```
dhclient
```
also you can specify your interface (if you know the dev ie. ath0, eth0, eth1, etc...)

---

### Post by TimelessRogue on 2005-10-27
As things have progressed on my way to solving this problem with my own setup, I've been editing my original post above rather that reposting the entire thing ... thought this might eliminate a bit of confusion bouncing back and forth ... or up and down, as the case may be ... so you might want to check up there.

---

### Post by Tor M on 2005-10-28
Hi!

I solved my wifi problem.

I found the solution in this threat:
[http://ubuntuforums.org/showthread.php?t=82237](http://ubuntuforums.org/showthread.php?t=82237)

I updated  the /etc/default/hotplug, changed the net agent policy NET_AGENT_POLICY=auto, in my case it was set to hotplug.

Then I changed the wifi section of my interfaces file to be much more detailed:

auto wlan0
allow-hoplug wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-channel 6
wireless-essid XXXXXXXX
wireless-key XXXXXXXX open

I added the lines about wireless-mode, wireless-channel, allow-hotplug wlan0 and specified if the wireless-key were open or restricted (open in my case, restricted won`t work for me.)

Now my machine boot faster than ever, and my wifi works at login without any script or puzzeling.

Hope this can help some.

Unfortunally now I have much bigger problems! My windows partition has crashed,  the bootsector or filetable has somehow been overwritten. It looks like it has been formated, and it hasn`t. Hundreds of family pictures, important mails, large projects................................gone! And ofcourse as the not so wise man I am, no backup!!
I have to find a way to run some kind of disk, file recovery.

But Ubuntu is working though! (Maybe even my wife can grow into liking linux now, when she has to use it for some time......)

Regards

Tor Martin

---

### Post by TimelessRogue on 2005-10-28
Okay then ... all is well and both my DSL (on eth0) and Linksys WPC11 v3 (on eth1) are up and running with no further problems.  I added the details in my original/edited post above.

---

### Post by athem on 2005-10-29
[B]I just found something and added this AFTER the post below.  I don't know whether this is an issue for others.  Using the Network Administration utitlity WEP settings don't seem to work properly.  In particular, you need to use the Hexidecimal string (not plain ASCII) option.  The ASCII option seems to write the write the wireless-key entry incorrectly in /etc/network/interfaces as:

wireless-key s:mysampleasciikeystring

Hex seems to work.[/B]

I'm also having problems with wireless  using Breezy.  I just bought the laptop (Acer Travelmate 8104 with ipw2200), so I never tried Hoary on it, and have been trying to get wireless working for a week with Breezy.

I downgraded to the ipw2200 drivers to 1.0.0  as recommended by many (including ieee80211 and ieee80211_crypt) for Breezy (it comes with 1.0.6).  Here is what I've found, maybe this can help shed some light on these problems:

I can get wireless connected when I turn off WEP encryption.  Related to this: the gnome graphical Network Administration and Network Monitor utilities don't seem to work properly.  I was having trouble switching to eth0 (my wireless card) as the default gateway, I don't think dhcp was working.  But when I turned off WEP on my router, bang - I got connected.  I think the Network Administration utility is supposed to manage the /etc/network/interfaces configuration file, but as said earlier, it doesn't seem to work properly.

If anyone has some tips, please let me know.  I'm going to look into the format for the interfaces file and try adding the key manually to that file.

UGH!

---

### Post by beckyh on 2005-10-29
I am no expert but the first time I installed Ubuntu last week I had wireless problems where it picked up the network fine but could not browse or anything.

Someone gave me some lines of code to put in the terminal and it worked.  I have a different setup now and cannot check the codes at the moment, but I do remember that the WEP key had to be done with a dash format in the interface file.  So if your key is 1234567890, in the interface file put in 1234-5678-90.
It may not work but its worth a try.

---

### Post by tshelton on 2005-10-30
Just upgraded to Breezy today -- wlan0 on Hoary became ath0 after the upgrade.  I've got a DLink DWL-G630.

FWIW, I was following this thread trying to get my laptop to connect -- I removed the WEP encryption on my access point, and it connected.

I re-instated the WEP encryption and it dropped the connection.

I edited /etc/network/interfaces and replaced my hex WEP key with the same key, but in upper-case (instead of lower-case).

sudo ifconfig ath0 down
sudo ifconfig ath0 up
sudo dhclient ath0

And now it's working.

Coincidence?  Who knows...but I thought I'd pass along my story...

Updated: nix that -- missed a setting -- WEP was still disabled when it was working.  Sorry....  :(

---

### Post by Dardie on 2005-10-30
Thanks to comments in this thread I've now fixed my problem (documented in [http://ubuntuforums.org/showthread.php?t=81883](http://ubuntuforums.org/showthread.php?t=81883)) - basically my wifi card would not  come up with an IP address or default route from DHCP during boot, and would leave these processes lying around:

$ ps -ef | grep lan
root 6889 1 0 18:10 ? 00:00:00 /bin/sh /etc/hotplug/net.ifup wlan0=hotplug
root 6979 6889 0 18:10 ? 00:00:00 ifup wlan0=hotplug
dhcp 6987 6979 0 18:10 ? 00:00:00 dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/run/dhclient.wlan0.leases wlan0

even though these scripts worked fine AFTER bootup if the runaway processes were killed.

The solution (from this thread, and refined with experimentation) was simply to add EITHER of the lines 'auto wlan0' OR 'allow-hotplug wlan0' into my /etc/network/interfaces.

Based on about 5 bootups each, my system boots successfully with DHCP 100% of the time with either of these, and maybe 5% - 20% of the time (ie. DHCP does not get IP address or default route) without.

Happy happy joy joy! (and thanks Tor)

---

### Post by jungle_traveller on 2006-01-30
I have the same problem with my ipn2220 wireless card.I have installed the drivers but with the ndiswrapper method.The card scan normaly but the problem is tha it cannot connect to the ap.The ap also has got a wep but the key is being taken from the server,and also a radius server peap,where i have to write user and pass.The problem is that i cant do the setting for wep(open-given from the server) and peap protocol.Can anyone help??

---

