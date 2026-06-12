---
title: "&quot;system policy prevents modification of personal network settings&quot;"
date: 2021-05-24
forum: Networking &amp; Wireless
---

### Post by alexanderedward2 on 2021-05-24
Hi,
*I have recently installed 20.04 on a laptop
*I initially connected  it to my home wifi, and my phone hotspot
*I am now elsewhere and unable to.... connect to any other wifi network OR even amend any details of the remembered connection with my phone hotspot
*The message in the enquiry line appears on some occasions, so I am trying to find out a/ what that means and b/ how to fix it.

Specifics
*I can see other wifi networks, but if I select one then click "connect", the dialog box disappears and nothing happens
*If instead select the phone hotspot and click on the gearwheel, all controls are greyed out, so I cannot change anything, including that I cannot 'forget connection'.
*If I change the password on my hotspot and then try to connect the laptop, I do get an opportunity to enter the new password, but that doesn't actually change the network settings, and won't connect.
*If I then change my hotspot password back to original (ie matching that stored in the network settings) I can again connect.


So, something is preventing me changing anything at all about network settings, including accessing new wifi networks
Any thoughts?

I am a low level linux user so if you tell me terminal commands, I need to know exactly what to enter!  
TIA
Alexander

---

### Post by TheFu on 2021-05-24
[https://help.ubuntu.com/lts/ubuntu-help/net-wireless-connect.html.en](https://help.ubuntu.com/lts/ubuntu-help/net-wireless-connect.html.en) is all I found related to that.
If the phone appears as a wifi-hotspot, I don't think it matters, provided you know the correct WPA2 PSK.

On ubuntu server, there isn't a GUI to control this stuff and all network settings have to be handled through administrator commands.

---

### Post by alexanderedward2 on 2021-05-24
Hi, thanks for the response.
Yes, I know how to connect to a wifi, but there is a problem with connection process. It is something to do with me, the user, not having permission to change ANYTHING about any network setting. 

this is a laptop, running 20.02 so not related to Ubuntu Server.

---

