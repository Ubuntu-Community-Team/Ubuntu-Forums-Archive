---
title: "WiFi randomly disconnects and sometimes fail to authenticate again"
date: 2017-07-31
forum: Networking &amp; Wireless
---

### Post by slowerphoton on 2017-07-31
I am using Xenial - Ubuntu.


This is the outcome of `dmesg`:


    [ 2195.776888] wlp2s0: deauthenticating from 94:0c:6d:b7:b2:de by local choice (Reason: 3=DEAUTH_LEAVING)
    [ 2218.981806] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
    [ 2219.032521] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
    [ 2225.238469] wlp2s0: authenticate with xxxxxxxxxxxx
    [ 2225.246594] wlp2s0: send auth to xxxxxxxxxxxx (try 1/3)


It deauthenticates randomly for no apparent reason and I have to turn networking off and on again to fix it. This works a few times, but eventually I will lose the connection completely (it will always get to try 3/3 and fail it). The only thing of help I've found is rebooting.


[Here I've run the script AskUbuntu suggests to diagnose the networking.]("https://pastebin.com/raw/F9RzLWvc")


The script is not from the time of the complete failure - otherwise I would not be able to post here.

---

### Post by BenginM on 2017-07-31
Hiya,

from dmesg output, the deauthentications are for reason 3,  which means "Deauthenticated because sending station is leaving (or has  left) IBSS or ESS". This reason is common. largely from local STA choice  (which can be for number of reasons: low signal, can't get IP address  ..

```

rtl8821ae 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use

```

you  may want to set security encryption mode to WPA2 /AES only , in the  main router , and the channel mode to a fixed channel , 1,6,9,11 are  preferred . in terminal use:

$ nmcli dev wifi list 

you also might have to set power save off on the card , and or use the fwlps=0 kernel option

$ modinfo rtl8821ae

it's a good idea to see the kern.log to make sure it's not a hardware faults ..

sudo cat /var/log/kern.log | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)

---

### Post by slowerphoton on 2017-07-31
I forgot to mention that no other devices have networking problems. I also have Windows on the same laptop and the WiFi connection in there works compeltely fine. Sorry for that.

---

### Post by johndough2 on 2017-07-31
Hi

It seems that it is an error with IPv6, but the rest of your system seems to be IPv4.

So do you need 6?  Can you disable it?

You  are using WEP rather than PSK?  Could you be hi-jacked and some one stealing your bandwidth?

Your signal is not the strongest and could be getting swamped, re-site your router?

WiFi9988 is stronger and on channel 6, same as you.

---

### Post by slowerphoton on 2017-07-31
I disabled IPv6, problem persists. 

Maybe it would be stronger, but that definitely isn't an issue. I also have Windows on this laptop and I never have any WiFi problems there.

---

### Post by jeremy31 on 2017-08-01
You should try installing the module from [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) after disabling Secure Boot if it is an UEFI install

---

### Post by slowerphoton on 2017-08-02
I am sorry but I can't see how to install it. I cloned the repository, found a Makefile so I typed 'make' into the terminal window, but that didn't install it I think.

---

