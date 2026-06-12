---
title: "Very Confusing Netork Dilema"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by Nimaran on 2007-07-05
Okay, I have a dual boot of Linux and Windows XP on my machine. I need to access the internet via my Windows partition from my Linux partition. Is this even possible. Any help would be great.

---

### Post by scxtt on 2007-07-05
you can only access the internet from the current ACTIVE partition - unless you're asking something differnent ... but it sounds like you're asking to run both linux and windows at the same time ... you could do it via VMware and loading your windows partition as a VM, but ... why?

---

### Post by Mr. C. on 2007-07-05
A partition is just a chunk of disk space; there is no relation to networking.

The native operating system provides network support; it also can provide access to that chunk of disk space called a partition.

Let's step back though - what is it that you are trying to accomplish?

MrC

---

### Post by Nimaran on 2007-07-06
There is a piece of software that resides on my Windows partition that allows me to access my network, without it I can't. That software is not available to Linux. So I was wondering if there is a way to some how feed my Linux network connection through my Windows partition. (Though the more I think about it the less likely it seems possible.) Could any of you think of another solution? (Possibly making that software work in Linux via some kind of emulator.)

Thanks in advance for your help.

---

### Post by jefffq on 2007-07-06
I beleive that would depend on what that software actually does. If it is supposed to do something with your local operating system's network connection then I doubt it will work. If it is simply letting some firewall know about your IP, or something less related to your actual operating system, then if you could get it to run in WINE you should be set.

In either of those cases, running this software in VMware will only allow the windows virtual machine to connect.

Is this an office network? I'm just wondering why you need to run this software to get online.

---

### Post by Nimaran on 2007-07-06
The Device is called a D-Link Secure spot and it is a very useful all in one device (firewall, anti-spam, website blocker, etc...) The only downside is it requires a thin client to be installed on each computer. I'm not quite sure on how it works, but I don't want to bypass it or anything just to get the client to work with Linux.

---

### Post by jefffq on 2007-07-06
Well you can always try to get it to run in WINE and see what happens. I can't think of any other options. Maybe route your internet connection through a Windows box or virtual machine running a NAT or some form of network sharing? Probably not worth getting that complicated though.

Or run Windows as the base OS and run Linux on that in VMware. This would definitely work, but I'm not sure what your reasons are for running Linux and if that totally defeats them.

---

### Post by timcredible on 2007-07-06
why not bypass it?  sounds like all it does is protect windows, and you're not running windows, so there's no risk.

---

### Post by jefffq on 2007-07-06
It could also be protecting his children and inbox.

---

### Post by Nimaran on 2007-07-06
NO, I don't want to bypass it and I wanted to try Linux seperate from Windows. I don't wanto to have to rely on Windows to run Linux. I've tried it in Wine, but I don't think it worked. In Wine is it more complicated than just installing the .exe do you have to do some other things?

---

### Post by Nimaran on 2007-07-06
> It could also be protecting his children and inbox.

Exactly.

---

### Post by Nimaran on 2007-07-06
The thin-client is also not just a simple .exe that is run at startup (I don't think) I've looked for it in my startup files and it isn't there, maybe if I could find where it launches from or whatever it does I could get it to work in wine, but all it does is run silently in the background and appears in my system tray.

---

### Post by Mr. C. on 2007-07-06
Nimaran,

The product provides hardware based protection on the device itself - you need no additional software for it to work.

There is also a third component, which is:

> The Individual Computer Layer protects by applying antivirus and spyware detection and removal, pop-up control, and application control.

This functionality as implemented will *not* work in Linux, as that software is intimately tied into a Windows operating system (which is obviously not running on the local machine when Linux is running).

The functionality provided by this Windows component is either available in other native means, or irrelevant for Linux.  Your other systems are protected by the appliance, and your Linux box will be protected via the appliances hardware-based firewall, content filter, etc.  You are not *bypassing* the device.

This is a non-issue.

MrC

---

### Post by Nimaran on 2007-07-06
Yes, but unfortunately you have to have the client in order for the device to let you access the network, so even though I don't need the services it provides I still need it to get online. Yes, I also know you can put the device into low security mode so you don't need the client, but unfortunately for some reason it still asks for the client in Linux, and when I put the device into low security it for some reason wreaks havoc on my Windows computers, don't ask why. I don't know. 

I am very sorry for being so difficult, but I am kind of in a tight fit here, and any more help would be great. So is there any way to emulate the program. Or do I need to seek other alternatives. :D

---

### Post by Nimaran on 2007-07-06
> You are not *bypassing* the device.


Wait, I think I get what you are saying. Is it possible to *bypass* the device?

---

### Post by Mr. C. on 2007-07-06
First, give up on the running their securespot windows client code in Linux - that's a dead end.  Their product is supports Windows and MacOS.

For you to bypass the device, you will need to replace this device with a non-interfering router/firewall which you directly attach to, and then you can place this Dlink device on the net to protect your other systems.  A four-port router/firewall/switch will allow you to connect, and allow the device to connect, giving you two networks.

MrC

---

### Post by Nimaran on 2007-07-06
Ok. Thanks that sounds like it would work. Not sure if I will be able to obtain the equipment though. Sorry to be such a pain but is their any other way to bypass it or anything. (Just trying to see all my options before I take action.)

---

### Post by Mr. C. on 2007-07-07
The device appears to act like a "captive portal", which forces authentication when it is in secure mode.  Unless you set the security settings to Low, the client software is required.  The settings appear to be all or nothing; there does not appear to be per-client settings.

MrC

---

### Post by Nimaran on 2007-07-07
Ok, Thank you it looks like I'll just have to get Low Security mode to work with my other computers. All of your assistance has been greatly appreciated.

---

### Post by Death_Sargent on 2007-07-07
you don't need the dlink software to connect it just makes it easier you should look into how to manually set the connection

---

### Post by Nimaran on 2007-07-08
Thanks for the help I got it working. What I had to do was disable the need for a thin client, and then disable all the security options that required one. Thank you all for your help.

---

