---
title: "vlc problem"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by awsomehighvoltage on 2009-06-18
ive tried to convert videos with vlc to rockbox for ipod video but the output file has no audio. heres what i did: 
```
$ vlc /media/Videos/The_WTF_Blanket__Snuggie_Parody_.flv --sout="#transcode{vcodec=mp2v,vb=600,width=320,height=<240,acodec=mp3,ab=128,samplerate=44100,audio-sync}:std{access=file,mux=ps,url=wtf.mpg}"
```and heres what i got:
```
VLC media player 0.8.6e Janus
Gtk-Message: Using Global Menu
[00000302] mux_ps private: Open
[00000400] ffmpeg encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000295] stream_out_transcode private error: cannot find encoder ((null))
[00000295] stream_out_transcode private error: cannot create audio chain
[00000398] main packetizer error: cannot create packetizer output (mp3 )
[00000302] mux_ps private: Close
[00000283] main playlist: nothing to play
[00000283] main playlist: stopping playback
```could someone help? thanks in advance!

---

### Post by Michael.Godawski on 2009-06-18
hi,

do you have installed the **ffmpeg** package?

---

### Post by awsomehighvoltage on 2009-06-18
> **Michael.Godawski said:**
> hi,

do you have installed the **ffmpeg** package?

yes

---

