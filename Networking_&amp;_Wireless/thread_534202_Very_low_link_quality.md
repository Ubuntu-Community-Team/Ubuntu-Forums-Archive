---
title: "Very low link quality"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by tiny4579 on 2007-08-24
My link quality for my AR5212 chipset card is very low.  As the iwconfig command shows, it's very low:

ath1      IEEE 802.11g  ESSID:"********"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: *******************   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=19/94  Signal level=-77 dBm  Noise level=-96 dBm
          Rx invalid nwid:5139  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I have attached an output file that may help diagnose and solve the problem.  I am currently managing the network with network-manager, but I was using wpa_supplicant and configured it under /etc/network/interfaces.

---

### Post by foxmulder881 on 2007-08-24
I'm not quite sure what you're asking us to do exactly?!?

Have you tried moving any obstacles in your surroundings that may be interfering with the signal quality?

---

### Post by tiny4579 on 2007-08-24
My brother gets good signal and he's about 10 feet from me, but not much closer to the router.  I used to get a much better connection, but then I reinstalled windows and now both XP and Ubuntu have horrible connections. I put on the same old driver that I had in XP before, which gives about 70-80% for my other brother.

---

### Post by foxmulder881 on 2007-08-24
Then I go back to saying... have you checked for any obstacles? Cordless phones etc... ?

---

### Post by tiny4579 on 2007-08-25
The obstacles I know of are walls and doors.  I tried turning the computer towards the router, but not much improvement.  There's a cordless phone about 10 feet or so from the router.  Not sure if that's affecting it any.  It also disconnects and reconnects a lot, dropping connections with online games.

---

### Post by tgalati4 on 2007-08-25
Could be your neighbors have fired up a wireless router or wireless printer.  If this is a pcmcia card, it's possible that it has flexed causing antenna problems.  I've seen cards damaged through flexing.

It's also possible that the chip is failing.  Most designs are pushed hard and they heat up and degrade over time.

Sometimes you need to remove the card (or power the computer down completely--including removing the battery) to reset the digital trimmers in the card.  When the trimmers are off the antenna loses some of its tuning capability.

---

### Post by tiny4579 on 2007-08-25
It's an Airnet wireless PCI card.  And before posting on this board, about a week ago, I switched wireless cards with anoter Airnet card of the same model because I had the same lack of connectivity.  I will try another switching back to my original Airnet card tomorrow, in case it works correctly, but I think it might be a location problem and not the card.

---

### Post by foxmulder881 on 2007-08-25
> **tiny4579 said:**
> It's an Airnet wireless PCI card.  And before posting on this board, about a week ago, I switched wireless cards with anoter Airnet card of the same model because I had the same lack of connectivity.  I will try another switching back to my original Airnet card tomorrow, in case it works correctly, but I think it might be a location problem and not the card.

If you're having the same problem with different cards then it's definitely an obstacle somewhere screwing with your connection.

---

### Post by tiny4579 on 2007-08-25
My path to the router may run into the air vent system.  If it is an obstacle like that, there's nothing I can do about it immediately.  I used to get about 40% from this same location though.

---

