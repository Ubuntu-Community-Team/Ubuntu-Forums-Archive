---
title: "Huawei e160 active but still no internet"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by lemontemayor on 2009-07-22
Installed remix 9.04 in my Dell mini and have a mobile broadband 3G usb modem. Ubuntu recognizes the modem and post it as active or connected but can't seem to have a real connection to the internet. The service provider was listed while configuring the connection so that made things easy at first. 
 
Perhaps it has to do with the SD capability of the usb? I searched for answers and couldn't find any convincing method. I browsed through usb_modeswitch option and seem to complex for my problem.
 
I thought of installing a preset solution from vodaphone in the UK and configure the appropriate parameters in accordance to my mobile service provider. This case involved once again installing usb modeswitch and a second program that would handle the connection.
 
After searching for almost all day for answers I become desperate and decided to ask for help.
 
Any suggestions would be greatly appreciated.

---

### Post by greenjumper on 2009-08-16
Similar problem here - any ideas?

---

### Post by hellomoto on 2009-08-16
ok, can u describe the problem a little better? is your modem recognised?

please open a terminal and post the output of the following command:
```
 lsusb 
```

If you modem is recognised and appears in network manager does it connect?

When you say you don't have proper internet, what do you mean exactly? Is it just slow?

If so try disabling IPv6 in firefox. In a browser window type: 
```

about:config 
```

in the filters box type "IPv6"
Double click "false" in the value to make it "True" to disable Ipv6. Can u now surf the net at faster speeds?

---

### Post by lemontemayor on 2009-08-17
The modem was being recognized.  I solved the problem updating the IP addresses for my carrier, TELCEL in Mexico.  The new IP addresses are 148.233.151.8, 148.233.151.6

Afterwards, the modem worked just fine.  The default addresses that came with the original configuration are no longer valid.  I had to update them.
 
Thanks

---

### Post by greenjumper on 2009-08-18
I also solved my problem, when I realised that I had mistyped the APN! What an idiot! :P

---

