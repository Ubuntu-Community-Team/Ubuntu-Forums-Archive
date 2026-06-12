---
title: "Creative Sound Blaster 5.1 help"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Tejus on 2009-11-21
I have a Creative Sound Blaster 5.1 PCI audio card along with a set of 5.1 surround Creative speakers (Inspire M5300). They were properly configured in WinXP with the bundled software from Creative. In Ubuntu they output sound, but with problems.

I tried to configure the sound preferences, but every time I change something the computer and the sound starts to lag and doesn't stop till I close whichever player I'm using (Generally VLC or Songbird).

If I go to the hardware tab and select what I assume is my creative sound card (labelled as "[SB Live! Value] EMU10k1X") and change it to an "analog stereo duplex", it works fine. But if I select "analog surround 5.1 output + analog stereo input", high frequency noise is added to whatever song is playing and changing the settings under the output tab (like balance or fade) leads to deafening fluctuations in the output along with system lagging.

Any suggestions as to what the settings should be for my setup?

---

### Post by Tejus on 2009-12-02
All right...fixed it myself.

I went to the Ubuntu software center and installed PulseAudio Preferences. Then configured the card from System>Preferences>PulseAudio Preferences.

---

