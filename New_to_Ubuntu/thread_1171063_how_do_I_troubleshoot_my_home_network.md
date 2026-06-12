---
title: "how do I troubleshoot my home network?"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by jon.reeve on 2009-05-27
Hi everyone! I've been having problems with my home network recently. Sometimes the connection gets really, really slow. Other times the connection drops entirely. I figure this could be a problem with (1) My wireless card or the driver (2) the router, (3) someone else on my network or (4) the ISP. I checked my log files, and don't see anything telling there, so I figure it's not a problem with the card, but with something else with the network. Are there any ubuntu tools I can use to troubleshoot my network, or figure out what's making it slow?

---

### Post by shifty_powers on 2009-05-27
do you have only one pc? might sound silly, but the easiest way to check is just to use another pc on your network. You'll soon find out if it is your pc or the network...

---

### Post by jon.reeve on 2009-05-27
My housemates have reported similar issues, so I think it's a problem with the network or the ISP. Is there a way to monitor the network traffic?

---

### Post by shifty_powers on 2009-05-27
you have a simple network monitor in your system monitor, go system>admin>system monitor.

also, if you have access to another router, try swapping it over. it sounds like the problem is with the network or isp, and in my experience it is easier to diagnose the fault this way than faffing around in software.

otherwise dig into synaptic and search for a network monitor. i'm sure some will be in there...

---

### Post by lisati on 2009-05-27
I notice that my internet speed varies, even when there's only one machine using it. I've even known it to be affected by the weather - rain water got into the phone cables along the street one year, which did wonders for my phone connection and my internet.

As for who uses your home network, you should be able to control (or at least monitor) who accesses it. I use a combination of WPA-based encryption and permissions based on MAC address on the wireless portion, and Mrs Lisati & I are the only ones who have physical access to the ethernet connections. One of my routers (one by Netgear) also has an option on it's browser-based control panel to show which machines are connected.

If you want to monitor traffic using your Ubuntu box, your options include a program called Wireshark.

---

### Post by anewguy on 2009-05-27
And depending on if you live in an apartment......I've had my wireless get screwed up by the neighbors phone - operates on the same frequency as my router (2.4ghz?). 

I also have noticed a difference with weather, etc..  I'm only about 30 feet away from the router, with a hallway and a couple of walls there so it's not just line of site.

I've also seen things for certain types of wireless connections where they have to specify the speed in the config file.  I don't think this would affect speed downgrades, though.

Make sure you're using MAC filtering at the router and if possible also hide the ESSID from the router.  If someone else gets on your router it can downgrade your performance.

Dave :)

---

### Post by lisati on 2009-05-27
> **anewguy said:**
> And depending on if you live in an apartment......I've had my wireless get screwed up by the neighbors phone - operates on the same frequency as my router (2.4ghz?). 

That reminds me: I once had troubles with my home network, and as part of the troubleshooting I discovered that one of my neighbours sometimes has a wireless network running that uses the same channel as the one I was using at the time.

---

