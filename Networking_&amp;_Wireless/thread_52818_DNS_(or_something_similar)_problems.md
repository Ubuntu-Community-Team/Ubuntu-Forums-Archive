---
title: "DNS (or something similar) problems"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by fivre on 2005-07-29
Recently, my ISP gave me a new number, and told me the current one would be phased out. 

Sadly, I can't get this new number to work, despite having tried several DNS IPs (all of which work with the old number).

The number connects as normal, but I cannot access the internet. (E.G., Firefox can't find anything, IRC won't connect.)

The new number does work properly with Windows 2000, however.

---

### Post by BrianB on 2005-08-20
I am having a similar problem but I can't seem to find a solution. Anybody know exactly whats wrong?

---

### Post by gned on 2005-08-29
My Ubuntu is slow to resolve urls, and I suspect it is related to DNS problems. Should I edit my hosts file?

---

### Post by gned on 2005-08-30
I was right, it was a DNS problem, but not a host file fix. All I needed was to get the IP addresses for my ISP DNS servers and add them to the DNS settings in my network settings ( Computer - System Configuration - Networking - Network Settings menu, and click the dns tab).

I had used the DNS IP from my WinXP machine's ipconfig message, but it turns out that it just had the IP of the adsl modem as the dns. Thus, when I used that IP in my Ubuntu settings, it had difficulty resolving urls. Not surprising really, there is only so much one can expect from a modem.

So, dear slow resolution sufferers, look up your service provider's website and get the correct DNS server IP address numbers. It worked for me. My Firefox is now quick as a flash!

---

