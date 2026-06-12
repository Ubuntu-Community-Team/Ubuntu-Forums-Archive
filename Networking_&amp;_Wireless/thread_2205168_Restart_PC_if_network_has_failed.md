---
title: "Restart PC if network has failed"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by ian_c2 on 2014-02-12
Hi,

I have a set up Lubuntu to open google-chrome when starting up. It displays a web page that refreshes/reloads every X seconds only if there is a internet connection. If there is no network connection I'd like to have the machine reboot so that the browser can restart along with (hopefully) the internet connection.

So basically I want to reboot every time there is no internet.

---

### Post by ian-weisser on 2014-02-12
How are you testing if there is an internet connection?
Or is that your question?

---

### Post by tgalati4 on 2014-02-12
It's not clear why you would need to reboot the computer if the network goes down.  Linux is quite robust with or without a network connection.  It handles those two situations quietly and without fuss.  Perhaps explain exactly what problem you are trying to solve.  Rebooting if the network goes down makes no sense.

But if you insist, write a script and place it in a cronjob to run every 10 minutes.

Psuedo Code:

tgalati4@Mint14-Extensa ~ $ ping -q -c 5 192.168.1.1 | grep "100% packet loss"
tgalati4@Mint14-Extensa ~ $ ping -q -c 5 192.168.1.2 | grep "100% packet loss"
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4000ms

So ping your local router.  If your router does down, no internet.  You could ping [www.google.com](www.google.com), but they will get annoyed, so ping your local router or some other website that you need access to.  My router at 192.168.1.1 is up so there is no output.  There is no device at 192.168.1.2 so you get an output "100% packet loss".  With that program a conditional to reboot the machine using *sudo shutdown -r now*.  There is probably a simpler way, but I'm too tired to figure it out.

---

