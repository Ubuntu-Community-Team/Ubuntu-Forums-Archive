---
title: "Network via 2WIRE Wireless PC card is not connecting !"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by andre-w on 2006-07-22
Hello,

After some time neglecting my ol' Ubuntu 5.10, I decided to install the new 6.06 and take my half-life Toshiba Satellite away from the DSL modem and make use of its wireless connection. However, I am experiencing difficulties with the wireless part of the story. While I am able to connect to the internet using my ethernet PCMCIA card, when it comes to my wireless card the only thing I get from FireFox is "Server not found". 

My modem is a 2WIRE HomePortal 1000HG ( [http://www.2wire.com/?p=266](http://www.2wire.com/?p=266) ), and my wireless card is a 2WIRE 802.11g PC Card Wireless Adapter ( [http://www.2wire.com/?p=118](http://www.2wire.com/?p=118) ), and both are ok. Before my Ubuntu 6.06 fresh installation, I did install the original Windows restore CDs just to ensure my modem and card would work via wireless connection, and after installing the right drivers, they did.

Here is what I am doing... first I go to System > Administration > Networking... and I open the properties of Wireless connection (The interface eth1 is active)... so I enter Network name (ESSID): 2WIRE123... Key type: Plain (ASCII)... WEP Key: 1234567890... and Configuration: DHCP. Then I get Activating interface "eth1"... and still no internet. Also, on my wireless card, I see the LINK LED on, and the ACT. LED off.

I remembered when I set the AirPort on my Mac... I had to enter $1234567890 for the WEP key, because the $ was required for non-Apple networks. I tried the $-thing on my Ubuntu just in case, but it did absolutely no difference.

Other than the Network settings, I have no idea what to do... not to mention command line configurations, so any suggestion will be very welcome.

Thanks in advance,

Andre W.

---

### Post by tturrisi on 2006-07-22
Try:

Network name (ESSID): 2WIRE123
Key type: HEX...
WEP Key: 1234-5678-90 (hyphen after every 4 chars)

In the wireless config section of router control panel set Authentication Type as Open System instead of Shared or Mixed.

This works for me using a 2wire 802.11b.

---

### Post by andre-w on 2006-07-22
Thanks for the reply, tturrisi!

I tried exactly as you recommended... unfortunately my problem remains.

Here is what I did... First I opened Ubuntu's Network settings and set Key type to Hexadecimal and hyphenated WEP Key according to the given suggestion. The second part was the tricky one, but in the end I got it.

Using my Mac (already connected via wireless), I accessed my router: [http://homeportal/](http://homeportal/) > View the home network > Wireless Settings (Edit Settings). After entering my System Password, I looked my Wireless Security's Authentication... it was already WEP-Open... the other alternatives were WEP-Shared and WEP-PSK, so I did not change the settings assuming it is the correct option.

For now, I will keep waiting the next post.

tturrisi, thanks again!

---

### Post by dus10 on 2006-08-02
what kind of ethernet pcmcia card do you have on the machine and did it work right from installation?

---

### Post by adottedfellow on 2006-08-03
Try to directly connect the 2wire first on the Ubuntu PC and try if it connects.

---

### Post by Dave Klinzman on 2006-08-04
I don't think that the Plain ASCII text string for a WEP key works at all.  According to the man page for iwconfig (under key/enc) a passphrase is not supported.  I do know, however, that the Hex string works because that is what I am using.  Either turn encryption off on the wireless router (to get an initial connect) or specify a key in the router but enter it's equivalent hex string in the Network Manager key dialog in Ubuntu.  Good luck!

---

