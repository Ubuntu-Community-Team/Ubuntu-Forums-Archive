---
title: "How to set up 2wire 1701hg gateway modem into bridge mode?"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-07-21
First of all, I would like to know if it is even possible to use a 2wire 1701hg gateway modem for the following: I have wireless internet through another modem and I would like the 2wire modem to catch the wireless signal so I can access the internet with a desktop wired through ethernet with the 2wire modem.

I switched it into bridge mode but it didn't work. I had to reset it.

Does anyone know how to set it up this way, or a tutorial explaining how?

Thank you!

---

### Post by sylvainrb on 2009-07-21
so it seems that the 2wire 1701hg gateway cannot be used as a wireless bridge.

Does anyone know of a good but still cheap wireless bridge I could get that works with Ubuntu?

---

### Post by sylvainrb on 2009-07-21
I found an access point but it won't connect to the wireless network. The brand is an intellinet wireless LAN access point.

I was able to configure it into station-infrastructure mode and can see my wireless network, but the connection fails everytime?

I need help, thanks!

There are more options within the interface, but I'm not sure of how to configure those...

---

### Post by LookTJ on 2009-07-21
Usually with 2Wire(at least newer models I know this, not sure about the older models), you have to call the ISP to set it.

---

### Post by LookTJ on 2009-07-21
> **sylvainrb said:**
> so it seems that the 2wire 1701hg gateway cannot be used as a wireless bridge.

Does anyone know of a good but still cheap wireless bridge I could get that works with Ubuntu?
The 2Wire as far as I know cannot be used as a wireless bridge because the way the firmware was designed.

DD-WRT(firmware) provides this feature, you could buy a WRT54GL and flash it with DD-WRT

---

### Post by jtrammell on 2011-09-13
If your 2Wire is not listing a computer with a static IP address, or you would like the 2Wire to act as a bridged router, the 2Wire offer the technicians pages to change advanced settings:
 

 h t t p://{router ip}//tech/configuration.html
 

 This will bring you into the advanced configuration for the 2Wire.  If you have a server with a static IP, and the 2Wire does not have it listed, it will not forward network/internet traffic to that computer.  You can reset your local area network’s computer list.  This will force the 2Wire to start rebuilding the list again and re-detect your server.
 

 This this problem become common, consider placing the 2Wire into bridge mode and using your own router.  This will require a static IP.


Shawn Zernik

[http://www.internetworkconsulting.net]("http://www.internetworkconsulting.net/")

---

