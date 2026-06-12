---
title: "Static IP Address Changes pppoe"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by WispFX on 2007-03-01
Greetings,

I'm trying to change my Static IP Address using "pppoe" and having trouble .. does anyone have some answers and directions to set me on the right path.

My Provider changed the Static IP Address to a new one and I need to know how to change it to the new address.

Thanks,
---WispFX

---

### Post by dieselpower on 2007-03-01
Where does pppoe get the address for ppp0? I have been helping wispfx and his provider changed his static ip because of a conflict, but ppp0 is still set to the old address and we can't figure out how to change it. Is it because his provider has not changed it yet, or is this something we need to configure?

Thanks,
Lawrence

---

### Post by zvacet on 2007-03-02
If you know new addres go to system>network setting,highlight your modem and click on properties.it will open window in witch you can see your static addres.Just type new one and close.If you used rp-pppoe to make connection you have to run rp-pppoe again and in some step ask you for your addres type new one.if you don´t know your new addres right click on panel>add to panel and choose network monitor under system&hardware.Once when icone is on the panel click on it and choose your type of connection.Go to support and you will see your new addres.Rest you know.

---

### Post by WispFX on 2007-03-03
Thanks for the help!  :)

---

### Post by dieselpower on 2007-03-03
We set up the connection by setting the speedstream modem to "bridge only" and used pppoeconf to set up the connection. As far as I remember, the router has no IP address, and pppoeconf never asks for one either, so I'm not sure where it gets the IP from, but I'll check the modem next chance I get.

Thanks!

---

### Post by WispFX on 2007-03-09
Forum Friends,

After several days of dealing with this issue .. and trying different things .. I decided to look at the Windstream DSL Modem firmware .. with my laptop (I had been trying to reconfigure things with my server PC.).  After looking at the firmware .. and not seeing anything relevant to my issue .. I went to the terminal and did an "ifconfig" and noticed that the pppo portion was showing the static IP address that Windstream had originally given me .. ending in 161.  As I considered this .. realizing that I had not tried to do anything to the Static IP address configuration with my laptop before this .. so it dawned on me that my problem might be with the Windstream people .. not with my system configuration or pppoe commands](*,) . 

So I called tech support.

Gave them my tele number for record reference and he gave me the 161 ending static IP.  I then explained that I had received an email from Windstream stating that they had to change my static IP to another one ending with 177 .. to which he acknowledged that he had some info there on that and that he needed to change it for me .. "They were just waiting on my phone call" ... and there was nothing in the email about calling tech support to get the changes made.  ](*,) 

So after all this hairpullin' an teethpickin' .. it was Windstream's fault that my new static IP was not showing up in the pppoe .. "ifconfig" command response.  A new "ifconfig" confirmed the new static address .. and I was able to then shift my powers of concentration and invention.

Hope this helps someone else.  Thanks to all those who took the time to read about my issue and tried to help.

---Merwin.
[www.WispFX.net](www.WispFX.net)

---

