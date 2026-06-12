---
title: "MSI P55-GD65 Realtek ALC889 Speakers don't mute when headphones inserted"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Natzapo on 2011-02-04
Hi guys, I've been trying to figure this out for a bit now, have searched the forums, checked google and looked into a few other forums as well.

The issue I'm having is that on my desktop I just installed ubuntu 10.10 and, while my sound works correctly otherwise, when I plug in headphones I simply get audio through both my headphones and the speakers.

Things I have tried:

1) In [this thread]("http://ubuntuforums.org/showthread.php?t=1598229&highlight=headphone+speaker+10.10") I did run the script, my results are [here]("http://www.alsa-project.org/db/?f=a12fee40b3cd3a2206d80223edc8b5fe989d60fe").

2) I tried editing my /etc/modprobe.d/alsa-base.conf file using the command gksu gedit /etc/modprobe.d/alsa-base.conf and adding a line at the end as suggested in that forum and in other places. Some of the options I tried were:

3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  auto
3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O

3) I tried installing the gnome alsa mixer, using the terminal mixer, the sound preferences etc to make sure I wasn't on an incorrect sound device, that I had my channels setup correctly (so far as I can tell) and all of that.

4) I followed [this]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=ALC889") to try upgrading my ALSA install, no dice.

5) I checked MSI's website to see if there were linux drivers/software for this model/series of MB, nothing.

6) I checked Realtek's website to see if there's an audio driver for the ALC889, there was, followed the instructions to install it. No joy.

Computer information:
MB: MSI P55-GD65
Proc: intel i5 750 @ 3.0ghz
ram: 6GB DDR3
VC: 2- 9800Gt w/1GB in SLI

Let me know if there's anymore information that I need to provide or if there's something I've missed here.

Thanks in advance for any and all help!

---

