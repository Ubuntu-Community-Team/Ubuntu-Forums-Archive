---
title: "Problems connecting to a Bluesocket network"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Munksgaard on 2007-09-20
Hi everybody!

Recently, my old laptop ceased to work. While i am waiting for enough money to buy a new one, I am using a business-style dell laptop i lend. This works perfectly, but i had to install Xubuntu 7.10 to get some speed into it (i have been using Ubuntu prior to that).
Everything works great, wireless too, except when I try to connect to my schools network.
My school uses some sort of wireless authentication software called bluesocket. The network itself is not protected by WEP or WPA, and I can connect to it just fine. Then, when you open up your internet browser, it should take you to some local domain, where you have to authenticate using a username and password before you are granted access to the internet. I just don't get to that site. When I open firefox, it hangs for a while, and then tells me that the server could not be found.

Why is this? When I try from any Windows machine, even using firefox, it works just fine.
I would be very grateful for any support on this matter, as linux is starting to look really lousy in the eyes of my schoolmates :)

Thanks in advance
Philip

---

### Post by robert_pectol on 2007-09-20
Once you associate your laptop with the access point, do you get an IP address?  If so, can you ping the default gateway?  Can you resolve any names to IP addresses?  (ex:  enter, "dig google.com" at the command prompt)  Even though the captive portal controls access to the Internet, most still rely on a functional resolver at the client end.  Basically your networking has to be fully functional before the captive portal can, "capture" and redirect your traffic to the login portal.

---

### Post by Munksgaard on 2007-09-20
As already mentioned, my wireless works just fine on my home network, which is protected via WEP, but i guess i'll have to try the other stuff out tomorrow in school. Ill report back.

Edit: Oh, and I should mention that, even if I go to my homepage, which is google, the address will change to that of my bluesocket login site, but as I said it just hangs there and eventually reports that it couldn't find the server.

---

### Post by Munksgaard on 2007-09-21
I get an ip address on the LAN, i can resolve hostnames via dig, but i cannot ping my the bluesocket site, if that's what you meant?

What i try to do is to ping the .local domain which pops up when i start firefox, but which won't be found. It tells me that the host is unknown.

---

### Post by unclesamslair on 2007-10-29
I am having the same trouble at my school where they use a bluesocket network. Before, it would just take a really long time to connect and then I would be fine, but now it won't connect at all. I'm using Gutsy with an Inspiron 1501 and the restricted drivers for the Broadcom Wireless card. Based on how many replies this got, I'm not expecting a response from anyone who can help us.

---

### Post by unclesamslair on 2007-10-29
> **unclesamslair said:**
> I am having the same trouble at my school where they use a bluesocket network. Before, it would just take a really long time to connect and then I would be fine, but now it won't connect at all. I'm using Gutsy with an Inspiron 1501 and the restricted drivers for the Broadcom Wireless card. Based on how many replies this got, I'm not expecting a response from anyone who can help us.

btw, when I went to get help from the people at my college the first question they asked me was "What kind of Windows are you using?" ********

---

### Post by unclesamslair on 2007-10-29
I opened up firefox typed "about:config" in the URL box and then typed ipv6 or something liked that and doubleclicked on the option to turn ipv6 off. Worked just fine. Let's see if it last though.

---

### Post by unclesamslair on 2007-10-29
> **unclesamslair said:**
> I opened up firefox typed "about:config" in the URL box and then typed ipv6 or something liked that and doubleclicked on the option to turn ipv6 off. Worked just fine. Let's see if it last though.

worked for about 3 hours then died.

---

### Post by aknight_sa on 2007-11-21
good day,

has anyone been able to solve this issue??

i am trying to connect to a guest network at work which uses a captive portal by Aruba... but i get the same problem as you guys have..
i am able to ping my gateway, but not the proxy, and i dont get the user name/password page..


Thanks
oh yes.. i am using Gusty on a Dell latitude D800

---

