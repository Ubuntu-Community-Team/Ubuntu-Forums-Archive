---
title: "[SOLVED] Unable to connect via wifi on upgrade, atheros card"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by jasonruk on 2008-10-30
Hi there.

I've been using ubuntu a while now with some success but the wireless has been a bit temperamental so I thought I'd take the opportunity to upgrade today.

I'm using the drivers and restricted hardware that are default with the upgrade and it doesn't connect.  I used to use ndis and have tried that as well but the network manager applet always reads trying to connect until I'm asked to enter my password and the cycle continues without ever connecting.  It's the same with the default drivers and with ndiswrapper using net5211.inf.


The wlan0 is UP and here's some output from lshw

 *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:3a:a1:7e:91
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

and the same thing with ndiswrapper

 *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 01
                serial: 00:1f:3a:a1:7e:91
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,06/21/2007,5.3.0.56 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
 

If any more inforation is needed I'll be happy to supply it I just would like to see it working.

output from ifconfig

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx  
          inet6 addr: fe80::21f:3aff:fea1:7e91/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11978 (11.9 KB)  TX bytes:17582 (17.5 KB)

 output from iwconfig as I try to connect

wlan0     IEEE 802.11bg  ESSID:"TalkTalk"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=95/100  Signal level:-41 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also, when the pop up for password appears it's changed from what I originally enter

I did just notice this though, sorry I dont know how to put this lot in a scrolling window.

 *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:4b:e6:75:d5:f3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by jasonruk on 2008-10-31
Hello

I've tried a few more thing, checked firewall access and that sort of thing.  My debug tells me that no ipv6 routers present  

