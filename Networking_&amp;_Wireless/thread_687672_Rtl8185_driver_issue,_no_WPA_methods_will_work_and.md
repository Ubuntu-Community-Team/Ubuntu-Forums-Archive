---
title: "Rtl8185 driver issue, no WPA methods will work and system freezing"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by jermsie on 2008-02-04
System: Ubuntu 7.10, wireless PCI card chipset rtl 8185

Situation:
Installed ndiswrapper and the windows xp INF for the **realtek rtl8185**. I'm pretty sure the system is using the 8180 driver instead, and when I connect to the network unsecured, it only ever shows as being 30% strength, no change. On my windows install, it shows around 60-80% constantly. I tried blacklisting the 8180 driver but then wireless became no option at all in the nm-applet. I'd really appreciate some help in properly setting up the 8185 driver.

Another issue. 
I read that Gutsy came with wpa supplicant already installed, but I installed it anyway. I've tried a variety of methods on Ubuntu Forums (ie: [manual network config]("http://ubuntuforums.org/showthread.php?t=571188&highlight=manual+network+configuration")) to connect to my WPA secured network but it's still no wireless option when I left-click the network monitor and nor does it connect on a manual setup.

Sometimes when I adjust some network setting or without doing much at all, the entire desktop locks up. Either the mouse and everything or just the entire desktop but cant click anything at all. Hard reset is the only way out.

Is any of this fixable? Haha, it's definately one way of flexing the stress muscle.

Any help is much appreciated :)

---

### Post by irritated skin on 2008-02-04
There is a problem with the r8180 driver that comes w/ the kernel 2.6.22.

First you will need to edit /etc/modprobe.d/blacklist and add 'blacklist r8180' to the file.
If you want to use WPA you will have to use the 2.6.22 Linux driver available at the Realtek website.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)

If you don't mind using WEP for your network ndiswrapper w/ the windows drivers on the same page will work satisfactorily.

There is a good possibility that upgrading the kernel to 2.6.24 would fix this problem too but I haven't had the time to try.

I  hope this helps.

---

### Post by jermsie on 2008-02-04
Blacklisting renders wireless totally unusable.

Id really like to avoid an open wireless network...

Good old ubuntu, always full of problems.

---

