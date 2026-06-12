---
title: "RT61 card on Hardy, nearly got it working"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Cadmus on 2008-04-28
Morning all, I've recently re-installed my HTPC with Hardy, I've got the wireless working but I have to re-enter my WPA key every time I boot, here's the details of the system first
[LIST]
[*]Dell Optiplex GX240
[*]Edimax EW-7128G PCI Wireless card
[*]An SSID we'll call MYROUTER for sake of argument
[/LIST]

Now the card appears to possess an RT61 chipset, here's the order of things I did and some of the side effects
[LIST=1]
[*]Installed Hardy with the standard options. No questions asked about wireless, network config was for onbaord copper port
[*]Hardy started as usual looked at ifconfig, copper port showing as eth0 and wireless showing up as wlan0 without an IP address
[*]Clicked on new Network Manager (I'm migrating from Feisty) and saw list of SSID
[*]My SSID wasn't on there so I said 'connect to other network' and entered my SSID and WPA key (about 20 alpha characters)
[*]Wondered why the signal strength was 0, then went back and typed in the RIGHT key
[*]Couldn't find out where to set up a static IP so right clicked on the Network Manager applet and selected 'Manual Config'
[*]Entered SSID and WPA key into the old-style network manager
[*]Was able to ping router and other machines on network
[*]Restarted machine, no network connection on wlan0
[*]Realised that I've somehow 'devolved' my netowrk manager into the pre-Hardy version, only option avilabale is manual config
[*]Re-entering WPA key makes connection come back up
[/LIST]

Now having made your eyes glaze over it comes down to the questions
[LIST=1]
[*]Is there a way I can get it so it doesn't need me to re-enter the WPA key each time? Will I need to do the ndiswrapper thing?
[*]How do I get the network manager to go back to its regular self?
[/LIST]

---

### Post by chronographer on 2008-04-28
try serialmonkey drivers, or setting network up via text files! /etc/networking/interfaces

---

### Post by Cadmus on 2008-04-28
Cheers chron, I've done the text set-up thing before with a Broadcom-based card so I'm fairly comfortable with it. Is that the most elegant solution for a machine that's only ever being connected to the same AP?

What are the odds of the serialmonkey drivers sorting my problem? I'm not so experienced at compiling my own drivers but there seems to be plenty of documentation, if it's highly likely to fix it I'll do that.

---

### Post by Cadmus on 2008-04-28
Right, heading to the machine to take another look, still a bit annoyed at the way the NM applet seems to hav regressed to the 7.xx version :)

---

### Post by Cadmus on 2008-04-28
After a little look at the machine tonight it's not connecting at all, I know this is the call of someone who's broken it but I literally have changed none of my wirless settings since I last had it working. Now the monitor apllet is always showing 0% signal even after a retype of the SSID and WPA key, also I cannot ping my router.

---

### Post by ushills on 2008-04-30
I have exactly the same card and found that the RT61 works out of the box with Hardy but with one major issue, you have to use network manager with a roaming connection and connect to you AP by clicking the card signal strength icon on the taskbar.

Any attempt to set a static IP or any manual configuration and the connection fails or does not start on reboot.

Using DHCP and roaming I have good connection speed and I do not need to enter the WPA password each time.

Try this approach and reply if it works for you - delete all you manual configuration and start with a fresh roaming connection.

Meanwhile, I am looking into the serialmonkey driver fix again as I need to use a static IP.

With Hardy at least the card can work albeit severely restricted.

---

### Post by kaivalagi on 2008-04-30
> **ushills said:**
> Any attempt to set a static IP or any manual configuration and the connection fails or does not start on reboot.

I am using a static configuration with my HTPC's rt61, and it sort of  works. I set it up using the network manager and it created a suitable interface file with the setting in it. When I reboot it fails to initialise properly, but if I run the following it kicks back into life:

```
sudo /etc/init.d/networking restart
```

I figured I would try running this same command in rc.local, but this doesn't get the card working on reboot...I still have to run the above command once logged in

