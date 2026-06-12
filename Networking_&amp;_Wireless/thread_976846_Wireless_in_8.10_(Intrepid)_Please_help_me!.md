---
title: "Wireless in 8.10 (Intrepid) Please help me!"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by phantom3113 on 2008-11-09
This wireless issue is driving me crazy. I have a Realtek 8187b wireless card. I've tried everything to get my wireless working, which I have (sort of). I scrapped Network Manager for Wicd, which is what got my wireless working initially. I've even downloaded and installed the windows drivers using ndiswrapper. However, I now have terrible wireless signal!. Three feet from my router I have 90% signal and 25 feet down the hall I have 35%! Is there anything I can do?

Laptop specs:
Gateway T-1621
Ubuntu 8.10 (Intrepid Ibex)
Realtek 8187b

Edit: Through my adventures on the internet, I have found a permanent fix for the poor performance of the OTB drivers for the Realtek rtl8187b cards (In 8.10 anyway. 9.04 is untested on my part as of yet). Following the thread here: [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092) I was led to another thread: [http://ubuntuforums.org/showthread.php?p=7157415#post7157415;](http://ubuntuforums.org/showthread.php?p=7157415#post7157415;) It contained the official linux drivers for the rtl8187b cards, directly from Realtek (attached).

I've tried the official drivers AND the new compat-wireless package, and the official ones have worked the best for me. To install the drivers:
1. Download driver package
2. Blacklist old driver;
   -in terminal run gksudo /etc/modprobe.d/blacklist
   -at the very end, add "#old drivers" (no quotes) and below that, "blacklist rtl8187"
3. Move the driver package to /home and extract it using "tar -xvf rtl8187B_linux_26.1052.0225.2009.release.tar.gz" then enter that directory (cd rtl*)
4. run sudo make; sudo make install
5. reboot and enjoy your flawless wireless :)

*A note though: I ended up installing these twice (messed up the first time) and both times it changed wlan0 to wlan1. If you use wicd, you'll need to change the settings so that it uses wlan1 instead after you reboot. Network Manager should change automatically.

Finally, these instructions and this fix were found by pimpinjg in the second thread. I'm merely passing them on so all may be helped by them :)

---

### Post by greatwolf on 2008-11-09
Here, you might want to give [this]("http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/") a try.

How much of it is working? What have you tried so far? Do you see the same kind of signal strength degradation in windows? A google show that this chipset is supposedly supported in kernal 2.6.27.

---

### Post by oldsoundguy on 2008-11-09
If this is a built in card in a laptop, can't be of help.  If it is a card in a desktop .. get rid of it and buy a universal wireless card such as the D-Link DWL-520G (cheap on eBay) .. I have them in a couple of Intrepid computers, a Mint computer and a Windows computer and have had ZIP in the way of issues.  Installed out of the box.

---

### Post by phantom3113 on 2008-11-10
The card in the laptop did come built in. Here's a sort of "timeline" of my wireless nightmares:

Installed 8.10 - attempted connecting to internet - wired and unsecured wireless networks working fine (shows that the card is working with Ubuntu) - tried to connect to home network (encrypted with 128 bit WEP) - Network Manager asks for WEP encryption key, so I input it - 20-ish seconds later, repeat same thing and so on.

Basically, I can connect to any network unless it has any kind of encryption. I even tried inputting all the nitty-gritty details manually for the WEP network. After reading a few other threads, I've tried the Wicd approach and ndiswrapper with the drivers (intended for 8.04). Wicd worked, but that's were the signal loss came in and after a bit of fiddling, failed to connect at all. After that didn't work, I decided to try and get Network Manager back and try that with the drivers, but I ultimately had to do another clean install of 8.10.

When I had windows (Vista...), I could always connect immediately/flawlessy to the network (after the initial setup) with 100% signal. The laptop also has a wireless on/off switch on the corner.

Sorry for the length...

---

### Post by phantom3113 on 2008-11-10
Blah-double post

---

### Post by oldsoundguy on 2008-11-10
Laptop!  PROPRIATARY as HE** and Realtec is even worse.  At least Broadcomm has made a couple of steps in the right direction but has a bit to go.

You will need someone that knows that junk to help you set it up .. and it may take some time as those clowns change their architecture as often as I change my sox, so backwards engineering is a nightmare for the code writers.

You just might consider getting a USB wireless dongle from a REPUTABLE manufacturer and going with that.

---

### Post by phantom3113 on 2008-11-11
That doesn't really fix my problem, unless you're referring to the signal loss with Wicd. My card works fine, Network Manager just keeps looping the authentication key request for encrypted networks.

---

### Post by buccaneere on 2008-11-11
I have seen, while searching for proper wireless configuration for my 3 wireless boxes, that completely different drivers work for some cards, where one driver worked at 54mbs, the other at 11mbs, same card.

I have not seen where signal strength was influenced by driver module...

Are you sure your strength problem is because of authentication cycling? Have you tried with encryption off?

---

### Post by prematurebaby on 2008-11-11
You need to search around Ubuntu forums. I eventually found my answer to the wifi problems. Alot of people had wireless problems, so you're not alone.
Pretty much you need to edit the Blacklist and /etc/modules/ but for your card type I'm not sure what I'd put.

---

### Post by phantom3113 on 2008-11-13
Ironically enough, I've actually been finding a bunch of other people with similar problems. :p Through other searching (and comparing) I actually like how Xubuntu 8.04 is looking, so I'm gonna try that one and see how everything fares. Even with these frustrations, I'm having a better time than with Vista. :)

---

