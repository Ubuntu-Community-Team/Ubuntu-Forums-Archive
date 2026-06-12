---
title: "MAC address issue"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by thierry on 2005-10-21
The MAC address of a network card is stored in Linux in the format 00:00:00:00:00:00 whereas in Windows it looks like 00-00-00-00-00-00 (as far as I know in Macs it's even 00 00 00 00 00 00).
 
This was fine until recently. Now here's the problem : my internet service provider only accepts the use of one card or 1 computer. A few days ago I booted in Windows (I do this very rarely) because I needed Internet Explorer to download something. It took me about an hour. After that I went back to Ubuntu and surprise : no more connection ! I phoned to the support line of the internet provider and they told me "Sorry we don't support Linux". The "expert" I was talking to even went further and told me : "I personally tried with Linux at home but it didn't work so I eventually went back to Windoze". I couldn't believe it :mad: 
 
The fact is that it did work with Ubuntu until now, and it seems I didn't get an IP address anymore because the string format of the MAC address had changed. Another story to put in the category Windows tried to kill Linux ?
 
I went around the problem by using a static IP, but is there no way to use dhcp again ? Perhaps by editing the file dhclient.conf ?
 
I'm not familiar with networks and would appreciate your help or advice.
 
Thanks.

---