I haven't tried creating my own interface file settings yet, in Gutsy I had to due to the serial monkey drivers I was using, and I used the same restart trick then, which worked a treat...

Any ideas?

---

### Post by Cadmus on 2008-04-30
Thanks for the advice, just checked this thread after a break. I'll see how the DHCP works out, I need port forwarding for torrents and the like but I have a feeling I might be able to make it go off MAC address (I have a fairly good router) instead of IP. I'll let you know how it turns out.

---

### Post by Girindor on 2008-04-30
I have also had problems with the RaLink RT61 chip set (or, RaLink RT2561T - apparently same thing) ...I wanted to start a new thread, but for some reason I am not able to / don't have the right priviliges or something, so I'm adding it here.

I installed Ubuntu 8.04 Server edition on an old Desktop to help me learn CLI and networking, and my wireless PCI card, which worked perfectly under 7.10 Desktop edition, is just not working. During the install it couldn't see it.

It is the Ralink RT2561T chip set. When I do "lspci" it tells me, "Network controller: RaLink RT2651/RT61 802.11g PCI", so it can see it.

I tried the following:
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "NAMEOFMYNETWORK"

so far so good.... but then, when I did:
sudo iwpriv wlan0 set AuthMode=WPAPSK

...it threw up the following error:
wlan0: no private ioctls

...I don't know how to proceed and would appreciate any help with this.
Thank you!

P.S. (Just because it needs mentioning: I love Ubuntu, but am really disappointed with Hardy Heron. It seems really buggy. I tried installing it on my sister's laptop and the sound wouldn't work at all, I then managed to get it to work somehow with Alsa, but it is bad quality)

---

### Post by rrkrr on 2008-04-30
I have Xubuntu 8.04 with a PCMCIA rt61 chipset card.
It's installed on a old, slow  256MHz Thinkpad.  I can get the card to work consistently (though with slower data rates than I expect) with Network Manager as follows:

1.Using Network Manager, select the "wireless connection" and the "Properties" button to get the "wlan0 Properties" dialog box.

2.Disable roaming mode and enter the network access parameters; - in my case the WEP key and  "Configuration: Automatic configuration (DHCP)".

3.Click "OK" to close "wlan0 Properties"

4 Click the check box next to the "wireless connection" to turn it off -  it immediately turns itself back on.   This seems to reset the card and I see  "Lock" light on it.

