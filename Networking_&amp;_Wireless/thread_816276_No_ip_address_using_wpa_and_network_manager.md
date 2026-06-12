---
title: "No ip address using wpa and network manager"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by dsluser on 2008-06-02
Hi all,

Stupid question - how do I enable DHCP with WPA wireless?

I've installed a Belkin f5d7051 using the excellent instructions at [https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54GS_v1_&_v2?highlight=%28f5d7051%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54GS_v1_&_v2?highlight=%28f5d7051%29)

My next problem was connecting with WPA. I attempted to follow a lot of instructions using wpa supplicant but my /etc/network/interfaces file currently just has the loopback adapter autoconfig in it and if I add in anything to do with wlan0 I lose the option to connect to my network.

If i use wpa_passphrase and parse my ascii to hex I can connect to my network using network manager but all my settings(ip address, dhcp, dns, subnet etc.) show as 0.0.0.0 which is why I think it's a simple case of enabling dhcp in ubuntu but I don't know how. I'm coming from windows and just learning this as I go

Can anyone help me out with this? Cheers.

---

### Post by jeffus_il on 2008-06-02
I don't know if this solves your problem but at a quick look it seems very relevant:
[http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/](http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/)

---

### Post by dsluser on 2008-06-02
Thanks a million for the quick response :)

Would I need to undo everything I did from the other post before attempting this? As I said I'm pretty new to ubuntu so I wouldn't know how to reverse a lot of it. 

Would you recommend formatting and starting from scratch with the link you posted or should I be alright to give it a shot on the current system?

---

### Post by jeffus_il on 2008-06-02
No don't start from scratch or reformat, that would be an overkill, I would have a look at the instructions and see where it differs from what you have done, and maybe try adding those steps.

Can you experiment without wpa just to make sure that the wpa setup is what is causing you the problem?

There is also WEP which is easier to set up, but is less secure, which is not necessarily a problem if you live in a low density area where it is unlikely that someone with a wireless card would be lurking closer than about 100 metres.

---

### Post by dsluser on 2008-06-03
Ok I'll try when I get home from work and post the results.

I would much prefer WPA as I'm in a city and there's quite a few backtrack users dotted around the place :) I have a router set up on WEP for practicing security auditing so it'll be no problem to test it out. I just automatically assumed it would work with WEP since I can see the ssid and I do send packets when trying to authenticate.

Should have an update by about 8.30pm GMT. Again thanks for taking the time to help

---

