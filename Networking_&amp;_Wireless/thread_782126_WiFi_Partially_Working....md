---
title: "WiFi Partially Working..."
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by foo25 on 2008-05-04
Hey, I'm having an utterly confusing problem... My WiFi only connects if I'm in a certain area of my house, or so it seems :confused:

For example, if I go downstairs, no wireless networks can be found, but if I simply walk upstairs, Ubuntu will find and connect to my network, along with finding others in the area. Once connected, I can go anywhere in my house and remain connected, however if I reboot, and I'm downstairs, it cannot find any wireless networks as before.

Very odd it seems to me... I have a Intel® Wireless WiFi Link 4965AGN chip and I'm running Hardy.

Any help at all is greatly appreciated! :)

---

### Post by ModelM on 2008-05-04
I'd try changing the channel your wireless router is using. Try channels 1, 6, or 11 first. If you're using one of these, try one of the other two.

---

### Post by foo25 on 2008-05-04
I tried that, but it seemed to prevent me from connecting at all, I even tried Windows and I couldn't connect. I assume that isn't the problem, unless I'm doing something wrong lol

Thanks anyway

---

### Post by foo25 on 2008-05-05
Anyone any other ideas? =S

---

### Post by jpeach on 2008-05-15
This sounds like a typical problem relating to the signal strength of your wireless router and not a problem with the wireless card. When you are in the basement does the wireless connection seem slower?  What is the signal strength upstairs and downstairs?

WiFi signals do not have great penetration when you change floors.  Plus, if the router is directly above or below you, the signal is not strong.  Make sure the antennas are vertical.  Small angle changes can have a large effect on the reception.

Your router may allow you to boost the power (mW) that it outputs or some routers allow you to install larger antennas and that will increase your range.

You could also install an Access Point (AP) in  the basement.

---

### Post by foo25 on 2008-08-31
Thanks for the info, but it seems very strange that with both XP or Vista, the wireless works anywhere in my house, and for a radius outside it seems, ie. I can sit in the garden with the laptop online. However, as soon as I boot Ubuntu, I cannot connect unless I simply walk upstairs. As simple as this sounds, it's a bit of a pain...

This is one of the few things that has prevented me converting completely to Ubuntu, and although I neglected to reply to this thread recently, I've tried everything I can think of. My router is a Linksys WAG354G, and I cannot see any options to increase the signal power it outputs or anything similar. I believe it may be a problem with Ubuntu choosing not to detect or connect to my router because the signal isn't as strong as it'd like. For example, downstairs (where I cannot connect), I get 4 out of 5 bar signal but at around 58-60%, whereas upstairs it'd be around 90% +

As I've said this is a main reason I haven't fully converted yet, so any suggestions would be great, thanks!

---

### Post by foo25 on 2008-08-31
Ok, this keeps getting weirder... If I do a scan for wireless networks downstairs, I can't see a thing in Ubuntu. If I walk upstairs, it detects maybe 5 or 6 networks. If I then proceed to walk downstairs and try to connect it works.

So apparently, it'll only detect wireless networks if I go upstairs in my house...? Yet once detected, I can connect from downstairs?! I'm completely baffled...

I've spent a few hours and worked out a few other things that were bothering me with Ubuntu, everything is working perfectly. This is the only thing holding me back from swtiching completely, and I'm all out of ideas =S

---

### Post by foo25 on 2008-09-06
Sorry to triple post, but I've been sitting for days messing around, and I can't find a thing that works.

This is the only thing stopping me from ditching Windows!! Any suggestions would be greatly appriciated, thanks!

---

### Post by jpeach on 2008-09-06
foo25, if I understand you correctly you can get it to connect downstairs if NetworkManager first sees your SSID when you are upstairs.  However, if you boot up while in the basement then you cannot connect because it does not see your SSID.

When you are upstairs your computer sees the SSID.  NetworkManager caches these SSIDs for a while.  When you go downstairs your SSID is still cached and that is why you can connect.

