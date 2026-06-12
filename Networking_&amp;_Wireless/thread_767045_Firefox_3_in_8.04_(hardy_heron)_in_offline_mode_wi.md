---
title: "Firefox 3 in 8.04 (hardy heron) in offline mode with usb modem"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by timcredible on 2008-04-25
Ok, so I did some searches and found that firefox keeps starting in offline mode for me because I'm using a USB modem (verizon wireless broadband) and networkmanager doesn't recognize it.  So, what's the solution to fix this?  Can I disable networkmanager and will that fix it?  Is there any setting in firefox 3 that can disable it from checking with networkmanager? 

Thanks.

---

### Post by erginemr on 2008-04-27
I am also using a USB modem to connect to internet and this was also bothering me ater upgrading to Hardy and Firefox 3.

The solution I have found was disabling Network Applet fron System -> Pref. -> Sessions and adding the following lines to the file "/etc/network/interfaces":
```
auto eth0
iface eth0 inet dhcp
```

Thus, I guess, Firefox believes that eth0 (i.e. ethernet card) is active although it connects to Internet via ppp0 (i.e. USB modem).

---

### Post by timcredible on 2008-04-27
Thanks!  I'll try it Monday morning.

---

### Post by siabost on 2008-06-17
Hi,

Tried that suggested by erginemr and it worked - you can even re-enable the network applet although that seemed to make my meagre 667Mhz processor work harder.

Thanks

---

### Post by Nikitas350 on 2008-06-23
see this: [http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179)

---

### Post by khermans on 2008-07-10
Here is a fix I developed for the issue...

[http://kristian-hermansen.com/code/disable.offline.mode/disable.offline.mode.html]("http://kristian-hermansen.com/code/disable.offline.mode/disable.offline.mode.html")

---

### Post by COKEDUDE on 2008-08-15
> **khermans said:**
> Here is a fix I developed for the issue...

[http://kristian-hermansen.com/code/disable.offline.mode/disable.offline.mode.html]("http://kristian-hermansen.com/code/disable.offline.mode/disable.offline.mode.html")


Could you please fix your link? I would like to see it.

---

### Post by GeorgeVita on 2008-08-16
Hi,

I am using Ubuntu 8.04, with or without my 3G USB modem, no ethernet or WiFi connected and "Firefox 3" can start "online" or "offline" depending on the status of the 'network configuration' icon.

BEFORE managing this, I was trying to setup manually a "point to point connection", from "properties" I set gprs, enable this connection, and I wrote "internet" to Access Point Name. Then "ok" and "close". These parameters actually are not used, but maybe they setup some flags.

Then I had Firefox starting online or offline:
1. Right Click on the Network icon (up-right on the screen, beside the Volume Control).
2. If the "Enable Networking" is selected, Firefox 3 starts always in On-Line mode, otherwise it starts always in Offline mode.

Regards,
George

---

### Post by uberdonkey5 on 2008-09-25
> **erginemr said:**
> I am also using a USB modem to connect to internet and this was also bothering me ater upgrading to Hardy and Firefox 3.

The solution I have found was disabling Network Applet fron System -> Pref. -> Sessions and adding the following lines to the file "/etc/network/interfaces":
```
auto eth0
iface eth0 inet dhcp
```

Thus, I guess, Firefox believes that eth0 (i.e. ethernet card) is active although it connects to Internet via ppp0 (i.e. USB modem).

I was worried about getting rid of network manager because surely updates will just replace it? Also wasn't sure if I needed it to set up proxy. Nothing else here worked but the above solution was ideal and worked perfectly.

---

### Post by gnuchanux on 2008-11-26
I suggest just changing **browser.offline-apps.notify** to **false** in Firefox **about:config**. 

More about about:config > type about:config in URL bar & promise that you won't break Firefox :P . Type in the above line in filter & list will narrow down.

---

### Post by sanjrockz on 2009-04-05
I had the same problem and tried various options I could take by changing firefox configuration, which were available on the Internet. But finally I was able to solve it using the trick given [here]("http://ubuntuforums.org/showpost.php?p=5521752&postcount=24"). I think its the right way to tackle the issue as it is the fix proposed by the [MozillaZine]("http://kb.mozillazine.org/Knowledge_Base") community, which maintains a knowledge base containing documents written by Mozilla developers and users. 

Setting toolkit.networkmanager.disable to true makes Firefox to not to use NetworkManager capabilities at all, which omits the incapabilities of the NetworkManager on handling available networks. This makes firefox to operate at online mode all the time. You can read more about how toolkit.networkmanager.disable works [here]("http://kb.mozillazine.org/Toolkit.networkmanager.disable"). Thank you very much [igray78756]("http://ubuntuforums.org/member.php?u=68243") for [sharing]("http://ubuntuforums.org/showpost.php?p=5521752&postcount=24") this with us.

:guitar:

---

### Post by johny_mplayer on 2009-09-03
thank you _sanjrockz_.man i have ubuntu for 3 years now and i couldn't fix this.really thanks!!!!!!

---

