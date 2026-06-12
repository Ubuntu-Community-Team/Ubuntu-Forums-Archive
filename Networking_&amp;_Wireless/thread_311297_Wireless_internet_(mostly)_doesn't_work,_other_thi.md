---
title: "Wireless internet (mostly) doesn't work, other things do"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by MCC on 2006-12-02
I have a strange problem with my wireless network connection. The only webpage I have gotten to load is newegg.com, but it took about a minute for it to connect and loaded quickly afterwards. Pings to other sites almost always don't return anything. But, I can log into my DSL modem and browse through its settings almost instantaneously. I inserted an audio CD and it successfully did a track lookup in a few seconds. :confused:

Hardware/setup:
IBM Thinkpad Z60t w/ Belkin Pre-N PCMCIA card
Ubuntu 6.10
Drivers through ubuntu-supplied ndiswrapper module
Routers: Belkin Pre-N/Actiontec GT701-wg DSL modem
Connection: WPA-PSK w/ WPA-supplicant

The same problems occur with or without WPA as well as with either router. Pings to the modem work with 0% loss and anywhere from a 1.41-10.3ms response. I should also note that a direct LAN connection to the Belkin router works with no problem, and XP Pro has no problems with the same setup. I also tried changing the wireless channel and putting the thinkpad's IP in the DMZ. Neither did anything at all to the connection.

---

### Post by teaker1s on 2006-12-02
sounds like a DNS issue try a static ip and manually enter your dns.

what chipset is your card and are you using native driver or ndiswrapper?

---

### Post by MCC on 2006-12-02
It's an Airgo chipset, and I'm using the Netgear WPNT511 driver as suggested [here]("http://www.linuxquestions.org/questions/showthread.php?t=379814&page=3") with ndiswrapper. I'll reboot now and try your suggestion.

Edit: I tried setting it up statically with the same result. It's resolving DNS just fine. In fact, Firefox grabs the page title within 5-10 seconds after I attempt to go somewhere. It seems that it can get the code in the head of a web page but times out before it gets anything else. It had sent about 250 packets and received roughly the same number, so it looks like data just isn't getting to my laptop. Debian Etch did basically the same thing, BTW, and I couldn't find a solution. I'll see if I can try the built-in Atheros card.

Edit 2: The atheros won't connect and I've had enough wifi configuration for one day. One thing I did notice is that even after clearing the firefox cache and going to modem config pages I haven't been to, the sent and received packet count did not increment nor did the systray app show any traffic at all. Hmm....

---

### Post by MCC on 2007-01-16
Update for possible future visitors to this thread with the same problem:

The issue has been solved. Apparently the GT701-WG modem has some problems routing packets to/from newer 2,6 kernel linux machines. A [firmware upgrade]("http://www.qwest.com/internethelp/modems/gt701-wg/index.html") (which requires Windows 98SE+ BTW) solved my problems. Don't use the modem's built-in firmware upgrade check (under utilities), as this failed to tell me that there was a new version available.

---

