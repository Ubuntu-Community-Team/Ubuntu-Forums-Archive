---
title: "Wireless-only office network - which authentication to use?"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by DigitalFudge on 2008-08-19
Hey Guys, 

I'm designing a wireless only office network. I intend to have multiple access points and at at least 10-15 clients.

I'm wondering whether I should dabble in using a WPA-Enterprise type authentication, or whether I should stick with a more traditional WPA-PSK setup. 

I've never used WPA-Enterprise and from what I've read it sounds really interesting. Regarding WPA-Enterprise I would  like to know:

[LIST=1]
[*]Is it broadly compatible with Windows/Linux/Macs/Smartphones?
[*]What does it look like to the user? I can only find info on the web about how the back-end works. What does a user trying to join a WPA-Enterprise network actually see? Does it appear as an open network, and when you want to join it it asks for your username and password?
[/LIST]

If I go with the WPA-Enterprise route I will have an ubuntu box hosting the FreeRADIUS.

Thanks guys!
DF

---

### Post by HalPomeranz on 2008-08-19
If the network is entirely wireless, then it's likely that you're going to end up extending your network reach by chaining access points together in "bridged" mode.  In this case, you have to use WPA-PSK because I have yet to find an access point that supports WPA-Enterprise in bridged mode.

In answer to your questions:

1) WPA-Enterprise works fine with Windows/Mac/Linux.  However there are lots of smartphones and other embedded wireless devices (printers, etc) that are unable to deal with WPA-Enterprise.

2) From the user perspective, the hardest part of WPA-Enterprise is getting the network certificates installed properly.  My experience is that normal users can't handle this process and it needs to be handled by the IT staff as part of the basic system setup process-- or at least scripted by the IT staff so that regular users can install the certs easily.  Also note that the certificates expire after some period of time, so you end up having to repeat this process every 1-3 years (depending on your certificate lifetime).  

After that, however, things are pretty straightforward.  The network shows up as a secure network (if you have SSID broadcast enabled), but assuming you have the certs set up properly the connection should be automatic.

---

