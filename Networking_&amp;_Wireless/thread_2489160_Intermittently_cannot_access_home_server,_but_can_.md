---
title: "Intermittently cannot access home server, but can ping it successfully"
date: 2023-07-20
forum: Networking &amp; Wireless
---

### Post by Paul_Hey on 2023-07-20
I have a server which runs jellyfin and Tvheadend.  I recently realised that it was still running 16.04 lts.  Via multiple upgrades I'm now back to 22.04 lts, and to my surprise, everything appeared to work, except that  no DNS address assigned. I sorted this, and all appeared to be well.  All updates and upgrades applied.

As the server can go days without being used, it runs a wake-up script whereby after a given amount of time idling, it shuts down after checking for any upcoming recordings, which are written to the bios if required in order to wake up.

Other than that, it gets a wol packet from whichever Kodi client is used.

I'm now having to regularly reboot manually, due to the server being on, but unreachable by SSH, samba or any of the other services running.  I am however able to ping it successfully.  I'm sure a full fresh rebuild is what it really needs, but I'd really like to be able to sort it without resorting to that.

I don't really know where to go from here, or what I should be looking at in terms of logs to diagnose what's happening.

---

### Post by TheFu on 2023-07-20
Yep, many subsystems have changed since 2016, so your server is full of conflicting subsystems.  The only fix I know is a fresh install.

If you use Jellyfin, why do you need tvheadend?  Jellyfin works with TV tuners from HDHomerun natively.

---

### Post by Paul_Hey on 2023-07-21
Okay, I think a clean install is on the cards in that case.

I use jellyfin because emby moved away from open source.  At the time of building the server, my choices were MythTV and Tvheadend.  I'd used Myth previously, and found Tvheadend so much easier to configure.

I use 2 x USB DVBT2 receivers, so I shall investigate whether I can do everything using jellyfin.  Thanks for your help.

---

### Post by TheFu on 2023-07-21
Other tuners that aren't Silcon Dust don't' work to my knowledge.

I've been running Jellyfin for about 2 yrs. Moved from Plex (anti-privacy) and Kodi before that.  If you have a DLNA-capable Silicon Dust tuner, then Jellyfin will work with it. No drivers to install.  Considering that "recording" a show is just downloading a file (you can use wget/curl) and saving it, the lack of drivers makes perfect sense.

Older HDHR tuners may require drivers or may not work.  IDK.  I gave away my older HDHR2 tuners and only have a Quad and an HDHR4 tuner now. Both "just work", though the quad doesn't have the same signal capture ability as the dual tuner model, which seems to get more, better, reception with OTA broadcasts here.  I have some stations that are too strong and many that are too week, so, I've had to setup one tuner with an amplifier and attenuators (need a slight amount of amplification) and the other without to get all the reasonable stations.

Silicon Dust makes really good network tuners. Any device on your network can use them. Plus, ethernet cables run 500ft without any issue, so placing a tuner a few feet from the antenna, then running ethernet from that point into your network switch really reduces COAX signal losses.  I don't know how satellite works. Never used it.

---

### Post by Paul_Hey on 2023-07-21
I looked into the silicon dust network tuners at the time of building my server.  As it was little more than a side hobby, I couldn't really justify the cost.

The USB tuners I have are robust and reliable.  I've found a guide for using them with jellyfin, but it still utilises Tvheadend to handle the tuner, then send it on to jellyfin via a URL, so this is another option.  

Having just looked at the cost of the silicon dust devices again, I think I'll stick with USB for now, and just keep an eye open for a second hand unit.  It would certainly make setup easier, and a more elegant solution overall.

---

### Post by TheFu on 2023-07-21
Right now is **_NOT_** a good time to buy new tuners around here.  We've been on the edge of new TV encoding standards, so all new tuners will be required.  Everything TV related seems to take 15 yrs longer.  They are chicken/egg problems.  Without the new tuners, nobody can see channels broadcast using the new standards.  Without any broadcast, nobody it interested in buying new tuners, especially since the govt is allowing encryption and DRM in the new standards to be enabled. There's consumer feedback against this going to the govt agency now, but the TV broadcasters and content creators have $billions to throw at lobbyists to get their way.
[https://youtu.be/fUyBpLf-m1s](https://youtu.be/fUyBpLf-m1s) is Antenna Man explaining the problem.  Hopefully, you live where this doesn't matter.

HDHR tuners are premium for good reason.  OTOH, I screwed around with TVHeadend and found it overly complicated.  For about a year, I used a little 'wget' script with 'timeout' and 'at' to schedule my recordings each week.

Also have a USB tuner too. Attempted to get it working with MythTV, but it was just too complicated.  There was 1 program it worked with using V4L2 drivers, but that was years ago.  The wget script was 1000x easier.

---

### Post by Paul_Hey on 2023-07-21
I chose very carefully when I purchased my DVBT2 usb tuners.  There was only one chipset which played nicely with Linux at the time, and the branding/naming of the devices was very confusing.  All I have to remember with a new install is to place a couple of firmware files in the right place.  That was the case a few years ago anyway.

I eventually gave up with MythTV, but I think my main problem was actually with my antenna.  Compared to MythTV I actually find Tvheadend a breeze to set up.  

Here in the UK, the last big change was a clearance of certain frequencies for 5g, so as far as I know I'm safe for the time being.

---

