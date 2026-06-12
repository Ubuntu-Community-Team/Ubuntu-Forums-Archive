---
title: "Cant get any tuners working."
date: 2009-11-13
forum: New to Ubuntu
---

### Post by LostMagix on 2009-11-13
Upgraded to 9.10 and I cant get any guitar tuners working


my line-in has sound, but i can't seem to get any of the tuners to read it..



fmit was the one i used in 8.04, here is the output from the terminal


```
:~$ fmit
Free Music Instrument Tuner version 0.97.7 built at Jan 19 2008 14:48:24
Install directory '/usr'
CaptureThread: INFO: Built in transports
CaptureThread: INFO:	N/A	JACK	Jack Audio Connection Kit
CaptureThread: INFO:	OK	ALSA	Advanced Linux Sound Architecture (lib:1.0.20)
CaptureThread: INFO:	OK	OSS	Open Sound System (lib:30802)
CaptureThread: INFO: Auto detecting a working transport ... using ALSA
CaptureThread: INFO: using ALSA transport
CombedFT: INFO: window size=400 FFT size=512 window size factor=1 zero padding factor=1
CombedFT: INFO: window size=1603 FFT size=2048 window size factor=4 zero padding factor=1
CaptureThread: INFO: ALSA: try to set format to Signed 16 bit Little Endian success
CaptureThread: WARNING: ALSA: cannot set channel count to one (2 instead)
CaptureThread: INFO: format is signed integer 16bits with 2 channel(s)
CombedFT: INFO: window size=1603 FFT size=2048 window size factor=4 zero padding factor=1
CaptureThread: WARNING: ALSA: Broken pipe
```


fmit is not seen in jack connections

---