I seem to be having similar trouble to hosk on this thread  [http://ubuntuforums.org/showthread.php?t=964574](http://ubuntuforums.org/showthread.php?t=964574)

Jason

---

### Post by brodie101 on 2008-10-31
I have the same card and this is what I did.

Downloaded a patched madwifi driver. Search google for madwifi-hal-0.10.5.6-r3861-20080903

1 Remove restricted modules

**sudo apt-get remove linux-restricted-modules***

2 Rebooted 

3 install build essential

**sudo apt-get install build-essential**

compile the intrepid madwifi driver with

**sudo make install**

Reboot and enjoy wireless!

I hope this helps!

---

### Post by jasonruk on 2008-10-31
Thanks for the advice but that still doesn't work.  I don't think it's a driver problem, all the different ones I've used seem to do the same thing and with different degrees of success worked under hardy.

---

### Post by pmsumner on 2008-10-31
Out of interested - was your WiFi working in Hardy?

---

### Post by river2884 on 2008-10-31
networking in 8.10 is horrible, horrible.

---

### Post by jasonruk on 2008-11-01
Wifi was (just) working in Hardy.  With madwifi, it was very very slow, so slow I was wondering why there was no dial up noise.

I had some success with ndis and the windows xp net5211 driver.  It was much quicker, to what it should be really but the problem with that was it would only connect 1 out of about 7 or 8 times at best and nearing 20 at worst.

I also tried the suggestion from Mallet on this page along with the backports suggestion, still nothing.
[http://ubuntuforums.org/showthread.php?t=964836&highlight=atheros](http://ubuntuforums.org/showthread.php?t=964836&highlight=atheros)

---

### Post by jasonruk on 2008-11-02
Hi, me again

Still no joy.

I've done this, 'sudo dhclient' just as hosk on the post I mentioned above and we do seem to be having the same problem.  

I also removed Network Manager and replaces it with wicd and still no wireless, it just keeps doing the same thing.

I boot the computer.  The the 'two little dots' in the top right corner appear with the swirly thing going around.  The bottom dot goes green and stays that way until the poop up appears with the 'cancel' and 'connect' option with which type of security (wpa) and my password (which is different from what I originally enter)  I press cancel or connect, it doesnt matter which the same thing happens.  It tries to connect again and the process is repeated until the maximum number of tries is reached and it stops trying.

I have noticed a lot of other people seem to be having this sort of problem too, has anyone else found a solution yet?  I'll keep posting and hopefully will get it working to so will also add the results here.  Although I am running out of my skills in this.  Hopefully it will improve them and my knowledge of linux but I would really like to have my wifi back.

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another wau to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another wau to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by jasonruk on 2008-11-02
I'm getting somewhere now.

I remembered having a similar problem a while back when I was looking at VPN just to see what it was all about and how it worked.  I added the tool for vpn and found that the wireless didnt work then too.  The new network manager dialogue on ubuntu 8.10 has with a section for vpn, I don't know if vpn tools are installed on that (I still don't know that much) Thinking a bit about this, as I have done for the last couple of days I though about removing the network manager process, have previously removed the network manager itself but that didnt seem to make any difference.  This time,however, I just bypassed the process editing interfaces as.

$ sudo gedit /etc/network/interfaces

and adding the settings I need to connect from there.

auto lo
iface lo inet loopback


auto ath0
iface ath0 inet dhcp

wpa-driver wex
wpa-key-mgmt WPA-PSK
wpa-pairwise TKIP
wireless-mode Managed
wireless-essid *******
wireless-key *******

I'm not quite sure if i need the auto ath0 or if it does anything but my wifi is currently working.  

I'll mark the post solved soon, because I have only rebooted twice but each time the wireless has worked.  I wouldnt want to mark it solved only to find it's some random act of kindness on the part of my computer.

Jason
with acer laptop, atheros chipset, ndiswrapper

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another way to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by jasonruk on 2008-11-02
Well, that didn't fix the problem but I am closer to a solution.  

The other thing I did was remove the driver (net5211) and remove ndis via synaptic, reboot, add them back and it works.

I also checked the sys log because of noticing some text on shut down just before it stopped working again.

There was a warning about 'gchararray' being passed as null

and a list tty numbers being killed by TERM signal

Now, I don't know what that all means but I think tty is possibly a location for a port or somewhere to connect to the router/internet.  That being the case it does re-inforce my original thinking of not connecting because ports dont open (as with an over eager firewall)

---

### Post by jasonruk on 2008-11-02
update

ok, when the computer doesnt shut down properly it's also waiting to close something called ALSA.  

I've read that ALSA is Advanced Linux Sound Architecture and would explain why on start up after a shut down that hasnt gone well the sound if off or muted. 

I am still on wireless right now so I've at lease found a way around things but I realise it if very likely to stop working again.  I've changed the sound card from ALSA to a generic OSS mixer that can be found in 
System > Preferences > Sound
and the sound still works well so if I'm not using the ALSA there will be no need to wait a several minutes for the computer or hard close the thing and things might work the way I want them to.  This all, of course, does rely on the ALSA causing the problems in shutdown and not the other way around, but I'm sure I'll let you know one way or another.

---

### Post by jasonruk on 2008-11-02
It seem to be running, but for how long I don't know.  I know what to do now though when it stops.

I'm going to close this thread and mark it solved.  If there isn't an update soon though to prevent the problem from starting I'll start a new one that is more specific to the situation.

All that's left for me to do now is thank myself.

Jason

---

### Post by jasonruk on 2008-11-03
I also just came across [this post]("http://ubuntuforums.org/showthread.php?t=873980&page=7") and found the double entry of ndis useful.

I've also since removed the 

wireless-essid *******
wireless-key *******

from the /etc/network/interfaces file.

---

### Post by eks on 2008-11-03
Have you tried [installing the package with the built-in modules on Intrepid]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")?

---

### Post by brodie101 on 2008-11-05
Sorry for the deplay in replying people, if anyone wants the madwifi driver I got working on intrepid with the atheros card, I uploaded to a free hosting site, here is the link, [http://www.usaupload.net/d/g1kocurvvwi](http://www.usaupload.net/d/g1kocurvvwi)

---

