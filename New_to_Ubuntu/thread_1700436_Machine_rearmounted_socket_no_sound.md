---
title: "Machine rearmounted socket no sound"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by WuLing on 2011-03-05
After I used ubuntu&#65292;my computer lead socket has no sound, but the rearmounted socket has sound
this is  the output of these terminal commands&#65306;
  
uname -a :
Linux wangxin-desktop 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux

aplay -l:
**** PLAYBACK &#30828;&#39636;&#35037;&#32622;&#28165;&#21934; ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  &#23376;&#35774;&#22791;: 0/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0


dpkg -l | grep "alsa":
ii  alsa-base                            1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-utils                           1.0.23-2ubuntu3.4                                 Utilities for configuring and using ALSA
ii  bluez-alsa                           4.69-0ubuntu2                                     Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.30-2                                         GStreamer plugin for ALSA


head -n 1 /proc/asound/card*/codec#* &#65306;
==> /proc/asound/card0/codec#2 <==
Codec: Realtek ALC883

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI





Can  some body help me?:confused:

---

