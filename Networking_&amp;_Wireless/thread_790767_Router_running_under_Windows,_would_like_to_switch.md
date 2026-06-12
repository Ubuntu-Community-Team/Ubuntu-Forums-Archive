---
title: "Router running under Windows, would like to switch it to Ubuntu."
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by fullmetalgerbil on 2008-05-11
I had both my desktop and my laptop running ubuntu (7.10 and 8.04 respectively). However I went and bought a Linksys WRT54G router to run wi-fi for the laptop and configured it on a spare machine I had loaded with Win Xp. It was a bit of a headache, and I wound up going to Linksys tech support (who had not even heard of Linux, which I had figured on, so luckily I was running Windows). But eventually I got everything set up and its running well and fine.
Well, almost. The thing is I dont want now to be shackled with a Windows desktop pc just because my router is attached to it. 
So, I'm wondering what it would take to hook up my already configured router to my Ubuntu box. Is it as simple as just plugging it in and Ubuntu auto detecting everything? That sounds too easy to be true, but I'm hoping its so.
Anybody have any input on this?

---

### Post by vorgusa on 2008-05-11
That should work fine... as long as you are getting an IP address automatically using DHCP.  make sure the cable modem or DSL is connected to the Internet/WAN port on the router and that all your other computers are wireless or connected to one of the other 4 ports on the router.  The router does not care if your computer is Linux or Windows as long as it is configured properly with an IP, default Gateway, and DNS server, which are all give automatically by the router's DHCP server.

---

### Post by major_rocks on 2008-05-11
i have the same router, and once the router is configured you are good to go. If you ever change ISPs then you may need that windows machine one more time, as i dont believe Linksys makes an installer for Linux. There may be routers out there that are more linux "friendly", i dont know of any....perhaps some of the other members will post if they do.

But you should be ok now that your router is all setup, i have had the same router for a couple years and switched OS's many times, whether it be some distro of linux, or even windows.

---

### Post by Tomatz on 2008-05-11
Router configuration is cross platform. I.e. you dont need the setup disc. Just open up a web browser on the computer that is lan(ed) to the router and type in the address bar 192.168.1.1 (usually the default for wrt). Then you will be able to enter the router configuration.

If that ip doesn't work just look in the manual for the "advanced config" ip address.

;)

---

### Post by fullmetalgerbil on 2008-05-11
Yeah, I already have the router configured and my modem set to bridge-I dont know about the DCHP settings or anything, but I'm hoping it'll just work. When I originally set up the router under Windows I had to tweak some settings inside Windows and I was thinking I'd have to do the same with Ubuntu.
Well, I'll give it a try. Thanks for the responses.

---

### Post by chili555 on 2008-05-11
It works beautifully. Once you have your Ubuntu machine hooked up and you have an IP address, you should be able to do [http://192.168.1.1](http://192.168.1.1) and configure it to your hearts content from it's web browser interface. I know, I do.

Did you know that the operating system running on the WRT54G is Linux?

---

### Post by fullmetalgerbil on 2008-05-11
But here's the thing: my hearts delight is [I]not[I]having to configure it. I just want to plug it in and have it work. The configuration novelty with Linux in general wore off for me some time ago-why do you think I run Ubuntu and not Debian?lol. Anyways, I'm getting set to hook everything up and give it a spin right now. I'll let ya's know how it all turns out.

---

### Post by Tomatz on 2008-05-12
> **fullmetalgerbil said:**
> But here's the thing: my hearts delight is [I]not[I]having to configure it. I just want to plug it in and have it work. The configuration novelty with Linux in general wore off for me some time ago-why do you think I run Ubuntu and not Debian?lol. Anyways, I'm getting set to hook everything up and give it a spin right now. I'll let ya's know how it all turns out.



Most routers have a wizard much like the setup disc's wizard, in the configuration. Just have a look for it.

It is the ONLY way to setup your router under linux. There are no drivers or applications to do this because you dont need them.
 
As said it should be 192.168.1.1

---

### Post by dmizer on 2008-05-12
> **fullmetalgerbil said:**
> But here's the thing: my hearts delight is [I]not[I]having to configure it. I just want to plug it in and have it work. The configuration novelty with Linux in general wore off for me some time ago-why do you think I run Ubuntu and not Debian?lol. Anyways, I'm getting set to hook everything up and give it a spin right now. I'll let ya's know how it all turns out.

router configuration is a one time thing.  once it's configured, you don't need to reconfigure it for every computer.  that's one purpose of most consumer level routers ... plug it in, configure it, and any computer on your network will get treated the same way without further configuration.

can there be any harm at all in simply plugging it in and trying it?  that should answer most of your questions.

---

### Post by steve allen on 2008-05-12
Watch out for using usb wireless adapters ubuntu does not seem to like them, well it doesn't like my netgear wg111 but then perhaps I'm just lucky!

---

### Post by fatcoin on 2008-05-12
I have same problem with my Netopia (Motorola) router. Administration pages are available on Windows, but no on Ubuntu. I think Ubuntu give me option "Connect to wired private 811.x connection" or something like that (i can't remember) in tray network icon but I don't know what username and pass to use since router is allways connected.
Static IP, subnet mask and gateway are same like Windows.

---

