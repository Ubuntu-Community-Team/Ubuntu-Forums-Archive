---
title: "WiFi accesspoint compatibility list"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by W3ird_N3rd on 2007-01-13
[size=+1]A list for **that**? WHY?[/size]

In [my thread](http://ubuntuforums.org/showthread.php?t=325095) I experienced a strange problem, and you can't find much info about it on the internet.

Apparently Ubuntu or maybe even Linux completely hates certain accesspoints. And if some hardware is not compatible, there should be a list with what works and what doesn't.

[size=+1]Okay, how can I test mine to add it to the list?[/size]

Note: if you've been using you AP intensively for several months you don't really have to do the test, if it would be incompatible you should have noticed earlier. Though you should make sure you use WPA1/TKIP, Ubuntu and no ndiswrapper (because I don't know what effect ndiswrapper has on the problem).

Glad you're asking. This is the test I came up with:

[list][*]Put your PC/laptop somewhere close to the accesspoint, make sure the distance can't cause problems.
[*]Set up your wireless network in such a way that it works.
[*]Make sure you didn't tinker with any WPA timer settings on the AP.
[*]Enable WPA1/TKIP security. Why WPA1/TKIP: it is the most simple way or protecting you wireless network that isn't cracked yet, and many people use it.
[*]Use native Linux drivers. If there are no native Linux drivers available for your card, too bad, don't participate in this test please.
[*]Use Ubuntu. I haven't tested other distro's and don't know where exactly the source of the problem is.
[*]Install XMMS.[/list]

Reset the AP first and associate your PC/laptop with the AP. If this already fails try if you can connect to a different brand AP with the same settings. If you can either your AP is broken or you've found a whole new problem.

Now fire up XMMS and play a reliable shoutcast stream. This is allowed to be a stream on the (W)LAN and the bitrate doesn't matter, as long as the stream is reliable and plays well. If you don't know any try [http://di.fm/](http://di.fm/). If you are deaf, you can check if the stream plays correctly by looking at the bars. If they are happily jumping up and down it works.

Notice the playing time XMMS shows. It shows minutes:seconds. After 99 minutes of playing it changes to hours:minutes.

Leave XMMS alone for at least 6 hours. Note some streams timeout after 12 hours, so don't fall asleep while testing (or sleep short). If you want to you can listen to the stream, if you don't just put the volume down. Come back to your machine after 6 hours. The timer should show something like 6:04 (6 hours and 4 minutes) and every minute the 2nd number increases by one (not every second, which would mean the stream has been playing for 6 minutes). If this is all correct your AP seems to work just fine with Ubuntu!

If the stream isn't playing anymore, and the playing stopped or XMMS proceeded to the next item on the playlist, your AP possibly isn't compatible. You can check for sure by hooking up the computer to the wired network and do the test again.

If you've done the test and you want to report it here, try to mention as much of the following info as possible:

[list][*]Brand and type AP, productlink appreciated
[*]Did you just use it intensively for several months or did you do the test?
[*]How long did you run the test if you did?
[*]If there is a WPA rekey-timer setting in the AP setup, what's it's value?
[*]If you did the test: if the stream fails, XMMS often keeps showing the moment the stream failed. If the timer shows it, what value is it?[/list]

[size=+1]Why XMMS?[/size]

It's a simple to set up test that continuously tests the connection, and if the connection fails it usually shows when it did. Yes, something that pings your router or other local device constantly would also be a good test, but I don't know any program that can do that and show results from the last 6 hours.

[size=+2]**THE LIST**[/size]

[size=+1]Compatible APs[/size] :mrgreen:

[list][*][Sweex LW050](http://sweex.com/producten.php?sectie&item=80&artikel=727) *1
[*][Netgear WGR614v6](http://netgear.com/Products/RoutersandGateways/GWirelessRouters/WGR614.aspx) *1
[*][MSI RG54SE](http://www.msi.com.tw/program/products/communication/cmu/pro_cmu_detail.php?UID=621) *1
[*][SMC SMC7904WBRA](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=1&scid=&pid=1493) *12
[/list]

[size=+1]Incompatible APs[/size] :cry:

[list][*][Asus WL-330g](http://www.asus.com/products4.aspx?l1=12&l2=41&l3=0&model=59&modelmenu=1)
[*]Belkin AP, unfortunately forgot the it's type, I brought it back to the shop when it showed up incompatible[/list]

Notes:
1 = also has router/switch functions
2 = has advanced features (e.g. modem/printserver/NAS/USB)

I'll try to maintain this list with the help of your replies.

---

