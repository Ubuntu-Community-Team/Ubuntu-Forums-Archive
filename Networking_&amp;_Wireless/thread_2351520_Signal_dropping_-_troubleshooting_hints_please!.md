---
title: "Signal dropping - troubleshooting hints please!"
date: 2017-02-04
forum: Networking &amp; Wireless
---

### Post by heatopher2 on 2017-02-04
Hi, I'm getting a bit frustrated with my wifi. I've got a Realtek RTL8723B USB adapter (which I installed a few weeks ago, immediately after migrating to Linux, with the helpful help of chili555: [https://ubuntuforums.org/showthread.php?t=2349727](https://ubuntuforums.org/showthread.php?t=2349727)). The adapter is connecting to a router supplied by the ISP, and it's going on and off a *lot*. One of the really weird/annoying things is that sometimes after a disconnect, I click on the connection name under the wifi icon, and then when I look at the connection information I have a new connection to the same old network, and that connections are listed under "Edit connections" as "Router-name" and "Router-name (1)". Why would that be happening? Sorry, me not understand this stuff. I don't find the wifi menu very intuitive, to be honest. Why do you get the available connections listed twice, as in the screenshot below? I think that it's when I click on one of those two that the "Router-name (1)" thing happens, but I did that just now and nothing changed. Hmmmmm. A bit confused.

[ATTACH=CONFIG]273518[/ATTACH]

What I really want here is a series of trouble-shooting steps. I'm fully aware that this adapter is a cheap USB thing that I bought for less than £10, and which is not able to receive a 5G signal, and that I'm probably better off getting a better adapter that can receive 5G. That of course could be part of it, but it is brand new, so it shouldn't really be the main source of the problem, should it? 

I'm most inclined to blame the router, which is a few years old by now, I think, and am prepared to phone the ISP (Virgin, if there's anyone fro the UK on here). More likely, I'll be better off to go in person to their local shop, rather than talk to someone in India who will mainly be trained to try to get a bigger TV package, but I want to be sure of my facts before I do that :~)

By the way, I notice that the connection dropped just now, while I was writing this! Argh. Help much appreciated.

---

### Post by chili555 on 2017-02-04
Most of the troubleshooting tips are included in my previous post. I do notice, however, this:>  The adapter is connecting to a router supplied by the ISP, and it's going on and off a *lot*.As well as:> I'm most inclined to blame the router, which is a few years old by now,If you are able to change the settings in the router, I then reiterate my previous suggestions:> As for the router, you might check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. I also note that the name of the network is jones repeats and/or jones wireless 2G. I have worked on more than a few cases where spaces in the name made connectivity spotty. If you have the option, I suggest that you change the name to jones_repeats and jones_wireless_2G or similar.

It is time for another of my famous rants! If you are not able to change settings in the appliance provided by Virgin, then I'd be very angry and tempted to either change providers or get my own router. In my own case, I am unwilling to attach to a device provided by AT&T where they know the passwords, backdoors, etc. I am unwilling to use less than optimum (read:insecure) settings set as defaults by the provider. I suppose they use WPA-TKIP just in case my grandmother visits with her circa-1998 laptop and PCMCIA wireless! Get real, AT&T!

I turn off wireless in the AT&T device and then use my own router.

END RANT.

The last thing I note is this:> I'm fully aware that this adapter is a cheap USB thing that I bought for less than £10That's not so bad, except that it uses a poorly maintained, obscure driver!

Please check the settings in the router and then let's move forward.

---

### Post by heatopher2 on 2017-02-05
Hi, thanks for the usual swift reply. Everything is on hold, as the Virgin "super-hub" fried its circuits last night when I was restarting it for the hundredth time in two or three weeks. So I have to wait until Wednesday for a new one, and rationed until then to the monthly 1GB of rather unreliable tethering off my phone. So time to take a break from everything, maybe!

Before the super-hub conked out, I did try renaming it, and the other one (which is an old router that I'm planning, or at least hoping, to turn into a signal extender). Interestingly, I wasn't able to use underscores to rename the super-hub, which again probably tells you something about its limitations. Whatever, hyphens instead. That's fine. I also couldn't find any way to play with channel widths, but well... it doesn't really matter any more. I'll just have to wait until Wednesday to report back :D

---

### Post by chili555 on 2017-02-05
If you wish, please give me the exact make and model of Virgin's appliance when you get the replacement. Perhaps we can look through the manual on line and find a few tweaks.

For me, at least, changing the 20 mHz channel width brought a nice bump in speed. In a recent case I worked on, it was crucial: [http://askubuntu.com/questions/877164/cannot-connect-with-wifi-when-close-to-router/877257#877257](http://askubuntu.com/questions/877164/cannot-connect-with-wifi-when-close-to-router/877257#877257)> Changing the band to 20 ghz resolved the problem 

---

### Post by heatopher2 on 2017-02-05
Sure, will do. Hopefully it'll have some slightly more advanced settings, but you never know with these ISPs, eh. The sales guy told me that it will have a longer range than the now-deceased one. Well, I should hope so! If it's still not particularly reliable when it comes, I will go and buy a decent router (when I can afford one, at least, ha ha). Any recommendations for a reliable mid-range one?

Meanwhile, I've stabilised my tethered connection with a little ping from crontab, so as long as I don't try to watch the Superbowl over this connection tonight, I should be OK until Wednesday :~)

---

### Post by chili555 on 2017-02-05
> **heatopher2 said:**
> Sure, will do. Hopefully it'll have some slightly more advanced settings, but you never know with these ISPs, eh. The sales guy told me that it will have a longer range than the now-deceased one. Well, I should hope so! If it's still not particularly reliable when it comes, I will go and buy a decent router (when I can afford one, at least, ha ha). Any recommendations for a reliable mid-range one?

Meanwhile, I've stabilised my tethered connection with a little ping from crontab, so as long as I don't try to watch the Superbowl over this connection tonight, I should be OK until Wednesday :~)I always check router reviews here: [http://www.smallnetbuilder.com/tools/rankers/router/view](http://www.smallnetbuilder.com/tools/rankers/router/view)

In my own case, I use a TP-Link Archer C7 AC1750. It covers all of my two-story, approximate 3200 sq. ft. house quite well. Mrs. Chili is connected with ethernet and gets smooth, reliable gigabit speeds. Happy wife = happy life!

I am sure it isn't the only good choice.

---

### Post by heatopher2 on 2017-02-08
Hallo! The *so-called* super-hub has arrived and I have what seems to be a reasonably stable connection (well, let's give it a couple of weeks before I pass judgement). It does have the channel width option that you mentioned before (20, 40 or 20/40 - I've got it on 20, following what you said). Nonetheless, it is certainly not a sophisticated piece of equipment. I can't use more than two numbers in a password, for instance! And underscores seem to be beyond its narrow world-view. I will get a decent router eventually, and just turn it into a basic modem, but anyway, it's OK for now.

So now I'm moving onto the matter that was in hand when the old one died. Namely, trying to connect that old router to this one, to be a signal extender.

Firstly, should I start this as a new thread, or is it OK to carry on here? Well, I'll try writing here, and see if there's a reply...

So, I was following this set of instructions: 

[http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/](http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/)

I successfully flashed the old router with the dd-wrt software, and then when I moved onto the next step I found that as soon as I made the dd-wrt a client bridge, as stated in those instructions, the dd-wrt signal just disappeared from the ether. I thought that maybe it was rebooting, and would come back at some point, but it was just gone, and I had to do a hard reset to get it back. So, OK, those steps don't seem very useful....

Next, I found these instructions:

[http://www.wi-fiplanet.com/tutorials/article.php/3639271/DD-WRT-Tutorial-3-Building-a-Wireless-Bridge.htm](http://www.wi-fiplanet.com/tutorials/article.php/3639271/DD-WRT-Tutorial-3-Building-a-Wireless-Bridge.htm)

which told me that I need to set a static IP on my laptop, and then connect it to the future wireless bridge. And then they give instructions to do that in Windows and on the Mac, but not on Linux. Sooooooo, I've subsequently been trying to follow a load of instructions to set that up and currently have /etc/network/interfaces looking like this. I'm assuming that enp3s0 is the ethernet port, and that that's the one I need to change. I had been using wlp2s0, but then it occurred to me that that must be the wireless port, and that that wouldn't be much use:

 # interfaces(5) file used by ifup(8) and ifdown(8)
  auto lo
  iface lo inet loopback

  auto enp3s0
  iface enp3s0 inet static
  address 192.168.1.2
  netmask 255.255.255.0
  gateway 192.168.0.1
  dns-nameservers 8.8.4.4 8.8.8.8

So.... I save that and restart the network manager, and when I check for my IP with "hostname -I" I've got no IP at all. When I try to get onto the router's control panel with 192.168.1.1, connected to the router by a cable, as stated in the instructions, no connection....

So, I feel a bit lost right now! I can't proceed, so I think it's time to leave this here, and go to the gym!

---

### Post by chili555 on 2017-02-08
First, converting an old router to a repeater using dd-wrt is beyond the scope of this forum and, for that matter, my scope! I am confident that there is a dd-wrt forum somewhere.

Second, this:> I'm assuming that enp3s0 is the ethernet port, and that that's the one I need to change.Why not find out for sure:```
ifconfig
```Here is the corresponding result from my machine:```
enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether xx:f7:28:ae:83:xx  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf0600000-f0620000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 258895  bytes 16504332 (16.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 258895  bytes 16504332 (16.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.120  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 2602:306:b8c8:15fa:e22c:310:89e8:2205  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::e28a:5920:5ed5:d892  prefixlen 64  scopeid 0x20<link>
        ether xx:c5:d4:0e:64:xx  txqueuelen 1000  (Ethernet)
        RX packets 1239783  bytes 1613688408 (1.6 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 610045  bytes 98958159 (98.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```In my case, enp0s25 is my ethernet interface.

Third, this will never fly:> auto enp3s0
iface enp3s0 inet static
address 192.168.[COLOR="#FF0000"]1[/COLOR].2
netmask 255.255.255.0
gateway 192.168.[COLOR="#FF0000"]0[/COLOR].1
dns-nameservers 8.8.4.4 8.8.8.8Finally, I suggest that you remove the added settings from /etc/network/interfaces and simply let Network Manager do its job. Ordinarily, when I am trying to administer a router as you've described, I simply plug in the ethernet cable in one of the LAN ports and NM reports that I'm connected. Then I type in the router's IP address in Firefox or whatever browser I am using this week (!!), and go.

---

### Post by heatopher2 on 2017-02-08
Hey, I got it working, finally! Unfortunately it did require booting  over to Windows, because it was much simpler to fix the static IP over  there. Or at least there were clear explanations that worked!

And then it was just about following these instructions for setting up a repeater bridge:

[http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge)

Now there's a decent wifi signal outside in the back garden and in the darkest nooks and crannies of the cellar of this four-storey house, plus I understand a little bit more about networks (albeit still not very much). "Job's a good 'un," as certain folk say over here. 

As much as I'm a full-on night owl, it is officially time to stop now! Thanks as always for your help. All the best to you and Mrs Chili :D

---

