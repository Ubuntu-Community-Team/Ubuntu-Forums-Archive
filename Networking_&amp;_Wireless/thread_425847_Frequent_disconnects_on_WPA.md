---
title: "Frequent disconnects on WPA"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by nythacker on 2007-04-28
I've freshly installed Dapper Drake and all current updates on my laptop and have correctly configured and connected my Linksys WPC54G v.1.2 laptop adapter to my D-Link WBR-2310 Wireless Router via WPA and Ndiswrapper. I could browse the internet, however, there are times when my wifi connection would randomly time-out or drop or disconnect and would have to reissue the following commands to reconnect to my AP again:

> sudo ifdown wlan0
sudo ifup wlan0

This is quite an inconvenience and would like a steady uninterrupted WPA wifi connection. Any solution to this random time-out/drop/disconnect problem?

Any help would be appreciated.

Thanks!

---

### Post by taz1234 on 2007-04-28
Here's a couple of things to consider:
1. are there many other wireless AP's in your local airwaves?  If so, try changing channels on your AP. If the strongest signals around you are using mostly odd numbered channels, ie. 11 - then select an even number for yours.
2. If the above doesn't work, (believe it or not) remove your AP's antenna and set the transmit power to the lowest setting.  You'll be surprized how far away from the AP you can still go and at the same time if this works, I'm willing to bet someone is trying to hack your AP.  I live in an appartment building with 20+ wireless signals going around.  People try to hack my AP's WPA by a method where they jam my signal and cause me to re-authenticate.  Removing your antenna will hopefully not make your network a strong target to where people may be doing this.  
3. Try (as a temporary experiment) 64 bit WEP instead of WPA.  My Mac's airport card sucks and can't hold a connection with stronger encryption for whatever the reason. (with my linksys AP)  If this works for you, I'm not sure what you can do to fix your connection when using WPA.  For me the answer was a $10 wireless usb adapter for my PPC Mac (running Ubuntu).
4. If all else fails, you may want to adjust the finer details of your AP's wireless transmission settings.  ie. MTU's and such.  The router often has online help built in that will tell you what each setting does.

Hope something above helps you out.
Jeff

---

### Post by nythacker on 2007-04-28
Thanks for the quick reply, Jeff. Unfortunately, I never had this kind of disconnection problems on my WPA network when I was with Edgy Eft using the very same equipment and configuration. Only when I freshly installed Dapper Drake and using the same exact WPA configuration which worked with Edgy Eft did I encounter this problem. I have two other wireless computers using Windows 2000 and configured to connect to my WPA router which virtually have no disconnection problems at all.

The same laptop where I installed Edgy Eft and later to Dapper Drake also is configured to dual-boot to Windows 2000 and I have virtually no disconnection/time-out problems at all using Windows 2000 connecting to my WPA network. So I guess it's just a Dapper WPA problem.

The main reason why I downgraded to Dapper Drake on my laptop is merely a personal choice because of its Long Term Support. So why did my WPA config work well with Edgy Eft and not with Dapper Drake?

My wpa_supplicant.conf file looks like this:

> 
network={
        ssid="NetworkEssid"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=945609a382413e64d57daef00eb5fab3ae228716e1e440981c004bc61dccc98c
  }


---

### Post by nythacker on 2007-04-28
**[COLOR="Red"]ERRATA:[/COLOR]** I have observed that my WPA problem is a [COLOR="Red"]time-out[/COLOR] problem as I am still connected to my router but can no longer browse the internet after some idle activity.

Need help badly.

Thanks!

---

### Post by nythacker on 2007-05-01
**[COLOR="Red"]UPDATE:[/COLOR]**

Okay, guys... I dunno what's going on here... :confused:   I can't explain it myself either but I've finally fixed my wifi WPA time-out problem on Dapper Drake.

[COLOR="Red"]**SOLUTION:** Do a fresh install of Dapper Drake![/COLOR]

Now, I'm still using the very same configuration and my old wpa_supplicant.conf that I posted above and am now experiencing a ROCK-SOLID WPA connection! No more time-outs/disconnect problems at all!

Pretty freaky, huh?!

Hope this helped some of you guys out...  =D>

---

