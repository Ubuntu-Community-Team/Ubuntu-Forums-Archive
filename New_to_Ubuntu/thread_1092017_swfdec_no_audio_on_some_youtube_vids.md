---
title: "swfdec no audio on some youtube vids"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-03-09
i have a power pc running ubuntu so i had to install either swfdec or gnash im using swfdec as my flash player and i can watch youtube videos but i get no audio , i started firefox in the terminal and the output when playing a youtube vid is: ERROR: swfdec_audio_decoder.c(203): swfdec_audio_decoder_errorv: error decoding audio: no suitable decoder for audio codec 10  i have installed gstreamer0.10-plugins however i still get no audio except for on very few videos , 1 so far and i still get the error:  ERROR: swfdec_audio_decoder.c(203): swfdec_audio_decoder_errorv: error decoding audio: no suitable decoder for audio codec 10  

is there something else i need to do after installing the audio codecs or are there any fixes?

---

### Post by powerofsole on 2009-03-10
my problem got even more serious. after realising that the SWFdec pluginube 
caused firefox to crash on ever single page requiring flash (youtube and pandora) among others, I decided to remove it. Only to find that on my Ubuntu 8.1 version I couldnt remove it using any means. I tried disabling it thru firefox, removing it using software synaptics......just couldnt do it.
Even manaully removing the file is not possible after finding it.

I was forced to reinstall the OS
AVOID SWFDEC ! it shouldn't even be offered on the standard plugins list. This software needs a LOT of developing ... it's not safe for use yet

---

### Post by flugh on 2009-03-22
Running Intrepid/8.10, Firefox freezing every single time I try to watch a Youtube video. Enabling javascript globally via Noscript was no fix.

I removed all flash plugin related packages, including the Adobe stuff, gnash, and swfdec. Then I installed the 'adobe-flashplayer' package, and all is now working.

In my experience (not backed up by code, debugging, or anything concrete) is that the problem lies with swfdec (although not to the extent of the previous poster, mine uninstalled easily via apt-get remove).

---

