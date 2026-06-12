---
title: "Wireless doesn't work in Feisty"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by b0ng0 on 2007-04-19
I just booted up the livecd of Ubuntu 7.04 final and the wireless network manager detects nearby wireless connections. However when I try to connect to my wireless network, although it says it is connected and shows signal strength, nothing to do with the internet works, e.g. browser doesn't load pages, GAIM wont sign in, etc. My wireless card uses the rt 2500 drivers i think.

I do not know a massive amount about ubuntu (in Kubuntu edgy my wireless just worked), so I may be missing out some configuration. However I want to make sure my wireless will work before i install Feisty.

Any help is appreciated. Thanks.

---

### Post by spd106 on 2007-04-19
Can you ping the router?

Also check that the /etc/resolv.conf has a nameserver.

---

### Post by forcesofhabit on 2007-04-19
I have a similar problem. It shows BOTH devices I have, shows the network, but with no signal strength. I am unable to connect with either device. I had the same problem with Beta.

---

### Post by RavanH on 2007-04-19
I have struggled to get my RT2500 based wifi to work on Feisty beta with **Network Manager **for a long time without any success. Same issues: detecting networks (no signal strenth) but no traffic after connecting.  Even without any encryption :(

Network Manager on Feisty just does not do the job for RT2x00 cards, as far as I can tell. There should be a new driver release pretty soon but I didn't want to wait for that, so tested with other wifi managers. 

**Wifi Radar**: Same as NM, it just could not deliver...

**Wicd Manager**: Oh, joy! What a relief... It works straight after installation without any hassle. I've read reports about it being not very stable but on my machine it has been running now for over a week without any problems. Reported systems running Wicd: [http://compwiz18.ig3.net/wicd/wiki/doku.php?id=testing](http://compwiz18.ig3.net/wicd/wiki/doku.php?id=testing)

Check it out on [http://compwiz18.ig3.net/wicd/wb/](http://compwiz18.ig3.net/wicd/wb/) and see if it is as stable as on my Packard Bell EasyNote R3450 with Ralink RT2500 wireless card. Read the How-to to install and to get the tray-icon working.

Fairly easy, even for a beginner like me ;) but you can get support on their forum [http://compwiz18.ig3.net/wicd/phpbb/](http://compwiz18.ig3.net/wicd/phpbb/)

-Allard

---

### Post by b0ng0 on 2007-04-19
I have tried pinging my router but I just get back "Network Unreachable"...

This is a bit of a backwards step considering it's a new version.

---

### Post by RavanH on 2007-04-19
Oh, I forgot to mention that removing Network Manager made manual connection with my wifi network possible. But then wired networking suddenly did not work anymore... Strange.

I really like to have the possiblility to roam and switch networks (wired and wireless) when I need to. And Wicd allows me to have it all :)

---

### Post by b0ng0 on 2007-04-19
Thanks, if I can't get  it working any other way ill try Wicd.

---

### Post by needtosearchforum on 2007-04-19
I got the same problem with my broadcom wireless. I just cant seem to get it to work with my WPA2 router. Ill give that Wicd a try. Not that i have any hopes of getting this to work..

*edit*
WOW! Wicd just works! :D

---

### Post by whayong on 2007-04-19
Can anyone confirm if this works with RT61 cards?

---

### Post by b0ng0 on 2007-04-19
Well Edgy does, so I presume this should. Although saying that, my wireless ain't working and it did in Edgy.

---

### Post by whayong on 2007-04-19
> **b0ng0 said:**
> Well Edgy does, so I presume this should. Although saying that, my wireless ain't working and it did in Edgy.


lol!  You have RT61 card?

What encryption were you using in Edgy? Feisty?

Did you configure the rt61sta.dat module that phq's how to instructs?

The reason for all these questions is because I did manage to get the rt61 card working in Edgy using WPA by configuring the said module.  What sucks is when I go to a hotpot, I need to undo the module since the hotspots I use don't use WPA.  So I was kinda hoping that wicd would cure this annoyance.

---

### Post by b0ng0 on 2007-04-19
No sorry, I have an RT2500 card. However my laptop has an rt61 and it works on edgy. Can't say for Feisty just now though :p

---

### Post by amiga_os on 2007-04-19
grrrrr...

I'm having exactly the same problem as the original poster (also have a ralink card with the rt2500).

What infuriates me is that I submitted bug reports with the rt2500 and network manager during edgy beta and feisty beta.  Searching on launchpad, loads of people report problems with ralink and network manager - there seems to be a plethora of repeated bug reports on these issues.  What's really crazy is some of these bugs get labelled fixed - but they're just not.

Since I had at least WEP access working with Edgy final, Feisty networking has gone backwards for me - as it doesn't support the card out of the box.  As much as I really love Ubuntu, I suspected this was going to be the case for the final release and it makes Feisty feel like a real let down.  I mean ralink networking *can* work (the code is there, the drivers are there)... it's just it doesn't work.  For all the ways in which Ubuntu shines, networking problems have put off a number of my friends now!

People have mentioned numerous fixes - which is the easiest one - and will it take an entire evening?

---

### Post by dschaller on 2007-04-19
Same problem here. Can't seem to get my rt2500 going with Feisty. The network manager just chokes. Maybe it's just me, but since Dapper the wireless in Ubuntu has been getting worse. I fire up Breezy and everything is just fine. Maybe I'll go back to that even if it's not supported anymore.

---

### Post by DiZASTiX on 2007-04-19
> **RavanH said:**
> I have struggled to get my RT2500 based wifi to work on Feisty beta with **Network Manager **for a long time without any success. Same issues: detecting networks (no signal strenth) but no traffic after connecting.  Even without any encryption :(

Network Manager on Feisty just does not do the job for RT2x00 cards, as far as I can tell. There should be a new driver release pretty soon but I didn't want to wait for that, so tested with other wifi managers. 

**Wifi Radar**: Same as NM, it just could not deliver...

**Wicd Manager**: Oh, joy! What a relief... It works straight after installation without any hassle. I've read reports about it being not very stable but on my machine it has been running now for over a week without any problems. Reported systems running Wicd: [http://adam.blackhole.cx/wicd/wiki/doku.php?id=testing](http://adam.blackhole.cx/wicd/wiki/doku.php?id=testing)

Check it out on [http://adam.blackhole.cx/wicd/wb/](http://adam.blackhole.cx/wicd/wb/) and see if it is as stable as on my Packard Bell EasyNote R3450 with Ralink RT2500 wireless card. Read the How-to to install and to get the tray-icon working.

Fairly easy, even for a beginner like me ;) but you can get support on their forum [http://adam.blackhole.cx/wicd/phpbb/](http://adam.blackhole.cx/wicd/phpbb/)

-Allard

> **needtosearchforum said:**
> I got the same problem with my broadcom wireless. I just cant seem to get it to work with my WPA2 router. Ill give that Wicd a try. Not that i have any hopes of getting this to work..

*edit*
WOW! Wicd just works! :D

I just spent all day downloading, installing and tryin to get my internet working in Fiesty. Thank you so much for this link, after hours of trying different drivers, messing with ndiswrapper and reinstalling ubuntu twice, Wicd just worked for me. I have a Broadcom BCM4318 wireless built in on my Dell Latitude 1300 and all I had to do with download the Wicd deb file, uninstall network-manager, install Wicd and reboot. Thanks so much for this link!

-diz

---

### Post by false_cognate on 2007-04-19
Since I've installed Feisty, my wireless has been broken. At first, it wouldn't even show nearby networks, but now it shows networks but will not connect.

I've got a Broadcom 4306 according to hardware info.
I've downloaded the .deb of Broadcom drivers from the relevant topic and installed (that is when it started detecting networks).
I removed ndiswrapper (I was using it under Edgy and it worked, however something changed in Feisty and I couldn't get it to work so I removed it in case it conflicted).
I also removed network-manager (didn't seem to help).

I installed Wicd (which shows the networks, but hangs upon connecting and won't connect, except for a wired connection).

---

### Post by Viper Daimao on 2007-04-19
im having similar problems. I did a clean install on my dell inspiron 6000 with an Intel PRO/Wireless 2200BG Network card. I could connect to my WPA2 wireless router seemingly fine, and could even access the router and transfer files between computers on the network, but cannot access anything outside the network. no gaim no internet. This is all out of the box as I haven't made any changes or downloaded anything for the wireless yet. 

I can use a wired connection for now (which works fine) but I guess I'll try this Wicd thing if it's not working in the near future. Can wicd connect to wpa routers with no problems?

---

### Post by keith11 on 2007-04-20
Well guys, this is a club no one would like to join intentionally, but oh well, I am joining your club of problems with wireless in Feisty.:) I have an intel pro 2200 wireless card and I am connecting to wireless through WEP 64-bit encrytption. My wireless worked in Edgy (Ubuntu as well as Kubuntu), but seems there is some problem in Feisty (I am using Kubuntu). I can connect to the wireless connection but as mentioned in the first post, none of my browsers can download a webpage and even update can't seem to connect. The browsers could download a webpage only once or twice. When I ping a website I can see ping times of around 80 ms, which is not that bad, but still I can't download any page. I tries using the DNS nameservers from opendns.org, but that doesn't seem to work either. I am going to try Wicd and then see what happens. I was very excited about Feisty, but this wireless thing kinda washed off some of that excitement. I am hopeful though that this would be a problem they will fix soon. 

Keith.

---

### Post by Episcopus on 2007-04-20
I too have an RT2500 card that isn't working.  I booted from the liveCD to check everything out before I installed Feisty on my laptop and the wireless isn't working.  Network manager detects my network and connects to it, but it won't communicate with the router, so I can't get an IP assigned to my computer.  I can plug into the router with a cable and get an IP assigned for my wired connection, though.

---

### Post by durerca on 2007-04-20
The same thing is happening with me on my Netgear WG511 PCMCIA adapter with a prism chipset. Ubuntu detects my card, can see wireless networks, and tries connecting but doesn't go any further. I've tried assigning a static IP but that doesn't help either. The wired connection works fine. I'd love to have Ubuntu installed on my laptop but so far I can't.

---

### Post by keith11 on 2007-04-20
I am not sure if this would help but I was going through many threads regarding an issue with my wireless in Feisty and I came across the following through a solved bug at launchpad:

1. You may want to change the channel number which is automatically looked for when you connect through a network manager. You can find out the channel number of your wireless connection by typing "sudo iwlist scan". After you know the channel number and if it is not 6 (6 is the channel number the network manager will usually look for), then try changing the channel number by typing "sudo iwconfig eth1 freq channel number". Replace the term "channel number" by your channel number without any quotes. This might tell your network manager to find that particular channel instead of the default channel number.


Hope this helps. Good Luck!

Keith.

---

### Post by wilderness wanderer on 2007-04-20
rt2500 pci card worked fine under Edgy. Upgraded via alt CD and no network. Numerous attempts at getting network manager to sort it out failed. I uninstalled network manager and it still will not connect via the Gnome network GUI. Note that this is with WEP encryption.

I _am_ able to connect via the command line:

sudo ifconfig ra0 down
sudo iwconfig ra0 essid blahblahblah key hexblahblah
sudo dhclient ra0

I found this at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/37120](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/37120)

Syntax to manually configure in /etc/network/interfaces

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyRouterName"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="MySecretPassword
        pre-up ifconfig ra0 up
auto ra0

Since I am only using WEP, modified to:

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyRouterName"
        pre-up iwconfig ra0 key "MyKeyInHex"
        pre-up iwconfig ra0 mode Managed
        pre-up ifconfig ra0 up
auto ra0

Now I have wireless connectivity which survives a reboot.

---

### Post by Episcopus on 2007-04-20
I use my laptop in many places on many access points, would I have to go through and manually set up the connection for each router I connect to?  It would be way easier if it just worked when I went to work or school.  I could probably make the sacrifice and do it all manually if I absolutely have to, but I am going to hold out hope that there is a way for it to just work.

---

### Post by b0ng0 on 2007-04-20
Sorry for the delayed reply, I managed to get wireless working after installation. Seems to be a bug/problem with the Livecd's that wireless doesn't work properly.

Roaming still doesn't work though... grr :mad:

---

### Post by wilderness wanderer on 2007-04-20
> **Episcopus said:**
> I use my laptop in many places on many access points, would I have to go through and manually set up the connection for each router I connect to?  It would be way easier if it just worked when I went to work or school.  I could probably make the sacrifice and do it all manually if I absolutely have to, but I am going to hold out hope that there is a way for it to just work.

Indeed.  In my case, network manager works fine with the wireless in my laptop.  On my desktop with a wireless PCI card I don't care about connecting to different networks, so using the config file instead works fine.  Hopefully the issue with Network Manager and/or the rt2500 driver will be fixed soon so they play nice together.  Of course, you can look into alternate wireless connection management utilities.

---

### Post by backhand on 2007-04-20
I thought I'd join the club of people having wireless problems :) 

I have a Toshiba Portege laptop with a Netgear WG511 v2 card, using ndiswrapper.

I was never able to get it to work on Edgy and I'm having the same problem with Feisty. 

The funny thing is that with my card plugged in I can sometimes manually configure the interface, but around 90% of the time my laptop just completely hangs. I can't even open a terminal window; I can try to open it in the desktop menu, the tab that says "terminal starting" opens and then quickly disappears. Trying to look at the system log does the same thing. I can't even press ctrl-alt-f1 to open another ttty and try to see what's going on with that.

I uninstalled Network Manager in Edgy, but that meant that I had to manually change networks every time I moved between work and home . Of course, that was a complete pain in the backside and I was looking forward to using the updated version of Network Manager in Feisty.

Anyone have any ideas?

Thanks for you help!

---

### Post by gesquive on 2007-04-20
Add me to the party, I have a Linksys WMP54G PCI card. I can't get internet access even if I disable encryption on the router. Oddly enough though, I can connect to the network, but when I do, i can't seem to get an IP address.
I thought this would be fixed by the time we got the final version, kinda frustrating.

It seems to be using the rt2500 drivers as well, and unfortunately i can't seem to get to the WICD web page.

---

### Post by wordgf on 2007-04-20
> **b0ng0 said:**
> I just booted up the livecd of Ubuntu 7.04 final and the wireless network manager detects nearby wireless connections. However when I try to connect to my wireless network, although it says it is connected and shows signal strength, nothing to do with the internet works, e.g. browser doesn't load pages, GAIM wont sign in, etc. My wireless card uses the rt 2500 drivers i think.

I do not know a massive amount about ubuntu (in Kubuntu edgy my wireless just worked), so I may be missing out some configuration. However I want to make sure my wireless will work before i install Feisty.

Any help is appreciated. Thanks.


I have the same problem and I have configured manually:

~$ lshw 
~$ lspci
sudo ifconfig eth0 down
sudo ifconfig wlan0 up

in my computer

---

### Post by kidcharles on 2007-04-20
I too have an rt2500 card and am having similar issues as others in this post. I can see my network under Network Manager (with zero signal strength), but if I try to connect it attempts to for about a minute and fails. This problem existed in beta too. The reason I got the rt2500 card is that the chipset designer has released the source code for their drivers under the GPL. The card works perfectly under both Dapper and Edgy. I have not tried this after install, only in a LiveCD session.

---

### Post by tl3000 on 2007-04-20
Looks like I'm not alone... my situation described in the following thread:

[http://ubuntuforums.org/showthread.php?t=415458](http://ubuntuforums.org/showthread.php?t=415458)

---

### Post by elmerfud on 2007-04-20
Wireless didn't work for me either.  However, if I do a /etc/init.d/networking stop and then start, it does.

You can see the console output here:
[http://ubuntuforums.org/showthread.php?t=415692](http://ubuntuforums.org/showthread.php?t=415692)

Please leave a message in that post if your situation is the same and I will enter it as a bug.

---

### Post by AdotB on 2007-04-20
I was having the same problem: Network Manager could see wireless networks but never connect to them. The ethernet on my laptop doesn't work, so you see how this was a big problem. I downloaded the earlier version using my Windows partition from the repos:

network-manager:
http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb

and the applet:
http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb

I uninstalled the network-manager packages and installed the older versions and now i happily browse the internet. The update manager always shows the updates of course, but if you don't mind that, this might be a good solution until this bug is fixed.

---

### Post by whayong on 2007-04-21
All the links to wicd site seem to not work.  Is the server down?

---

### Post by SiN486 on 2007-04-21
I have two cards: Intel PRO/Wireless 2200BG and a 3com 3CRWE154G72, the intel is onboard and pretty standard on centrino laptops. The 3com is a PCMCIA card. 

The intel works flawlessly out of the box, and WPA/WPA2 is even available. While the 3com only has WEP as an option and does not connect to my access point, it just tries (shows the swirly icon with the two grey spheres), though I did somehow get it to connect once, though I can't replicate it.

Also, with feisty the 3com shows as 'wlan0' and 'wmaster0' while in edgy (this card worked flawlessly with edgy) the card shows up as 'eth1'.

---

### Post by Pomo on 2007-04-21
> **whayong said:**
> All the links to wicd site seem to not work.  Is the server down?

Here is a latest wicd version if you need one. The site indeed seems to be down at the moment.

---

### Post by plafuro on 2007-04-21
Thanks a lot for the package!

Unfortunately any of the solutions is working for me (downgrading network-manager, using wifi-radar or wicd) :-(. I guess i'll just wait a little.

---

### Post by Loursalacampagne on 2007-04-21
Has the same problem : network-manager didn't work with chispset rt2500.

Now it work fine with wicd ! Thanks a lot for the tip ! :)

---

### Post by richie60 on 2007-04-21
I've been having the same problem too both with the new ubuntu & kubuntu live cd's.

My wireless network is seen, but when I try to connect - nothing happens.  Do I need to install it to make a difference as i've been only trying it running from cd.

---

### Post by whayong on 2007-04-21
Thanks for the link.  Now to get wireless up and working.  Anyone have any ideas? lol!  I have an RT61 card.  Currently using WPA.  WICD see's my AP, it just won't connect.  It gets as far as obtaining an IP address, then it doesn't connect.  Wired works fine however.

---

### Post by ziadoz on 2007-04-21
I can see wireless networks in network manager, I just can't connect to them. Any idea what's going on?

---

### Post by Episcopus on 2007-04-21
Today I tried /etc/init.d/networking stop, then start.  After it started, it DHCPDISCOVER attempted to obtain an address for eth0.  My wireless card appears as ra0.  Is there a way to make DHCPDISCOVER attempt to obtain an address on both devices?  If not, what can I change so that it tries to find an address for my wireless card instead of my ethernet jack?

---

### Post by a-musing amazon on 2007-04-21
I can't say anthing about your specific card, however can I pass on what helped me to get mine working on a new PC I've just built.

I have a Netgear WG311v2 with the TI chip. This has always proved a problem in the past for me, since although it is supposed to be able to use the acx111 kernel driver I could never get it to work. However in the past I did get it to work with ndiswrapper under Knoppix. 

The lines I needed to have in /etc/network/interfaces were

....
iface wlan0 inet dhcp
# Set wireless network parameters
wireless_mode managed
wireless_essid name_of_my_wap
wireless_key my_wep_hex_keycode
wireless_keymode restricted

(where name_of_my_wap and my_wep_keycode have been changed for obvious security reasons).

The point is that (after some experimentation) I needed the lines  

wireless_mode managed
and
wireless_keymode restricted

to get it to work.

However when I installed on Feisty on this new PC (I was just attempting to use the card) I found that the Admin/Networking tool simply created this: 

...
face wlan0 inet dhcp
# Set wireless network parameters
wireless-essid name_of_my_wap
wireless-key my_wep_hex_keycode

in my etc/network/interfaces file.

With this I could, like yourself, see all my local networks, but I could not connect.

Adding the missing lines using 

#sudo gedit etc/network/interfaces

to 

face wlan0 inet dhcp
# Set wireless network parameters
wireless-mode managed
wireless-essid name_of_my_wap
wireless-key my_wep_hex_keycode
wireless-keymode restricted

has now got it working.

It seems the Gnome Networking tool has suffered /again/ from oversimplification. If you have backed up your old script then check it and see if it has been changed. Otherwise check the network tools documentation for the full set of commands you can try but that the Feisty Admin/Networking tool doesn't handle for you. I suppse the good news is that the acx kernel module now sees to work which means I can use the card (I have several) on my other, X86_64, PC, where I have been stymied by the lack of a 64-bit windows driver for ndiswapper to interface with.

---

### Post by Episcopus on 2007-04-21
When I opened /etc/network/interfaces there wasn't an entry for ra0, which is my wireless card.  I did /etc/init.d/networking stop, then start and this was at the end of the message:

> SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


How can I associate my wireless card with wlan0, or how can I make my computer look at ra0 for wireless instead of wlan0?

---

### Post by a-musing amazon on 2007-04-21
Have you tried renaming all the references in /etc/network/interfaces from wlan0 to ra0?

If you google for wlan0 ra0 then you find some suggestions on other flavours of linux that this will work.

---

### Post by a-musing amazon on 2007-04-21
Just to update my previous report - when I repeated my edit of the /etc/network/interfaces file on my other PC, running the 64-bit (X86_64) flavour of Edgy, this also now works on wlan0 i.e. I can use wireless with my WG311v2 in 64-bit :) . Anyone need a less than year old wireless bridge?

---

### Post by AirRaven on 2007-04-21
Just wondering- would you reccomend upgrading to Feisty just yet?

I'm on a RT2500 as things stand on Edgy- does WiCD work well?

---

### Post by Episcopus on 2007-04-21
I added ra0 to my /etc/network/interfaces file and now dhcpdiscover is trying to obtain me an IP.  Part of the problem might be that dhcpdiscover requests IP addresses on 255.255.255.255 and my subnet mask is 255.255.255.0. Could that be a problem? If so, how do I fix it?

---

### Post by zarathustra on 2007-04-21
I've been having similar problems, something getting rid of network manager and installing wicd doesn't solve. It just won't save the essid (which my router doesn't broadcast). Upon booting, checking the connection with a simple iwconfig command shows the essid to be blank even though it's in the interfaces config file. It has to be manually set by taking the connection down. Would installing a newer version of the driver (I don't even know what version feisty is using, but I'm assuming you can get newer CVS snapshots) stop this problem?

---

### Post by Episcopus on 2007-04-22
I edited /etc/network/interfaces to read:

> 
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 mode Managed
pre-up ifconfig ra0 up
auto ra0


I also edited /etc/resolv.conf to add my primary and secondary DNS.

My wireless connection works now, and it survived a reboot, so I think that fixed it for me

---

### Post by b0ng0 on 2007-04-22
AirRaven:

It depends really. It seems to work for some and not for others. For instance, my wireless worked fine in Kubuntu Edgy and when I tried the Ubuntu Feisty LiveCD it didnt work. However when I installed it, it seems to work (but roaming doesn't sadly, I still have to manually configure it).

It's hard to say if you should upgrade, like I said things that don't work LiveCD might work after install so there's not a direct way to test. I would personally say just install then if it doesn't work try and fix it but then I abuse my computer far too much.... one day I think its going to leave me .

---

### Post by AirRaven on 2007-04-22
> **b0ng0 said:**
> AirRaven:

It depends really. It seems to work for some and not for others. For instance, my wireless worked fine in Kubuntu Edgy and when I tried the Ubuntu Feisty LiveCD it didnt work. However when I installed it, it seems to work (but roaming doesn't sadly, I still have to manually configure it).

It's hard to say if you should upgrade, like I said things that don't work LiveCD might work after install so there's not a direct way to test. I would personally say just install then if it doesn't work try and fix it but then I abuse my computer far too much.... one day I think its going to leave me .

*shrugs*

Ah well. It'll only be the sixteenth reinstall of Ubuntu I've done in the last year and a half. I'm sure all that reformatting isn't doing my Hard Disk any harm.

**EDIT**: Nope. No luck. The networking's just as broken on a fresh install as it is on the LiveCD.

---

### Post by dcapurro on 2007-04-22
I am unable to connect to the web. I have a DWL-G122 Ver C1 USB adapter. The manager detects the wireless networks available but i am unable to connect to them, even if they are unsecured. I tried the command "sudo iwlist scan" but i get the following answer:

lo                Interface doesn't support scanning
eth0           Interface doesn't support scanning
wmaster0   Interface doesn't support scanning: operation not supported
wlan0         no scan results

Do you know what can i do to solve the problem?

Thanks

> **keith11 said:**
> I am not sure if this would help but I was going through many threads regarding an issue with my wireless in Feisty and I came across the following through a solved bug at launchpad:

1. You may want to change the channel number which is automatically looked for when you connect through a network manager. You can find out the channel number of your wireless connection by typing "sudo iwlist scan". After you know the channel number and if it is not 6 (6 is the channel number the network manager will usually look for), then try changing the channel number by typing "sudo iwconfig eth1 freq channel number". Replace the term "channel number" by your channel number without any quotes. This might tell your network manager to find that particular channel instead of the default channel number.


Hope this helps. Good Luck!

Keith.

---

### Post by hiddensphinx on 2007-04-22
my netgear WG511U card worked fine in Fiesty Fawn Beta using WPA but now when I did an upgrade from Edgy to Fiesty my  WG511U card does not work with WPA

Fiesty Fawn looks at it as a WEP card but I my Netgear router is running WPA!!!!!!!!!!!!!!!

Wake up honey! You worked fine as a LIVE CD but now all you see is WEP :((((

---

### Post by ziadoz on 2007-04-22
I compiled a new kernel (2.6.20) and now my wireless works fine and dandy. I'm posting this from my laptop on the wireless.

---

### Post by hiddensphinx on 2007-04-22
> **ziadoz said:**
> I compiled a new kernel (2.6.20) and now my wireless works fine and dandy. I'm posting this from my laptop on the wireless.

Did you do a clean install

because I am PISSED OFF!!!

The LIVE CD knows a WPA signal when it sees it but the upgrade on my laptop going from Edgy to Feisty has no idea what the hell the "word" WPA means..it still detects a WEP signal when the real signal is a WPA :confused: :confused: :confused: :confused:

---

### Post by ziadoz on 2007-04-22
Yeah. This is a fresh install of Feisty Fawn. I just followed through this [guide]("http://www.howtoforge.com/kernel_compilation_ubuntu") with the 2.6.20 kernel from kernel.org.

---

### Post by zarathustra on 2007-04-22
> **ziadoz said:**
> Yeah. This is a fresh install of Feisty Fawn. I just followed through this [guide]("http://www.howtoforge.com/kernel_compilation_ubuntu") with the 2.6.20 kernel from kernel.org.

What card are you using?

---

### Post by bluebuddha on 2007-04-22
> **ziadoz said:**
> Yeah. This is a fresh install of Feisty Fawn. I just followed through this [guide]("http://www.howtoforge.com/kernel_compilation_ubuntu") with the 2.6.20 kernel from kernel.org.

Did you install straight-up 2.6.20, or the latest stable version 2.6.20-7?

Also, I noticed that Feisty uses 2.6.20-15, which I guess is considered "unstable" by kernel.org (?)  :???:

---

### Post by ziadoz on 2007-04-22
I used 2.6.20. To be honest I just grabbed any kernel to try it, I didn't have any data on the install anyway. I'll probably do it again now with a stable kernel now I know its the problem. My wireless card btw is a Broadcom 4311.

---

### Post by Domie on 2007-04-22
yep, this doesn't work either...

Rather a shame, since many new people will go back to Windows...

---

### Post by mas99 on 2007-04-22
And if it does work for you, dont get excited, it might not last.

I get WPA connectivity until I suspend or close the lid, after that zilch and I have to reboot.  

All worked fine on edgy.

---

### Post by zarathustra on 2007-04-22
I'm trying to compile the latest vanilla kernel right now. I think I will have to install seperate drivers for my card too (it uses rt2500), fortunately they are open source and easy to install (which makes the fact that it doesn't work properly in Feisty so odd). I've downloaded a CVS snapshot (since the last beta version doesn't support 2.6.20 kernels).

---

### Post by zarathustra on 2007-04-22
Didn't work for me; I have the same problem with the essid disappearing.

---

### Post by sabredog on 2007-04-22
I installed Feisty on a wirelessly linked PC the day after it was released. No joy.

Card is a Netgear WG311V2 conecting to a Netgear DG834G router. Wireless protection is WEP open.

the NM sees the card, gives signal strength etc. It can roam to connect or manual confif connect but cannot obtain a IP and thus no browsing/ see other computers on the LAN.

I will try editing the interface file as mentioned earlier in the thread and see how that goes before installing alternative software.

Do you need to uninstall NM if you install alternative software?

---

### Post by keith11 on 2007-04-22
> **sabredog said:**
>  Do you need to uninstall NM if you install alternative software?

I think it depends which one you are using as your alternative, for example, if you use wicd, which many people swear by, then you will have to get rid of nm.

Keith.

---

### Post by Domie on 2007-04-23
Will this be fixed or do we have to wait till 7.10?

---

### Post by plafuro on 2007-04-23
Hi,

maybe this seems like a silly problem, but got me without connection for a while... i checked in synaptic and several ndiswrapper-utils were installed at once (?), i.e.  ndindiswrapper-utils-1.8 and swrapper-utils-1.9 ...

After uninstalling those and reinstalling the latest package i got my wpa connections working again. Before that i could see all available networks but i couldn't use the wpa ones.

Don't know if this might help anyone but double checking won't hurt...

Cheers,

---

### Post by zarathustra on 2007-04-23
I should probably add that I am not using WEP or WPA, I'm not using DHCP either and my router doesn't broadcast its essid.

---

### Post by JerseyShoreComputer on 2007-04-23
Try turning off ROAM mode and go into manual config.... Also you can try WiFi Radar... I tried both of these and it works for me now even without using WiFiRadar...

Good luck!

---

### Post by Punisher187 on 2007-04-23
I had the same problem with my rt2500 card.  Installed kubuntu 7.04 x64 and saw wireless networks with no signal.  Tried to connect to my open unprotected wireless and couldn't connect.  I "sudo apt-get remove network-manager" and I was then automatically connected to my wireless :confused:.  Used adept manager to get the dependencies that the wicd file that was posted here needed.  After I installed that everything works like it should.  Thanks to everyone for all your input :)

---

### Post by tomhollis on 2007-04-24
I am having a similar problem with my bcm4318 wireless card, by removing and reactivating the driver module network manager was then able to run my card no problem:

sudo rmmod bcm43xx
sudo modprobe bcm43xx

This may help with your cards if you are lucky, bit of a botch but it will do me for now.

Tom

---

### Post by Handssolow on 2007-04-24
Yes I've got my RT2500 wireless working but every time I boot up I'm still having to input the following lines because my essid and key aren't retained, yet Network Manager and WiFi radar show them correctly. (Launchpad Bug #78037)
sudo ifconfig ra0 down
sudo iwconfig ra0 essid "XXXXX" key XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX
sudo ifconfig ra0 up
sudo dhclient ra0 

Surely there's a simple fix?

---

### Post by Handssolow on 2007-04-24
x

---

### Post by sammao on 2007-04-24
DWL-G122 Ver.3 C1
Or in general DWL-G122 not working i guess, in 7.04 or any linux? All I found was a link to a page on italian with lots of commands and stuff and the guy who didt it saying on english "when i got the time I´ll translate it" friendly guy.. I guess he never will translate.

---

### Post by Handssolow on 2007-04-24
Further questions -  Network Manager is install with Feisty and appears at the top in Feisty Ubuntu as "Manual Network Configuration, correct?
Opening up this box, I only see WEP as an option. Should I have WPA too?
Or Is there a problem with my RT2500 because my drivers need updating and/or there aren't any updated ones yet?

---

### Post by zarathustra on 2007-04-24
> **Handssolow said:**
> Further questions -  Network Manager is install with Feisty and appears at the top in Feisty Ubuntu as "Manual Network Configuration, correct?
Opening up this box, I only see WEP as an option. Should I have WPA too?
Or Is there a problem with my RT2500 because my drivers need updating and/or there aren't any updated ones yet?

I don't think it's anything to do with the drivers. I tried compiling my own kernel like someone else in the thread and I had to install the drivers, so I used the latest CVS available. I still have the same problem as you, it's something Ubuntu is doing that is causing this.

---

### Post by rkillcrazy on 2007-04-24
I just went from 6.10 to 7.04 and my wireless stopped working.  6.10 saw the wireless card fine and it worked great.  7.04 doesn't show a wireless option in network manager.  The laptop is set up for dual-booting XP Pro & Ubuntu.  XP can still use the wireless NIC.  I'm pretty sure it uses the **Intel Pro Wireless 2915ABG** on-board WNIC.

I've tried using **NDISGTK** but that was a bit flakey and I had to uninstall it and install it a second time for it to even half work right.  I say half 'cause it took the INF file but said that the device wasn't installed or enabled.  I've heard of this happening but the wireless still would work and show up in network manager.  I looked but still only saw WIRED & MODEM.

Someone told me that Intel provided a set of wireless drivers for the open source community.  Is this right and if so where can I find them?  Furthermore, I've never installed Linux drivers so how would I go about doing this?

I'm new to Linux but am employed as a Windows Network Admin so I'm pretty good with Windows command-line and some of the more advanced settings and tweaks.  I have played around with Linux a little.  So I guess I wouldn't consider myself an expert but I don't think I'd qualify as a novice either.  Nonetheless, I just can't get this to work so maybe I've met my match?

---

### Post by davince on 2007-04-24
I have the same problem with 7.04 and a RT2500 card. Strang enough it seems to be doing something with iwconfig, because as long as it is trying to connect iwconfig seems to be configured correctly. But then it gives up and the settings are cleared. 

I have a WEP encrypted network with a preshared key, but somehow when it tries to connect it says 'Waiting for key' (or something in that direction) .. no idea why it should do that because I selected 'shared' mode. It also doesn't show the signal strength. :(  I can get it to work by configuring it with iwconfig (adding key and essid) and then giving the DHCP client a kick... but I rather just have roaming access working. 

Oh, and the name is ra0... but it also tries to do somethnig with wlan, which I have no idea comes from. so I really hope they fix it soon.. I just want it it 'just work'...

---

### Post by zarathustra on 2007-04-24
> **rkillcrazy said:**
> I just went from 6.10 to 7.04 and my wireless stopped working.  6.10 saw the wireless card fine and it worked great.  7.04 doesn't show a wireless option in network manager.  The laptop is set up for dual-booting XP Pro & Ubuntu.  XP can still use the wireless NIC.  I'm pretty sure it uses the **Intel Pro Wireless 2915ABG** on-board WNIC.

I've tried using **NDISGTK** but that was a bit flakey and I had to uninstall it and install it a second time for it to even half work right.  I say half 'cause it took the INF file but said that the device wasn't installed or enabled.  I've heard of this happening but the wireless still would work and show up in network manager.  I looked but still only saw WIRED & MODEM.

Someone told me that Intel provided a set of wireless drivers for the open source community.  Is this right and if so where can I find them?  Furthermore, I've never installed Linux drivers so how would I go about doing this?

I'm new to Linux but am employed as a Windows Network Admin so I'm pretty good with Windows command-line and some of the more advanced settings and tweaks.  I have played around with Linux a little.  So I guess I wouldn't consider myself an expert but I don't think I'd qualify as a novice either.  Nonetheless, I just can't get this to work so maybe I've met my match?

Drivers are here: [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

I'm not convinced it's a driver issue though. I get this error whenever I bring the card down and set the essid:

> Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Function not implemented.

---

### Post by rkillcrazy on 2007-04-24
> **Domie said:**
> yep, this doesn't work either...

Rather a shame, since many new people will go back to Windows...

Or they could go back to 6.10 :) 

But, yes, it's a bother.  I did find the site for the Intel/Linux drivers.  I've not had a chance to work with it.  I'm hoping I'll be able to figure out how to install these drivers...

[http://ipw2200.sourceforge.net/]("http://ipw2200.sourceforge.net/")

---

### Post by almax00 on 2007-04-24
> **Handssolow said:**
> Yes I've got my RT2500 wireless working but every time I boot up I'm still having to input the following lines because my essid and key aren't retained, yet Network  

Surely there's a simple fix?
here's part of what i did to get a similar ralink card to work:

check in /etc/wireless for a directory called something like RT2500STA and open that directory. inside is there something like rt2500sta.dat ? use a text editor to open the .dat and you can input your SSID and your WPA passphrase and other variables.  

then add module to autostart:
#> echo 'rt2500' >> /etc/modules

create an alias: #> echo 'alias ra0 rt2500' >> /etc/modprobe.d/aliases

(your actual driver name may be different than rt2500......substitute as needed)

i have an RT61 pci card also made by ralink and used the following link to get it to work: [http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822).

it shows how to compile different drivers but since your card is working you won't have to do that. scroll down to after step 10 where he talks about getting the device up after reboot. skip the blacklist step also. 

good luck.

---

### Post by SwaroopKunduru on 2007-04-24
Hi All,

I have the saame problem Please look the attachment. I dont see wireless device. Also I am attaching "lspci: command.

Thanks in advance and regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2007-04-24
sudo ifconfig wlan0 up

When I do the above command it says no such device? How can I see wireless device?

Regards,

Swaroop Kunduru.

---

### Post by zarathustra on 2007-04-24
> **SwaroopKunduru said:**
> sudo ifconfig wlan0 up

When I do the above command it says no such device? How can I see wireless device?

Regards,

Swaroop Kunduru.

Try doing iwconfig or ifconfig -a to see if it's even listed. What card is it?

---

### Post by keith11 on 2007-04-24
> **SwaroopKunduru said:**
> sudo ifconfig wlan0 up

When I do the above command it says no such device? How can I see wireless device?

Regards,

Swaroop Kunduru.

Not sure if this will help but if you know what the module name for your wireless card is, type "lsmod" and check if it shows up. If not try adding your module by "modprobe wireless_module_name" withtout the quaotes of course where wireless_module_name is the name of your wireless card. Good luck!

Keith.

---

### Post by weijmano on 2007-04-24
I had also problems with my wireless I have made some changes in /etc/network/interfaces after I read this forum.

#Activate wirelesscard
iface eth1 inet dhcp
pre-up ifconfig eth1 up
pre-up ifconfig eth1 down
pre-up ifconfig eth1 up
pre-up ifconfig eth1 down
pre-up iwconfig eth1 essid "XXXXXX"
pre-up iwconfig eth1 key "XXXXXXXXXXXXXXXXXXXXXXXX"
pre-up iwconfig eth1 mode Managed
pre-up ifconfig eth1 up
auto eth1

---

### Post by Viper Daimao on 2007-04-25
I'm still having problems with wireless in Feisty.  I hope someone can help me. I did a clean Feisty install on my dell inspiron 6000, with an intel wireless card and using ipw2200 driver. I can connect to my WPA2 network fine, and can transfer files over the network and ping external IPs. However I cannot ping domain names. Nor can I access any outside webpages, or connect to instant messengers, nor connect to ip addresses. I tried changing my dns to opendns but this hasn't helped. I turned off the encryption of my network and still see the same behavior. So I tried installing wicd, but still saw the same exact behavior. 

I looked at my /etc/network/interfaces file and saw this

```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp

auto eth0
```

The weird thing is I don't have a eth2, ath0, or wlan0 interface. My wired network card is eth0 and my wireless card is eth1. So I added ```
auto eth1
iface eth1 inet dhcp

```
but nothing changed. I've tried manually stopping the network and restarting to see no change.

This all worked fine under Edgy so I'd be really grateful for any help or anything I can try to figure this out more.

---

### Post by amniarix on 2007-04-25
I eventually got my RaLink RT61-based card to work under Feisty, and [wrote up a tutorial]("http://ubuntuforums.org/showthread.php?t=419709").

---

### Post by keith11 on 2007-04-25
> **Viper Daimao said:**
> I'm still having problems with wireless in Feisty.  I hope someone can help me. I did a clean Feisty install on my dell inspiron 6000, with an intel wireless card and using ipw2200 driver. I can connect to my WPA2 network fine, and can transfer files over the network and ping external IPs. However I cannot ping domain names. Nor can I access any outside webpages, or connect to instant messengers, nor connect to ip addresses. I tried changing my dns to opendns but this hasn't helped. I turned off the encryption of my network and still see the same behavior. So I tried installing wicd, but still saw the same exact behavior. 

I looked at my /etc/network/interfaces file and saw this

```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp

auto eth0
```

The weird thing is I don't have a eth2, ath0, or wlan0 interface. My wired network card is eth0 and my wireless card is eth1. So I added ```
auto eth1
iface eth1 inet dhcp

```
but nothing changed. I've tried manually stopping the network and restarting to see no change.

This all worked fine under Edgy so I'd be really grateful for any help or anything I can try to figure this out more.

Wow, it seems as if someone has the same problems and he did all the same things I did for solving the problem. I must admit though that I do face problems like you but I am also able to download the pages sometimes. I have filed a bug report related to this error for ipw2200 in Feisty here:

[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108450](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108450)

I am yet to receive any answer but you can leave comments about your problems in my thread so the developers would know it is a problem which other people too.

---

### Post by Viper Daimao on 2007-04-25
> **keith11 said:**
> Wow, it seems as if someone has the same problems and he did all the same things I did for solving the problem. I must admit though that I do face problems like you but I am also able to download the pages sometimes. I have filed a bug report related to this error for ipw2200 in Feisty here:

[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108450](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108450)

I am yet to receive any answer but you can leave comments about your problems in my thread so the developers would know it is a problem which other people too.

Thanks Keith, it's definitely true, misery loves company :)

---

### Post by keith11 on 2007-04-25
> **Viper Daimao said:**
> Thanks Keith, it's definitely true, misery loves company :)

Well, sure it does. :) I would like to ask you to confirm the bug on the link I posted on my earlier post by leaving a comment there because as launchpad works, they reply sooner if the bug has been confirmed by more than one user. Good luck!

Keith.

---

### Post by lifishing on 2007-04-26
After I upgraded to Feisty, my wireless network with RT2500 chipset didn't work properly. It dropped connection every once a while. I figured out it's the network-manager's fault.

    Now my wireless works fine with following settings:
 
   1.  Uninstall network-manager
   2.  In /etc/Wireless/RT2500STA/RT2500STA.dat: 
[B]
   [Default]
   PSMode=CAM
   SSID=MY_SSID
   NetworkType=Infra
   Channel=10
   AuthMode=WPAPSK
   EncrypType=TKIP
   WPAPSK= MY_PASSWORD[/B] 
    
    I don't know if "Channel" matters. I get channel number by looking at my router's setting.

   3. In /etc/network/interfaces:

[B]   auto lo
   iface lo inet loopback
   address 127.0.0.1
   netmask 255.0.0.0
  
   iface eth0 inet dhcp
  
   iface ra0 inet dhcp
   auto ra0[/B]

---

### Post by erm67 on 2007-04-26
> **b0ng0 said:**
> I do not know a massive amount about ubuntu (in Kubuntu edgy my wireless just worked), so I may be missing out some configuration. However I want to make sure my wireless will work before i install Feisty.

Any help is appreciated. Thanks.

The driver works but  the configuration utility RaConfig2500 shipped with ubuntu don't because they patched it to use eth0 as the device name so gives always the error "driver not found", after you have installed the rt2500 package edit the /etc/rt2x00.conf and put a single line with ra0 in it, now you can use RaConfig2500 to configure you wireless card.
if you are actually using the old driver (creates the driver ra0) then prior to install Feisty  copy /etc/Wireless/RT2500STA/RT2500STA.dat (if you created it) from your old installation in a safe place and then after the installation to feisty and all old configuration will be retained.
I have opened a bug regarding the RaConfig2500 utility not working so hopefully someone will package the correct version.

Syntax to manually configure in /etc/network/interfaces

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyRouterName"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="MySecretPassword
        pre-up ifconfig ra0 up
auto ra0

---

### Post by zarathustra on 2007-04-27
> **amniarix said:**
> I eventually got my RaLink RT61-based card to work under Feisty, and [wrote up a tutorial]("http://ubuntuforums.org/showthread.php?t=419709").

Thanks, the little pre-up command for setting the essid has worked for me. Now when I boot up I automatically have a connection. I didn't need to bring it up and down a couple of times first, either.

---

### Post by petersen_t1 on 2007-05-02
Hello all,

I started my ubuntu journey with Dapper Drake, v6.06, which I loved (after a while!) At first, I had all the usual problems in a migration from one operating system to another, including my share of wireless issues. But I have to say ubuntu was hands down the easiest linux distro I've ever used (and I've been involved with linux in some forms or another since the early 90's). So I kept on  chugging away, cause I was happy with the way (most) everything was "just working" in ubuntu. Anyway, with that background let me provide insight to my issue and my solution to the problem.

Just a few days ago, I was running Dapper with wireless working just fine (I had found a nifty little aplet called Network Selector). I have a linksys card with the rt2500 driver, it worked out of the box on dapper. Then yesterday I upgraded to feisty fawn (via the 6.06 -> 6.10 -> 7.04 procedure), decided to keep things as close as possible to a standard "clean" installl, so I removed network selector and allowed the "default" network manager to run.

This is where my problems started. The Network Manager would see the wireless network, but would not connect. Sometimes it showed a signal strength of 0, and sometimes it showed a strong signal strength. Also, one other important thing I noticed was that the light on the wireless card was no longer lit.

So then I thought "how was it working before", "what was the change involved?" and viola: I changed from network selector to network manager, which was the only major change which seemed to break my wireless support. So, I removed network manager and re-installed network selector, and presto, I'm back online, the wireless card light is lit, and all is well.

I don't know why ubuntu's default choice for wireless management does not work for me in feisty, but I thought I'd share this insight with others as a simple trick rather then fooling around in the command line and editing files left and right and creating havoc with your system :) 

If anyone has any ideas how to get the network manager to work on my system, that would be appreciated, and I will certainly give it a shot (after all I would prefer to use fesity's "default" choice for wireless)

---

### Post by tl3000 on 2007-05-02
> **petersen_t1 said:**
> Hello all,

If anyone has any ideas how to get the network manager to work on my system, that would be appreciated, and I will certainly give it a shot (after all I would prefer to use fesity's "default" choice for wireless)

The Network Manager in Fiesty is broken and does not handle wireless keys properly.  See all the bug reports:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/?field.searchtext=wpa+wpa_supplicant+%22network+manager%22&orderby=-datecreated&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/network-manager/?field.searchtext=wpa+wpa_supplicant+%22network+manager%22&orderby=-datecreated&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by petersen_t1 on 2007-05-02
Thanks dude!

:guitar:

---

### Post by Viper Daimao on 2007-05-02
I had some problems earlier with wireless, Then even wired stopped working. A few days ago, it all started working perfectly. I don't think I actually did anything. I'm stumped. Happy, but stumped.

---

### Post by petersen_t1 on 2007-05-02
LOL, not unusual for linux to behave that way at times, but glad it's working for you now. Just out of curiosity, what kinda wireless card/chipset do you have?

---

### Post by Chonnawonga on 2007-05-02
I've been having similar problems on a wireless card with a Prism54 chipset.

---

### Post by petersen_t1 on 2007-05-02
> **Chonnawonga said:**
> I've been having similar problems on a wireless card with a Prism54 chipset.

Hello, just wondering if you tried my simple trick above. Try de-installing network manager then installing network selector. Let us know if it works for you or not. I may or may not have had success doing that because of my chipset, but who knows, maybe it will help a bunch more people out. And it's really easy to do. :)


By the way, your sig is hilarious!!  :lolflag:

---

### Post by Chonnawonga on 2007-05-02
Thanks for the suggestion, petersen. (And also for appreciating the joke: no one else seems to find that funny. Heads buried too deep in Linuxspeak, I guess.)

I tried network selector, but with no luck. In fact, I had even less success than with network-manager and Wicd, which could at least detect broadcasted networks. I suspect my problem is different in nature from yours. I appreciate the suggestion, though. At this point, I'm willing to try anything!

Unless there's some sort of significant progress, I'll probably downgrade to Edgy tomorrow. :(

---

### Post by Viper Daimao on 2007-05-02
> **petersen_t1 said:**
> LOL, not unusual for linux to behave that way at times, but glad it's working for you now. Just out of curiosity, what kinda wireless card/chipset do you have?

I have a dell inspiron 6000, with a standard intel wireless card and using ipw2200 driver. Not sure what the exact problem was, but there were some signs that there was a dns problem. Did a clean install, wired worked, and wireless connected to my WPA2 linksys router fine, but couldn't access the internet (wireless network access was fine).  Took it to my friends apt, and it connected to his WEP netgear router. Now I was able to ping ip's such as google's but not domain names such as [www.google.com](www.google.com)

So I try entering in the opendns servers on my router to override the one received from my isp. Restart laptop, restart router, No change. Then I removed the opendns servers and restarted both router and laptop, and suddenly my wired was giving me the same behavior. So I am busy for a few days, then enter the opendns servers back in, and still no apparent change. A few days pass, I open the laptop from standby and all of a sudden everything works perfectly. 

So all in all I'm glad, but fearful about my laptop's wireless fickleness.

(edit, I should note that I also uninstalled network manager, installed wicd to no change. Then installed an older version of network manager also to no change, so I upgraded that from synaptic to the current version and still no change. This would be before the wired connection stopped working,)

---

### Post by rkillcrazy on 2007-05-02
Looks like I'm still having issues.  I was hoping there'd be an update that would've fixed it but I suppose I should stop holding my breath...  

Can anyone give me a "walk-through" with this set of drivers?
[http://ipw2200.sourceforge.net/]("http://ipw2200.sourceforge.net/")

I'm still pretty new to Linux & nothing I've found on the web has helped.  I know I'm able to download **ipw2200-1.2.1.tgz** without issue but that's as far as I can get. :(

---

### Post by Chonnawonga on 2007-05-03
Just an update: my problem with the Netgear WG511 v1 (Prism54 chipset) has been solved using [this post]("http://ubuntuforums.org/showpost.php?p=2585938&postcount=19"). Good luck to all of you.

---

### Post by ladyatlas777 on 2007-05-04
I  am a newbie to linux. I've run Kubuntu "Edgy" for about 3 months and have loved it since my friend made me install it. (I complained so much about windows) Well my gist is I upgraded to feisty fawn kubuntu and I'm having the exact same problem as everyone else. I cannot connect through wireless. I have tried everything. It just doesn't work. So I'll be downgrading back to "Edgy" and waiting anxiously for this issue to be resolved. Its very disappointing. This is a major feature and having it not work makes me question whether this release was rushed or not. Its a shame. I was looking forward to the upgrade.

---

