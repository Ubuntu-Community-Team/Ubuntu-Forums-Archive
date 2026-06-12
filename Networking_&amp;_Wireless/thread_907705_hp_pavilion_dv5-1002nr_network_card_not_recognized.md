---
title: "hp pavilion dv5-1002nr network card not recognized"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by lin00bie on 2008-09-01
Hi,
I've installed ubuntu via the alternate-i386 dvd. I've been having a major problem with the network card. When I click on the network manager icon, on the top right, it doesn't show wireless connections. I don't think the card is being recognized. How do i go about installing the drivers for my card?
From the device manager, on vista, i have the Atheros AR5007 802.11b/g wifi adapter. Please help me install these drivers.

---

### Post by alan.nafa on 2008-09-05
I have the same problem. The quick touch buttons work, but the volume doesnt actually control master volume. Plus the card is detected i just cannot turn it on, because the wifi button is touch sensitive and refuses to turn blue (on)

---

### Post by jackson_vkh on 2008-09-06
I'm having the same problem as well.  At the present time, my network card does not work, USB keys work sometimes, and other times they do not, my card reader is the same.  I have no audio controls, and my video is jumpy.  Not having a good time here.

---

### Post by lin00bie on 2008-09-07
has anyone found a solution?

have you guys tried other distros? would that fix the problem? i know some distros come with comercial drivers.

---

### Post by gsilva on 2008-09-18
Take a look to this [http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

---

### Post by serian on 2008-10-07
> **lin00bie said:**
> Hi,
I've installed ubuntu via the alternate-i386 dvd. I've been having a major problem with the network card. When I click on the network manager icon, on the top right, it doesn't show wireless connections. I don't think the card is being recognized. How do i go about installing the drivers for my card?
From the device manager, on vista, i have the Atheros AR5007 802.11b/g wifi adapter. Please help me install these drivers.

You have to download madwifi from this site [http://madwifi.org/wiki/UserDocs/GettingMadwifi]("http://madwifi.org/wiki/UserDocs/GettingMadwifi"). I had same problem and had solve it. 
I did't do anything to do it work.It was worked by itself.
You can find answer to how install madwifi in searching system of this site.
And you prorably have to install "libgphoto" packages.

---

### Post by lin00bie on 2008-10-11
thanks for the replies.
i tried both of them but they didn't really work. i was playing around with it from a few guides i found online and one of them enabled my card. i was able to surf the web via wireless but after booting vista and coming back to ubuntu, it stopped working. now i can't get it to work again.

when i type in iwconfig i get the following
```
lo   no wireless extensions.
eth0 no wireless extensions.

```

---

### Post by serian on 2008-10-14
> **lin00bie said:**
> thanks for the replies.
i tried both of them but they didn't really work. i was playing around with it from a few guides i found online and one of them enabled my card. i was able to surf the web via wireless but after booting vista and coming back to ubuntu, it stopped working. now i can't get it to work again.

when i type in iwconfig i get the following
```
lo   no wireless extensions.
eth0 no wireless extensions.

```

Show output from command
```
lspci

```

---

### Post by Charybdis3 on 2008-10-15
Hello, I have the same problem with an hp pavilion dv5 I got yesterday. Neither my wired or wireless internet works by default, so I can't get any updates to fix it. Hope a solution comes soon.

Thanks

---

### Post by chuwys on 2009-03-27
hi all hp dv5 users
after looking like crazy a lot of pages i found exacly what we need!

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

good luck

---

