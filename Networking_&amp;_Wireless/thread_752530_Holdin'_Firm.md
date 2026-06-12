---
title: "Holdin' Firm"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by Exsecrabilus on 2008-04-11
So I recently installed bcm43xx-fwcutter because it said that if I installed that, I could turn on WLan and then I finally could wirelessly connect it to my Linksys or whatever and finally get Internet.

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Screenshot3.png[/IMG]

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Screenshot4.png[/IMG]

But when I did, and went to enable it, I discovered something: I don't get it.

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Screenshot5.png[/IMG]

Please help, where am I going to find the firmware to enable this and get Internet?

---

### Post by Exsecrabilus on 2008-04-14
Please? Someone help, please.....

---

### Post by kutjara on 2008-04-14
> **Exsecrabilus said:**
> Please? Someone help, please.....

That entry in the Hardware Drivers panel essentially means that you've installed a "wrapper" for your card's Windows wifi drivers. You need to extract the .inf and (sometimes) .sys files from the driver installation .exe file (HOWTOs can be found by searching here or via Google), and install them, so that the wrapper can use them.

What you have now is a translation program that communicates between Linux and the Windows drivers for your card. It actually needs the Windows drivers to work properly.

If you search on "Broadcom 43xx" here on the forums, you'll find quite a few threads describing exactly how to get things set up.

ON EDIT: Oops, I didn't notice it was looking for the apsta file. I saw the panel and thought it was the usual "I can't find the driver" nag message. The post below gives the correct advice.

---

### Post by Het Irv on 2008-04-14
you need to download the file get it to work,  [wl_apsta.o ]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")

Download this to a jump drive and transfer them over. And then use the local file option.

---

### Post by Exsecrabilus on 2008-04-16
> **Het Irv said:**
> you need to download the file get it to work,  [wl_apsta.o ]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")

Download this to a jump drive and transfer them over. And then use the local file option.

After I do that, how will I enable WLAN and how will it detect my Linksys then connect me to the Internet?

---

### Post by Exsecrabilus on 2008-04-16
Wow, this forum seems to be active, it's been 2 hours and this topic already fell onto the fifth page!

Can someone please answer the above post though? :( :confused:

---

### Post by Het Irv on 2008-04-17
Sorry about the wait, somehow this didn't show up in my control panel.

If you have downloaded the file, move it to your desktop and then go through the steps you took in your first post.  When you get to the last dialog box you should be able to browse to the desktop and find it.

---

