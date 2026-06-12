---
title: "Wireless in Gutsy causing laptop to freeze"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by zaomaster on 2007-10-25
I've got a problem with my wireless card set up.  I'm using a 3Com pcmcia card 3CRGPC10075.  In Feisty it was working fine (though I've never had stellar wireless connection with Ubuntu :( ) but now in Gutsy it's causing my whole system to freeze up.  I'm, unfortunately, running ndiswrapper for the driver.  Here's some information:

ndis: mrv8335x : driver installed
        device (11AB:1FAA) present

iwconfig: wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lspci: 03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

I can connect sometimes (but not often) and in the process of trying to connect it will freeze my system.  Any thoughts?

thanks.

---

### Post by Mitsuhashi on 2007-11-14
I have the same issue.
My wireless card is correctly recognized, I can scan for wireless network, but, when I try to connect, the connection is made (I can see the IP assigned to my laptop from the access point admin page) and the link led of my wifi card is turned on, but all is freezed.
I don't know if this can help in someway but I've seen that when this happens the capslock led start to blink.

---

### Post by Socket370 on 2007-11-18
I too am having the same problem, right down to the blinking Caps Lock light when it freezes.

---

### Post by lauzonaj on 2007-11-28
yeah... me too... my hp omnibook 6000 freezes using  both the default driver or the ndis wrapper... caps and other lights blink when it freezes up

---

### Post by eagletip on 2007-12-05
Yeah,this is way too familiar. Installed gutsy and all was well until I decided togo wireless. Not much on anything except the love of gutsy so can't figure out the solution.

---

