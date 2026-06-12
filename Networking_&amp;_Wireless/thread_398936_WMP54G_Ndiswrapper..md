---
title: "WMP54G Ndiswrapper."
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by cebert on 2007-04-01
Hello.

I need a basic how to. I have searched around the forums but have not found anything that helps me, to the point where me wireless is success. 

I have a Linksys WMP54G wireless PCI card. And will be using Ndiswrapper. (I haven't downloaded anything at all yet, compleatly fresh copy of Ubuntu.)

I hear a lot about egdy and dapper, how do I know what I have?

I found two tutorials on this site,

[this](http://ubuntuforums.org/showthread.php?t=296822&highlight=wmp54g+ndiswrapper+howto)
and
[this](http://www.ubuntuforums.org/showthread.php?t=132980)

However both the links to the ralink website, 404 me... 

Via more research I found [this](http://www.ralinktech.com/ralink/Home/Support/Linux.html) page but I have no idea which link I should choose.

The tutorials provided in the forum arn't descriptive enough for me, so does anybody know of a complete newbie guide for my wireless card model with ndiswrapper elsewhere?

Thanks for your time.

Edit* I am using NO security, this is what throws me when others are explaning how to set it up w/ security, I don't use any encryption.

---

### Post by doddi on 2007-04-01
Hi cebeert,

This is the link that I used to get me going. So just follow this and you should have no problems. The only thing it doesnt mention is that at one point I needed to reboot to get rid of the original BCM driver. I am sure there is a more elagent way but I am a newbie :) 

[link]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

doddy

---

### Post by cebert on 2007-04-01
I'm not using a Broadcom, doddi.

I did some more searching, and have no found out why resources are fairly scare for it. Because it takes hardly any setting to get from step 0 to 1!

But... I have my card on and flashing. I set up the device in network setting, by going into properties setting the ESSID. And I set my connection settings to DHCP.

I have not got any security on my Access Point. But it doesn't seem that I have the option to choose no security. Is it compulsory in Linux to have some form of key?

So far thats all the config setting I have set up. I tryed going into google but just get server not found, what am I doing wrong?

Thanks.

---

### Post by doddi on 2007-04-03
Like I said I am no expert but I would think that you should be able to follow the same steps in the link that I provided but to use the driver for your modem rather than the one documentated.

I am not using any security on my wireless so I know that will not be your problem.

What happens if you type *iwconfig* in a terminal? if your SSID is in there then I guess you are a step in the right direction.

Did you compile ndiswrapper from source? with your latest headers? Also, the driver that you are using within the ndiswrapper...does it actually work in a windows environment, i.e. it is for your hardware?

Is that driver installed in ndiswrapper, to find out type: *ndiswrapper -l* for a list of installed drivers.

Again I would urge you to at least read through the link I provided to gain an understanding of what it is you are doing? I do think it will help you out even though it is for hardware.


Someone please correct me if I am wrong...I am new to this...only used Linux for a couple of weeks.


Doddi

---

### Post by MeeMaw on 2007-04-03
Have you tried typing       sudo lspci      to find out what driver you actually have?  I have a Linksys WMP54g and I don't use ndiswrapper on Edgy. (However, Linksys used several chipsets in their cards and we have to pin down which one you have.)

Post the output of lspci and let's see if we can figure out what you need.

:)

---

### Post by MeeMaw on 2007-04-22
BUMP
So, cebert, did you figure out which driver you need?

:)

---

