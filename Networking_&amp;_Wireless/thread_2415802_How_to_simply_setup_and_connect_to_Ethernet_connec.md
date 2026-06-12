---
title: "How to simply setup and connect to Ethernet connection please?"
date: 2019-04-01
forum: Networking &amp; Wireless
---

### Post by oldnub on 2019-04-01
Hi,

I've just installed Disco Dingo (dev branch) on an old laptop and would simply like to connect online (wired) with my provider login and password.
(In windows we setup a new connection and just enter username and password.)

Would you be kind enough to walk me through this in Ubuntu please?

The router/ethernet cable is connected and the router and laptops have been rebooted, etc. The router is working OK because my Windows PC is connected to this forum.

Thanks . (I look forward to using Ubuntu on this old but still OK laptop - to replace Windows 7.)

[COLOR=#a9a9a9](I see that ipconfig is not recognized anymore I believe in this build.)[/COLOR]

---

### Post by SeijiSensei on 2019-04-01
Usually you just plug in the cable, and Ubuntu takes care of the rest. Is there a specific problem you're having?

---

### Post by oldnub on 2019-04-01
[LEFT][COLOR=#222222][FONT=Verdana]Upon installing Ubuntu the network window shows Wired [Connected - 1000Mb/s  The green switch is on and there is the settings icon *][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]If I click that settings icon for Wired it opens the Wired connection profile window which includes the Details/Identity/IPv4/IPv6/Security tabs.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Am I (everyone) supposed to click on the security tab and then click on the greyed-out 802.1x Security button to turn it on? If so, what Authentication are we supposed to choose? (MD5/TLS/PWD/FAST/Tunneled TLS/Protected EAP (PEAP)) (I'm just using a standard broadband modem.)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Thanks for your advice.[/FONT][/COLOR][/LEFT]

---

### Post by webaake on 2019-04-02
"802.1x Security" is for wireless (wifi) only. You go by wired (ethernet cable with RJ45 plugs standard) you say, so it should work out of the box with a standard router.

That is to say, if your standard broadband modem is correctly connected and is set to share its connection to your other computers. If so it should give your computer an IP and share DNS-servers.

You could try and set your IP and DNS servers manually in the wired section (IPV4) of the Network Manager Settings.

---

### Post by chili555 on 2019-04-02
> "802.1x Security" is for wireless (wifi) only. That's incorrect. [https://en.wikipedia.org/wiki/IEEE_802.1X](https://en.wikipedia.org/wiki/IEEE_802.1X)

In Ubuntu, select Settings > Network > Wired and click the gear icon. One of the available tabs is Security. Set your properties there.

[IMG]https://i.postimg.cc/bwzBQLpH/Screenshot-from-2019-04-02-09-42-14.png[/IMG]

---

### Post by webaake on 2019-04-02
I stand corrected. I've never used for standard wired, so there you go.

---

### Post by SeijiSensei on 2019-04-02
Needing to authenticate for Ethernet is pretty uncommon, though, no?  Most consumer routers only expect authentication for wireless connections.

---

### Post by ubontik22 on 2019-04-05
Hi,  I want to connect 2 Ubuntu (18.04) machines. They ping to each other but I can't connect them.  Thanks

---

### Post by chili555 on 2019-04-06
> **ubontik22 said:**
> Hi,  I want to connect 2 Ubuntu (18.04) machines. They ping to each other but I can't connect them.  ThanksPlease start your own new question. Thanks.

---

