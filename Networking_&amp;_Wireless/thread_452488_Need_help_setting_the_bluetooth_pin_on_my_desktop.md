---
title: "Need help setting the bluetooth pin on my desktop"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by vees on 2007-05-23
Hi,

I have purchased a Cyber-Blue bluetooth 2.0 USB dongle and I am trying to pair my Nokia N800 Internet Tablet and my Nokia 6133 cellphone to my computer.  I have tried using bluetooth-gnome, kde-bluetooth, grml-btnet and I have tried to play around with hcid, hcid.conf, hcitool but I could not establish a connection.

I have to say that the computer "sees" the dongle very well, and the OS "sees" the N800 (a search on gnome's bluetooth manager finds the N800 but when I try to click on "properties" nothing happens). It looks to me that this is not a hardware issue.

On the N800 side I went to tools->control panel->bluetooth-devices-new where it 'found' my computer with no problems. I then tried to pair the devices and it gave me a passcode. I found no way of "seeing" that passcode request on my computer other than this message on the tail -f /var/log/syslog output:

```
hcid[4648]: pin_code_request (sba=00:15:83:BE:9E:F0, dba=00:19:4F:DB:1B:54)
```


However, I did not find how to answer this pin request to the connection was terminated with the message "pairing failed".

Which file should I edit to have my desktop respond to the authentification request with the correct pin number?

I tried playing around with /etc/bluetooth/pin and /usr/bin/pinwrapper and I did '/etc/init.d/bluez-utils restart' many times after that, but to no avail.

All I need is to set the pin on my desktop as, say, '1234' once and for all.  Which file should I edit and how?  Which service should I start?

Many thanks,

VS

PS: BTW - I can pair the two Nokia devices just fine.  Both of them ask for a pin number before connecting and both of them pop up a window asking for a pin to accept an incoming connection request.  All I do is enter 1234 and the devices are paired one and for all.

---

