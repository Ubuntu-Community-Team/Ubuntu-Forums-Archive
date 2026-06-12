---
title: "I don't know my wireless network key"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by PatrickMay16 on 2006-12-15
Hey guys.

I just got a PCMCIA wireless network card, and it seems to have been detected by Ubuntu just fine (shows up as wlan0 in the GNOME network configuration tool).

Just one thing, though. I have no idea what the key for our wireless network is, and my brother (who set it up) is currently in another country.
I have admin access to all the other computers in the house, though, including my dad's laptop which is setup to use the network fine.

So, does anyone know a way of which I can retrieve the key from my dad's laptop, or some other way determine what the key is?

Thanks.

If you think I'm asking this to break into someone else's network, I can give you good proof that I am telling the truth; a photo of me holding paper with your user name, and also the laptop in the background.

---

### Post by RudolfMDLT on 2006-12-15
Hi,

There are two ways of determining this:

1) All wireless networks have an Accespoint. Log on to this access point and under the wireless settings there should be a security option or a WEP subheading. Under this heading you will find the KEY.

2) In the windows wireless configuration utility there is a option for displaying the key that your dad typed in, that is, display the key not with *'s but actual characters. I cannot remember the exact place for it but if you sniff around it should be somewhere. Also in Ubuntu you need to manually configure a wireless connection that requires a KEY. I use Kubuntu, so I won't be able to help you in gnome perfectly.

You could try looking in your dad's networking config file and see if he manually setup the wireless connection.

sudo nano /etc/network/interfaces

Goodluck,

Rudolf

---

### Post by PatrickMay16 on 2006-12-15
> **RudolfMDLT said:**
> 
2) In the windows wireless configuration utility there is a option for displaying the key that your dad typed in, that is, display the key not with *'s but actual characters. I cannot remember the exact place for it but if you sniff around it should be somewhere. 

Great, thanks. Though i've been looking around and I'm having trouble finding it. (my dad's laptop is running windows xp).
If anyone knows exactly where it is, that would be very very helpful. Thanks guys.

---

### Post by RudolfMDLT on 2006-12-16
Well. in all honesty most people use the Wireless utility that came with the wireless adapter in windows and not the windows default configuration utility so there are a diffrent couple of places that this could be. What card is your dad running and what application does he use to configure his Wireless card, 3rd party or the Windows utility?

---

### Post by brownkenny on 2006-12-16
I've had good luck with the Wzcook program in the aircrack package.  It should do the trick for you.
[http://www.wirelessdefence.org/Contents/Aircrack-ng_WinMain.htm]("http://www.wirelessdefence.org/Contents/Aircrack-ng_WinMain.htm")

---

### Post by PatrickMay16 on 2006-12-16
> **brownkenny said:**
> I've had good luck with the Wzcook program in the aircrack package.  It should do the trick for you.
[http://www.wirelessdefence.org/Contents/Aircrack-ng_WinMain.htm]("http://www.wirelessdefence.org/Contents/Aircrack-ng_WinMain.htm")

This really did the trick. I'm typing this to you now from my laptop.

Thanks very much!

---

