---
title: "Wireless access has ceased to function"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by MikeMLP on 2007-05-24
I've had a stable 7.04 system up and running for a few weeks at home, using my wireless access point.  I recently upgraded both the router and access point firmware to the latest version, and directly afterwards my wireless under Ubuntu worked just fine.  The last update that I can remember getting through synaptic is a samba update sometime last week.

Regardless, now, when I boot into 7.04, the wireless connects just fine, but no data gets through.  All web pages on firefox display 'this page cannot be displayed.'  My weather applet won't download weather data as it normally does.  Yet I am connected.  The Network Manager applet says so.  When I log onto my access point (from my wired desktop machine, of course), the mac address of my laptop appears in the list of connected computers.  When I boot into windows, the wireless works fine.  The only think I can think of is that something in that samba update broke the wireless capability.  I don't know though... could this be a firewall issue?  I'm at a loss, and I'm starting to get tired of having to be in windows again too!

Thoughts?

edit:  I tried a 7.04 livecd and was unable to connect, despite the fact that I had a 7.04 installation that used to be able to connect just fine.  I am perplexed.

---

### Post by aakour on 2007-05-25
Same problem here. After last night's updates (samba and some other stuff), wireless stopped working. It can't connect to my WPA AP, and it connects to my unencrypted AP but no data goes through. I had the same behavior if I launched beryl-manager before nm-applet, but launching beryl after wireless was connected solved this issue. Now the problem is however back, and doesn't seem to have anything to do with Beryl this time.

---

### Post by MikeMLP on 2007-05-25
Have you tried connecting to your wireless using a 7.04 live cd?  I would think that the latest updates would not be rolled into the livecd - the livecds should have the April 19th 7.04 release on them, without any newer updates included.  Hence why I was really shocked when the LiveCD didn't allow me to connect to my wireless network.

---

### Post by whistlerspa on 2007-05-26
This may have nought to do with it but I found that I had a desktop that wouldn't wireless whereas my laptop would (both running Feisty).

I removed the cable from the LAN card to the router and then setup the wireless again. After reboot  it's been fine ever since and I've done a good few startups since then. 

I wonder whether there was some sort of conflict between wired and wireless connectivity causing this.

---

### Post by MikeMLP on 2007-05-27
I finally had a chance to connect my laptop via a wired connection today, and it worked just fine.  I downloaded some updates, including more samba updates via the wired connection.  I then restarted, pulling the plug, but wireless behavior was the same.  All network indicators say that I am connected; even signal strength is accurately shown, yet if I try to access a web page, or the routers, the connection fails.  If I try to ping the wireless access point, or the router, none of the pings are responded to.  I've double checked all filters and firewalls, but as expected, everything was just fine.  So, there is no change, and I still have no idea why this is happening.  Back to my Windows partition, sadly, where the wireless works fine.

Any other thoughts?

---

### Post by ryanVickers on 2007-05-27
Hmm, worldwide samba update crises :p

Possilby it has changed something though to make it "work" better, but it broke the connection.  Try reverting to the old setup if possible and just not letting it update anymore until you can find a fix.

---

