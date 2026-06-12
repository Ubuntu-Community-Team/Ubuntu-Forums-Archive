---
title: "Buetooth speakers sound bad- better alsa drivers?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Doublehelix22 on 2010-07-19
Have had a quick search and there are so many topics around this that after a few reads my head caves in- sorry if it's been asked before

I just bought a beautiful bluetooth speaker. Makes pretty good sound from my Nokia N95 phone using bluetooth and likewise makes beautiful sound when cabled to my Lucid laptop

But the sound coming out of them from my laptop { Lenovo Thinkpad T410 ) using bluetooth is execrable, even to my cloth ears. Like cheap tinny radio

Am figuring it's the bluetooth-alsa driver? I read somewhere the default driver in Lucid is for lower quality reproduction, but I'm pretty new to this and would welcome other ideas

When I  type in 

dpkg -l | grep "alsa"

I get:

ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

if I need to install another package should I uninstall bluez-alsa first? 

Thanks!

---

### Post by Doublehelix22 on 2010-07-20
[FONT=Arial Narrow][SIZE=3][COLOR=Blue]I've gotten better quality ( but not as good as I get from my phone tether ) from these speakers using GAMaus suggestions at

[http://ubuntuforums.org/showthread.php?t=1152229&page=7](http://ubuntuforums.org/showthread.php?t=1152229&page=7)

Then I went to Banshee and faffed about with equalizer settings, created my own settings for the speaker profile

Sound is waaaaay better now. Not fantastic. Not as good as I get from my bluetooth/phone/speaker connection, but liveable[/COLOR][/SIZE][/FONT]

---