If you boot your laptap while in the basement it does not see your SSID and you cannot connect.  NetworkManager does not need to see your SSID.  I turned the broadcast of my SSID off in my router.  It is an extra security measure.  To connect to my network is choose "Connect to Other Wireless Network" in NetworkManager then type in my SSID.  Give that a try when you are in the basement.

My thinking is that you have a strong enough signal to use your laptop in the basement but for some reason NetworkManager has a problem seeing the SSID.

---

### Post by foo25 on 2008-09-06
I'll definately give that a try jpeach, really appriciate it, I believe I may have tried it a while ago, but not any time recently, thanks.

---

### Post by Gnea on 2008-09-06
Perhaps the basement isn't the central portion of the house?  Remember, 802.11 expands out in a circle, so if it's got strong signal hitting a concrete ground, that signal isn't going to bounce off of anything, since it relies on line-of-sight.  Have you considered moving the WAP to a more central location in the house?  What about placing the WAP on the rafters of the ceiling in the basement?  Or pulling an ethernet cable up through the floor/wall?

---

### Post by jpeach on 2008-09-06
Gnea, you are absolutely right and that was my first thought.  However, foo25 says that when he boots into WinXP or Vista on the same hardware he has no problem connecting in the basement.  So, there has to be a usable signal there.  Further, if he is upstairs and NM gets the SSID he can then connect in the basement with Ubuntu.  To me, this indicates that the linux driver can handle he degraded signal that is in the basement.  But for some reason it is not seeing the SSID.

What is really puzzling me is that the router sends out special packets every few seconds that announce the SSID.  For some reason there is a problem with these getting detected in the basement.  I assume that they are broadcast with the same amount of power as the data packets.  Foo25's machine can see the data packets so why can they not see the SSID broadcast packets?

---

### Post by foo25 on 2008-09-07
You see this is what is baffling me! I tried the "Connect To Other Network" option, but it just shows connection at 0%, and I can't load anything using that connection. I've had to boot back into Vista just to reply because Ubuntu won't pick up a single SSID from any network down here, yet I've got an Excellent signal from my router.

Once I boot into Ubuntu, I cannot dectect a single SSID, but as soon as I am half-way upstairs Network Manager suddenly picks up about 6 SSIDs or more surrounding me, and instantly connects to my router. This is what is really confusing me. The connect seems to be using 802.11g, perhaps Ubuntu is trying to use 802.11b or 802.11n and not gaining the same strength?

Just a thought, any way I could check this or change which type of connection it uses? I'm guessing Network Manager doesn't include these options.

---

### Post by jpeach on 2008-09-07
foo25, that is really strange.  The fact that you are able to connect in the basement by forcing the it to connect to your SSID says that your laptop has enough of a signal for it to communicate.  Yes, the signal strength is 0%.

I am wondering if there is a problem with NetworkManager (I am grasping for straws here).  Go into the basement and do NOT connect to anything.  Bring up terminal window and issue this command.  You may have to replace "wlan0" with the name of your wireless device.  wlan0 is the standard but I have also seen it as eth1 a couple of times
$ iwlist wlan0 scan


This should list all the AP that it can see.

Now connect (from the basement) to your wireless router.  Then issue the following command.

$ iwconfig 

You can tell from the bit rate what protocol is being used.
802.11a Bit Rate=5 Mb/s
802.11b Bit Rate=11 Mb/s
802.11g Bit Rate=54 Mb/s
802.11n Bit Rate=Not sure... but probably different then the others

Your wireless router is probably running in "Mixed Mode" meaning that it allows connections from 802.11b/g/n.  Try setting it to 802.11b then try and connect.  Then set it to 802.11g and connect the repeat for 802.11n

You should also google your network card to see if there is any known problems with your driver.  You find the name of your card by using the following command.

$ lspci | grep -i "network controller"

To get the name of the driver take the model number and issue your command.  My card is a "Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection" so I used 4965 in the grep command, that needs to be changed for your card

$ lsmod | grep 4965

Linux can use native linux drivers but it can also use windows drivers using a program called ndiswrapper.  Google your driver to see if it is linux or windows.  If it is linux then try replacing it with the Windows driver.  I do not know how to do that but I do not think it is difficult.  This way we can rule out a driver issue.

---

