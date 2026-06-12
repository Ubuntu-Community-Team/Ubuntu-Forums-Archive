---
title: "Existing Wifi Connections Won't Go Away"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by erichnewell on 2008-01-10
I am running 7.10 on a Dell M65 with the restricted Broadcom 43xx firmware.

I have no issues using the wireless per-se. Once connected, it works flawlessly...but there has been a major change since Feisty:

I have networks that persistently show up in my "available networks list" that are simply NOT THERE and my main wifi network never appears in the list no matter how often I connect using the "Connect to Other Wireless Network".

"BadNetwork" is one I setup to test kismet and other wifi tools...it is *offline* and I've even run kismet just in case someone nearby had actually setup a similar router with the same name recently. All I can see is my laptop trying to beacon for the non-existent network...yet it still appears as an available network with 90% reception quality.

How do I make this go away? and why is it showing up in the first place?

On another note: my main wifi does not appear in my list where it used to under Feisty. I used to be prompted by the key manager for my password to enable the protected WPA encryption and away I'd go. Now I have to set it up manually every time.

I'm guessing that the nm-applet is simply not refreshing properly but do not know how to flush the cache or force a refresh manually.

---

