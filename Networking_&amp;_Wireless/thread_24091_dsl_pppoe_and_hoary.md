---
title: "dsl pppoe and hoary"
date: 2005-04-05
forum: Networking &amp; Wireless
---

### Post by vitti on 2005-04-05
Hallo!  :grin: 
Last Friday (1st April 2005) I downloaded HOARY, and than I started installation on my notebook ASUS LD3840. 
For now, for the things that I saw, it seem very interesting, and probably I' ll move also my desktop to UBUNTU.
I have a small home network with one desktop (XP), one MAC mini and the notebook with the new HOARY.
But I found a problem connecting to internet; :? 
For this I use a LAN DSL modem (DHCP server) connected to a LAN switch. and I have  configured pppoe using pppoeconf.
Normally my notebook reach, and it is reached every node of the lan, and the file /etc/resolv.conf contains just one line like this:
"nameserver xxx.xxx.xxx.xxx" (DHCP server address)
When I try to start the internet connection with command:
"pon dsl-provider"
I could see with "Plog" that the connection it was established, and the 2 dns servers from the provider.  :grin: 
At the same time I saw that my /etc/resolv.conf contains just  the 2 DNS addresses, and I suppose that everything was ok.
But when I tried to reach any site on the web with the browser, i got the message that it cannot resolve the url!  #-o  #-o 
Looking at my /etc/resolv.conf,  :-o NOW IT CONTAINS AGAIN JUST ONE LINE! THE ORIGINAL ONE, THE ONE WITH THE DHCP SERVER ADDRESS!
I re-wrote the file with the 2 DNS received, and after a while it was again with just the original ONE line! ](*,) 
It seems that *anyidontknowwhicprocess* (DHCP Client?) every 60 seconds tries, with success!, to overwite the /etc/resolv.conf with the information related to my local LAN, and forgotten the ones received from the provider.
Is there anyone that knows this behaviour? 
May I change in any the DHCP client configuration? :twisted:

---

### Post by kahping on 2005-04-08
have you tried disabling DHCP and trying to connect afterwards? that helped solve my problems, but then again, i don't have a LAN DSL modem. i'm guessing yours is a router/modem? mine's just a normal modem(no DHCP, bla bla). it's worth a shot if there's no better ideas...

also try searching the forums(there's a "search" near the top of the page) for pppoe and see if you find anything helpful.

good luck

kahping

---

