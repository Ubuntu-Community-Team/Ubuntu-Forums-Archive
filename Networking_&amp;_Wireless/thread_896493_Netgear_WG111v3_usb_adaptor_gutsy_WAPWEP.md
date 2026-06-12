---
title: "Netgear WG111v3 usb adaptor gutsy WAP/WEP"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by MichaelSM on 2008-08-21
Hi all.

I've done what I can so far....

Using ndiswrapper, and having loaded the .inf Windows drivers:

Everything is almost fine. The usb module is recognised, in Network Config. gui my **** WIFI modem/router was detected. The wireless connection is ticked and enabled. It all looks perfect, except ...

Every 12 seconds or so, the led on the adaptor flashes five times, corresponding with a flickering of lights on the Netgear modem/router, but it won't settle on a connection.

In the wireless Properties there's a drop-menu of WAP/WEP selections, all of which seem to require a password. The only password I ever used was setting-up the modem/router, which was its default as in 'password' but that doesn't work. 

Probably I need to set a password for WAP/WEP. But HOW?

Any help greatly appreciated.

Thanks in anticipation,

Michael.

Maybe this will help ...

michael@michael-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
michael@michael-desktop:~$ dmesg | grep -e eth -e iwl
[   40.114873] eth0: VIA Rhine II at 0x1d000, 00:30:1b:35:0c:56, IRQ 11.
[   40.115604] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   52.793737] eth0: link down
[   69.000599] wlan0: ethernet device 00:1e:2a:42:37:de using NDIS driver: wg111v3, version: 0x1, NDIS version: 0x500, vendor: 'Realtek Wireless LAN', 0846:4260.F.conf
[  299.392136] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
michael@michael-desktop:~$ lspci -nn | grep -i intel
michael@michael-desktop:~$

---

### Post by pytheas22 on 2008-08-21
You should check the settings on your router to see what the WPA or WEP password is.  Generally you can access the configuration utility on most routers by opening a web browser on a computer that's connected to them (use an ethernet cable if you don't have any computers connected wirelessly) and typing "192.168.1.1" or "192.168.0.1" in the address bar.  On the configuration page, you can choose which wireless security options to use, and set the password.  I suspect that you're unable to connect because the WPA passphrase on the router isn't really "password."

It could also be a problem with the ndiswrapper driver, but please check your router's configuration first so that we're sure your WPA passphrase is correct.

---

### Post by MichaelSM on 2008-08-22
Thank you Pytheas22 for your quick response.

I've done a LOT of testing over the last night or so.

Here's the scenario:

I got a new MacBook recently, pre-programmed by a Government department.With AirPort WIFI.

So I bought a Netgear wireless modem/router so that I could use it at home with wireless which is VERY new to me. It took very little fiddling to get AirPort connected to the Netgear unit, which at that stage hadn't been set up with security. OK?

Later,since I'd mucked around with WEP/WPA, the Macbook told me it couldn't find a network, so I went via ethernet on my Linux PC to the router's location 192.168. etc and set up a WPA password in WPA Mixed Mode. Then I entered that password into the Mac's network WPA config, and it was back on line very quickly.

Cheered by that small accomplishment - as you can imagine - WHOOO! and knowing that the WPA password was established, I then went, on my Gutsy PC, to Admin>Network(admin password required for reconfig) found that the wireless connection was still enabled - done at boot - then entered my 'working' password for the modem/router under the drop-menu which has a few options ...WEP etc and WPA Personal or WPA Personal2.I've tried it in both ...

But the Network Config gui won't maintain the password, and I still can't connect the Gutsy PC to the modem/router. The LED on the usb adapter flashes but can't stabilise. Yes I have tried this with ethernet plugged, unplugged, reboot after reboot; USB adapter in/out ...one might imagine the scenario.

Could there be an issue with /secrets files?

At least I know I've done the right thing re. Macbook. Otherwise I'd be booking myself into a psychotherapy unit....

Any help greatly appreciated. I hope I've explained this properly.

Cheers to all,
Mike.

To make things worse or better; when I interrogate the Netgear modem/router's interface, my PC is registered as an attached device....!

---

### Post by pytheas22 on 2008-08-22
Don't worry about being confused about how wireless all works; it is a complicated thing.

My strongest suspicion is that your problem has to do with Network Manager, the connection manager that Ubuntu uses by default.  One thing that may help you is to enable Roaming Mode for your wireless card in the System>Administration>Network utility.  Then try to connect to your network by left-clicking on the Network Manager icon (it probably looks like to computer monitors now and should be in the top-right corner of your screen) and selecting your network's name from the list.

If that doesn't help, you can also try using [wicd]("http://wicd.sourceforge.net")--there are installation instructions on the site.  Installing wicd will require you to uninstall Network Manager.  But in many cases wicd works when NM doesn't.

Please give the above two things a try and let me know if it helps.  If not, please run this command the next time the wireless connection drops on Gutsy:
```

dmesg | grep ndis
```

and post the output here.

---

### Post by MichaelSM on 2008-08-23
BIG thanks pytheas22!! 

I did as you suggested with Roaming Mode and Network Manager; a few boxes popped up asking for passwords and other data and all is now hunky-dory.

BTW, after having followed every thread I could find (ALL of which dismissed Roaming Mode as incredibly slow and just about useless, which was why I was fiddling with Network Configure ..) NONE of them mentioned the Network Manager! 

I'd previously ignored NM beause my ISP connection was via a USB Alcatel Speedtouch 330 plus usbadslmodemmanager, which Network Manager wasn't interested in at all.

So far no hint of a dropout, and the wireless connection is between 65/78% according to NM. No detectable loss of speed with Internet.

There have been hundreds of 100% negative posts all over the shop about the Netgear WG111v3 usb adapter,which must look pretty silly now....

Mostly, I appreciated your well-written response. Too often, people get carried away with technical intricacies, and miss the point entirely.

Excuse the long-winded reply, but I hope that when others Google Netgear wireless stuff, they find this thread.

Cheers, and thanks again,

Michael.

PS With hindsight I'm amazed at my dumbness regarding the MacBook. It must have been pre-set to roam for networks, otherwise it wouldn't have detected the Netgear modem/router in the first place ....'THINK more, act LESS impatiently ..' My lesson learned ...!

---

### Post by pytheas22 on 2008-08-24
I'm glad you figured it out, and don't feel like you missed something that should have been obvious--if you've never used Ubuntu before, it takes some getting used to the way that it handles wireless.  Windows does things quite differently, and I don't know about OS X but it probably does as well.  For instance, I know of more than one person who was entirely unable to figure out how to connect wirelessly in Ubuntu because he never thought to *left*-click on the Network Manager icon in order to view the list of available wireless networks, presumably since Windows requires you to right-click.  So part of the wireless difficulties in Linux boil down simply to learning a new interface and abandoning the habits acquired from other operating systems.

The other major problem we have on Ubuntu is that Linux wireless-driver development was not centralized or standardized in the beginning (it mostly is now), so depending on your particular hardware, the steps required to get connected wirelessly varied, because different drivers worked in different ways.  The situation has improved a lot recently, and Network Manager is designed to make networking as seamless as possible, but because of inconsistencies in driver behavior and design, it's still problematic in some cases.

But I'm glad you're online now :)

---

