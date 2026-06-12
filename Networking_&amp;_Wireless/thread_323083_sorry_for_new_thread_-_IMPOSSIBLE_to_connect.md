---
title: "sorry for new thread - IMPOSSIBLE to connect"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by Korrontean on 2006-12-21
[B]
Hi there, I'm trying to connect to the internet from my laptop. I've patiently followed the troubleshooting guide with no results. When I type "iwconfig", this is the result:[/B]

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"izagirre"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**When I type "sudo dhclient ath0":**

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:0e:9b:cf:da:48
Sending on   LPF/ath0/00:0e:9b:cf:da:48
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[B]
Have you got any idea of what could be the problem? THANK YOU VERY MUCH!

Jon[/B]

---

### Post by meng on 2006-12-21
Well it's seems to be not picking up a signal or recognizing an access point. Have you got any encryption, or is it an open network?

---

### Post by Korrontean on 2006-12-21
Thanks!

It has a WEP of 8 characters. I have already typed it in "Properties"

What should I try?

---

### Post by meng on 2006-12-21
Try this:
sudo iwconfig ath0 key restricted s:--------
(insert your wep key in there)

then post the output of:
iwconfig
again

---

### Post by Korrontean on 2006-12-21
Sorry, I can't get it right. What is the exact way to type it?

The code is 12345678.

---

### Post by meng on 2006-12-21
sudo iwconfig ath0 key restricted s:12345678

---

### Post by Korrontean on 2006-12-21
This time the command worked, but the answer to iwconfig is still:


ath0      IEEE 802.11  ESSID:"izagirre"
          Mode:Managed  Frequency:2.467 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by meng on 2006-12-21
Of course I assume the name of the wireless network is "izagirre"
It still reads as though you have no signal? Have you got a signal? Is your laptop sitting right next to the router/access point?

---

### Post by Korrontean on 2006-12-21
Do you think I should go somewhere to find an open network and see if it manages to connect?

(thank you!)

---

### Post by Korrontean on 2006-12-21
Yes, Izagirre is the right name and I do have a signal.

---

### Post by meng on 2006-12-21
Okay as a last resort try:
sudo ifconfig ath0 up

I can't explain why iwconfig keeps suggesting you have no signal.

---

### Post by Korrontean on 2006-12-21
In case it helps, I can add that when configuring the connection from "System" "Administration" "Networking", I can see all the wifi networks available around.

However, when I configure it to connect to mine, "izagirre", it doesn't apparently try to connect. I haven't seen any "connecting" or similar message. It says "Activating interface "ath0" " for a couple of minutes and then stops without any result.

THANKS!

---

### Post by Korrontean on 2006-12-21
Well, after the last command you told me the answer to iwconfig changes:


ath0      IEEE 802.11g  ESSID:"Izagirre"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:A9:07:84:0A
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:10  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Korrontean on 2006-12-21
well, it's actually 


ath0      IEEE 802.11g  ESSID:"Izagirre"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:A9:07:84:0A
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:10  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by meng on 2006-12-21
Well it's identified an access point finally, that's progress! Still a crappy signal, are you physically right next to the access point (just for the purposes of excluding a signal strength problem)? You can try
sudo dhclient ath0
now

---

### Post by Korrontean on 2006-12-21
I am less than one meter away from the router.

When I type the last command, this is the answer:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:0e:9b:cf:da:48
Sending on   LPF/ath0/00:0e:9b:cf:da:48
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by meng on 2006-12-21
I'm afraid I've run out of suggestions, except this last one: make sure there's not some extra security feature on your router, e.g. some have a feature that restricts which wireless cards can connect, by nominating that only certain MAC addresses are acceptable. Make sure you don't have such a feature enabled on yours. Good luck with a solution, sorry I couldn't help.

---

### Post by Korrontean on 2006-12-21
sorry, someone is waiting me for dinner...................THANKS A LOT FOR YOUR HELP...

I hope I'll be able to solve it one day.......................................................I think I'll go somewhere else to check other networks.

thank you again!!! i can't believe how quickly the community responds to anyone asking for help. it's just unbelievable.

---

### Post by Robert.Zapata on 2006-12-21
> **Korrontean said:**
> Do you think I **should go somewhere to find an open network and see if it manages to connect?**

(thank you!)


I was ready to advise that...!! Seems like the issue is with the "acces point" itself..so far everything seems to be fine, the hard part is to make your machine running under Ubuntu to see the wireless card and you alredy pass that section.

Go to a Public Library, University, CyberCafe or some other place that you know has a "Hot Spot".

---

### Post by Robert.Zapata on 2006-12-21
> **Korrontean said:**
> ... i can't believe how quickly the community responds to anyone asking for help. it's just unbelievable.

Forgot that you are at least 6 hours ahead...!!!! 

Yes. This community is really **AWESOME**..!!!! Lots and lots of very nice people always eager to help. Just reading the "How-to's"  and other post on the board you get to learn a lot.

Happy Holidays..!!

---

### Post by Korrontean on 2006-12-22
Thank you, Zapata!

I'm going to the library now, hopefully I'll come back with my ubuntu fully functional!

---

