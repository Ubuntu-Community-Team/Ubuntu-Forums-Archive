---
title: "how do i know if i have a static address or dynamic.  isp people are useless"
date: 2018-07-02
forum: Networking &amp; Wireless
---

### Post by bodhin2 on 2018-07-02
aby clues?  i am getting a new wireless and i guess to set up security it is one of the questions>  i think i can try one setup and may if that doesn't work try to start from scrtcth again and try something else?  or maybe i can't?  haven't set up wirelss in years re: router.  but have done it on my laptops to get it connected to my airport.

---

### Post by TheFu on 2018-07-02
If the router you control doesn't have a specific netmask and specific IP entered into it, then you have a DHCP address.

BTW, I'm not certain I get the question correct due to abbreviations and/or spelling issues.

What do you mean by "wirelss", exactly?  LTE, 4G, WiFi, Wi-Max, Satellite or something else?

---

### Post by bodhin2 on 2018-07-02
aorry -crippling arthritis makes typing a nightmare.  wireless....

:-)

---

### Post by chili555 on 2018-07-03
The short answer is that unless you have taken specific steps to set up a static IP, then you have dynamic.

First, you will have an IP address from your internet service provider (ISP) that your router, modem, etc. gets from them. ISPs usually charge extra for static IP addresses as they are typically needed to run a server that is accessible from the outside world. Running a server means a lot more traffic for your ISP and they feel entitled to charge more to get more. If you didn't request and pay for a static IP from your ISP, then you don't have one. Your IP address that is visible to the world may change.

Second, you've mentioned that you use an Apple Airport. It is, in most respects, a wireless router. It will give devices that connect to it addresses in the range of 10.0.1.2 or similar. Unless you have gone to extraordinary steps to use a static IP address on your computer, say 10.0.1.150, then you don't have a static IP address; you have dynamic.

In most home computing situations, dynamic works perfectly well. Aside from setting a WPA2 password and a meaningful SSID, this should all be plug and play.

---

### Post by bodhin2 on 2018-07-03
Thanks chill, i thought it may be static.  i am not sure i need to  put int the ip addresses you mentioned.  I will have to try to figure that one out.  wireless router will be in this week i hope.  I used wep before but never setup the wpa2  i have to create ssid i take it - is the name of the wirless that appears - correct?  pw i get.  thanks so much - i wish i had it in front of me at the moment.

---

### Post by TheFu on 2018-07-03
The ISP would provide a form to you with the static IP and netmask if you paid for it.  If they didn't, then you don't have it.

You never answered what "wireless" means in your responses. In many parts of the world, wireless means a cellular internet connection because they don't run wired connections to homes.

---

### Post by chili555 on 2018-07-03
>  I used wep before but never setup the wpa2 i have to create ssid i take it - is the name of the wirless that appears - correct? You don't want WEP as it is insecure. The reasons that we have progressed to WPA and then WPA2 is that WEP is so easily cracked.

I suggest that you prefer WPA2-AES, sometimes referred to CCMP, and not WPA WPA2 mixed mode. I'd set a fixed channel, either 1, 6 or 11, and not auto channel select.

The SSID is indeed the name of the wireless that appears. I'd pick something that is recognizable to you and your family; how about bodhin2? Select a password that is not easily guessed; that is, not 12345678 or your house number, etc. Save the changes to the router, reboot it and you should be all set.

Then your Ubuntu computer should see the wireless router at the Network Manager icon at the upper right of the desktop; click on it, supply the password you selected and connect. Done!

Other devices, iPads, Chromebooks and even Windows computers (!!!) should be the same.>  i am not sure i need to put int the ip addresses you mentioned.Probably not.

Post back if we can help you more.

---

### Post by bodhin2 on 2018-07-03
Man thanks so much!  should be here thursday - late in the day probably.

it has this [COLOR=#505258][FONT=AktivGrotesk-Regular]WPA2,WPA-PSK/ WPA2-PSK encryption[/FONT][/COLOR]

hope this helps.

---

