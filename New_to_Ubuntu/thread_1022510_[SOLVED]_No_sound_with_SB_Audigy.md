---
title: "[SOLVED] No sound with SB Audigy"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by GMod on 2008-12-26
my on-board audio quit so I installed a SB Audigy sound card. Ubuntu found the new card and I can control the volume on the card but I still have no audio. Another thread requested the output of aplay -l... here it is

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
... any help is greatly appreciated... Thanks

---

### Post by rbringh on 2008-12-26
I had a similar problem. I had to disable the onboard audio card via a BIOS modification. Unbuntu was picking up both cards and using the defective onboard card. It is possible to disable cards from Ubuntu, a search on the forum may help you find info on this.

I know this is not much info but the card does work in Ubuntu.

---

### Post by GMod on 2008-12-26
Thanks for the info. on-board audio already disabled in bios. Unchecked the audigy Analog/ Digital output jack box and behold the wife screamin' to turn that S^&T down!!!

---