5.Type in a name in the "location" box above and save it by clicking the icon showing an arrow pointing to a disk drive (at least I think that's what it is...)

6.At this point the wireless card is working, though data transfers seem to go in spurts.

7.After restarting the computer, the lock light on the card may or may not come on, but in either case to get it working again I have to open Network Manager and click the checkbox next to "Wireless Connection" to reset the card, and then select my saved location name and activate it by clicking the big green checkmark that shows up.

8.(Sometimes after selecting the location name, it takes 20 or 30 second for the green checkmark to show up.)

9.After clicking the green checkmark, a dialog box appears indicating that the network location is being changed.

10.The card then works well enough to use email and surf the web on this machine.  (I've given up on videos)

---

### Post by ushills on 2008-04-30
to increase the speed of the native rt61 driver you need to add the following to /etc/modprobe.d/blacklist.

blacklist ipv6

your speed should then increase, wish I could use a static ip though need it for printer sharing and web-server routing through router.

---

### Post by Girindor on 2008-04-30
thanks for your help, guys, I really appreciate it. However, my problem is slightly different:
When I used the Desktop edition of Gutsy it worked without any problems, using the Network Manager applet. But now I am trying to use the server edition, so there is no NM applet - just command line... ;-)

any tips anyone?

---

### Post by Cadmus on 2008-05-01
Girindor, you're probably better off reading the guide at the top of the forum about doing wireless by hand. It's a little intimidating (especially for WPA) but if you're running the server edition you should have known what you were getting into :lolflag:

In other news my machines working fine, other than needing a keyring unlocking at boot for the WPA key, but I'm sure I've seen a solutuion to this and it'll give me a chance to get a handle on all the keyring stuff in Hardy. Turns out my Router forwards by MAC so it doesn't matter that I'm on DHCP.

---

### Post by ushills on 2008-05-01
Have a look at my post here for setting up via the command line, you need to us the interfaces file

[http://ubuntuforums.org/showthread.php?t=777036](http://ubuntuforums.org/showthread.php?t=777036)

---

### Post by ModEvil on 2008-05-16
Hi Everyone,

I'm trying to get RT61 setup using my Linksys WMP54G v4.1 PCI on Hardy. I've installed linux-headers and build-essentials and have installed the driver. The issue I'm running into is setting up the /etc/network/interfaces config. 

First, most of the install docs I've read keep mentioning ra0 as the interface but I believe it's supposed to be wlan0. Can anybody confirm this? Is there somewhere I need to check that I may have skipped over?

The other settings I'm having issues with in the interfaces config is the actual syntax for a WEP-128 encryption scheme.

I think that if someone could answer my first question I'd be able to find a answer to the second, but if your feeling generous I'd gladly accept a syntax example in your reply.

Thanks for the help

---

### Post by kaivalagi on 2008-05-16
> **ModEvil said:**
> 
I'm trying to get RT61 setup using my Linksys WMP54G v4.1 PCI on Hardy. I've installed linux-headers and build-essentials and have installed the driver. The issue I'm running into is setting up the /etc/network/interfaces config. 

Any reason why you installed the drivers, as for me, Hardy works out the box for my RT61 based wifi...

> **ModEvil said:**
> 
First, most of the install docs I've read keep mentioning ra0 as the interface but I believe it's supposed to be wlan0. Can anybody confirm this? Is there somewhere I need to check that I may have skipped over?

From what I remember when working with Gutsy the drivers did setup the wifi as wlan0 and not ra0

> **ModEvil said:**
> 
The other settings I'm having issues with in the interfaces config is the actual syntax for a WEP-128 encryption scheme.

When I setup the RT61 drivers for Gutsy I created WPA priv settings in the interfaces file for my wifi network to work. Now I am using Hardy default RT61 support I just used the network manager to set it all up for me. The only work around I needed was to restart the network on login (/etc/init.d/networking restart...or something like that), to bring it "up" properly.

Hope that helps

---

### Post by ModEvil on 2008-05-16
> Any reason why you installed the drivers, as for me, Hardy works out the box for my RT61 based wifi...

I hosed my working network setup when it stopped working all of a sudden. It turned out to be a router issue. 

Do you know if wlan0 is configured somewhere by default. I figure that this is a setting which can be changed and it's possible that I may have changed it. If you (kaivalagi) or anyone else knows where to confirm the network interface please let me know. 

Thanks.

---

### Post by kaivalagi on 2008-05-16
> **ModEvil said:**
> I hosed my working network setup when it stopped working all of a sudden. It turned out to be a router issue. 

Do you know if wlan0 is configured somewhere by default. I figure that this is a setting which can be changed and it's possible that I may have changed it. If you (kaivalagi) or anyone else knows where to confirm the network interface please let me know. 

Thanks.

I am not entirely certain of what you mean. If you run ifconfig or iwconfig in a terminal window you should get a listing of the network devices and their aliases. Based on these aliases you can then setup your /etc/network/interfaces file to suit what you need.

Does that help?

---

### Post by ModEvil on 2008-05-16
kaivalagi 
> Does that help?

Yes, that's exactly what I was looking for. I needed a definative answer on what I should call the network interface (wlan0 or ra0).

Much Appreciated

---

### Post by ModEvil on 2008-05-17
Thanks for the help kaivalagi I got it all figured out now.

For anyone else having trouble setting up their interfaces file here is what I'm using:

auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wireless-mode Managed
wireless-key 26_digit_hex_key
wireless-essid Name_of_your_network
auto wlan0

This is for a WEP 256 bit encryption through it should also work for 128 bit encryption.

---

### Post by kaivalagi on 2008-05-17
> **ModEvil said:**
> Thanks for the help kaivalagi I got it all figured out now.
Glad I could help :)

Don't forget to mark the thread solved (thread tools at the top)

---

