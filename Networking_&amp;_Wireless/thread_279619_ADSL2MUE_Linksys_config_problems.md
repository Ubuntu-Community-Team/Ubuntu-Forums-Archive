---
title: "ADSL2MUE Linksys config problems"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by QBU on 2006-10-18
I am new to Ubuntu & Linux in general and am having some troubles connecting to the internet. ](*,) ](*,) ](*,) 

I use BT broadband option 1 in the UK on an HPPavillioonDV1000 laptop and was previously trying to connect using their Voyager 105 usb modem but never managed to configure it correctly to work, so I invested in a driverless ethernet based modem: the Linksys ADSL2MUE, thinking as I have read in many places that it should be really easy with such a modem to connect to the internet on linux! :confused:  It hasn't proven to be!

I configured the modem and it connects fine to the internet, I can browse sites and e-mail fine on windows. On Ubuntu however whilst the modem is connected to the internet the same way opening a browser and pointing to any website results in a timeout if I set DHCP on the network card/connection in Ubuntu but I can open the modem settings through the browser by going to the modem's IP of 192.168.1.1

Seeing as the modem says it's connected and I can browse to the config page I would expect to be able to browse web pages too. 

Anyone else out there using this modem or any ethernet modem for that matter and had the same problems or just knows how to get this working right?

I hope someone can just tell me the settings to use if not I can post more details of settings for a troubleshooting session if someone who knows networking/modems thinks they can help.

---

### Post by mips on 2006-10-18
Ok so you can ping your router.
Can you ping 209.85.129.104 ?
Can you ping [www.ubuntu.com](www.ubuntu.com) ?

If you can ping the first one then we know your connectivity is fine.
If you cannot ping the second one then we know you have a DNS issue.

To fix the DNS issue usually just involves specifying your ISPs primary & Secondary DNS server IP addresses.

---

### Post by QBU on 2006-10-18
Thanks for the quick reply.:D 

I will try and Ping those addresses when I get home this evening.

Meanwhile I can foresee a possible problem...:-k 
No where have I been able to find the DNS addresses for BT broadband. Does anyone have them/know where they can be found.

I guess if it comes down to it I can request them from BT.

---

### Post by mips on 2006-10-18
Apparently the BT DNS servers change more often than my underwear.
You can try:
ns0.bt.net  217.32.105.90
ns1.bt.net  217.32.105.91
ns2.bt.net  217.35.209.188
ns3.bt.net  194.72.6.57
ns4.bt.net  194.73.82.242
ns5.bt.net  194.72.9.34

Alternatively something more stable like:
[http://european.nl.orsn.net/tech-pubdns.php](http://european.nl.orsn.net/tech-pubdns.php)
IP 217.146.139.5
IP 62.157.101.211
Not that it is considered PC or polite to be quering root servers [-X

Router parameters
VPI = 0 (zero)
VCI = 38
Authentication = CHAP
Modulation = G.DMT
Encapsulation = VC MUX
Encapsulation Protocol = PPPoA

Keep in mind that if you statically configure your DNS servers and they change you are fooked. What you could do is add ALL of them in this order:

217.146.139.5
62.157.101.211
217.32.105.90
217.32.105.91
217.35.209.188
194.72.6.57
194.73.82.242
194.72.9.34

---

### Post by QBU on 2006-10-18
:-D [SIZE="5"]Problem solved!![/SIZE]1:D 

Thank you mips!!:D 

Thank you others who posted elsewhere on the net in forums the DNS's for BTYahoo/BtBroadband!!:D 

I decided to skip the pinging and just try adding the DNS IP addresses I first set the ethernet connection properties for my ethernet card to a static IP address within the range specified by the modem then went to the DNS tab.

The DNS servers I set are:
                          194.72.6.51
                          194.72.9.38
They are the primary and secondary servers from two different pairs posted by others on the net. I just kind of picked them at random from a list figuring that if one no longer worked the other might!

I will try and describe my settings completely in a following post for the benefit of other users.

---

### Post by QBU on 2006-10-18
I guess you were writing your post at the same time as me!!

Thanks for that list.

I have written a rough guide, which I just posted before I saw your reply with all the DNS's. here: [http://www.ubuntuforums.org/showthread.php?p=1633386#post1633386]("http://www.ubuntuforums.org/showthread.php?p=1633386#post1633386")

It may now need some refinement. 

I have actually had it working okay now for some reason in DHCP mode. But only after closing the network settings window having set it, reopeneing, deleting the DNS for th modem which has appeared and entering the two DNS's I listed in my Problem Solved post in this thread. Then closing it again to set it.
Thing is now I opened it again to check my settings to write that walkthrough and noticed it only shows the modems IP under DNS again. I don't know why that is?
With static IP it seems to remember at least.

It sounds like Dynamic (DCHP) would be best though given BTs propensity for changing DNS's, so I'll stick with it if I can and if it keeps working. 

Thank you very much for all the help and advice.:D

---

### Post by mips on 2006-10-18
> **QBU said:**
> 
Thing is now I opened it again to check my settings to write that walkthrough and noticed it only shows the modems IP under DNS again. I don't know why that is?
With static IP it seems to remember at least.


[http://www.ubuntuforums.org/showthread.php?t=128254](http://www.ubuntuforums.org/showthread.php?t=128254)  post#13
[http://www.ubuntuforums.org/showthread.php?t=126533](http://www.ubuntuforums.org/showthread.php?t=126533)  post#17

---

