---
title: "Recording Live Streaming Audio in RealPlayer"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by lhb1142 on 2009-09-21
:confused:  I have never figured out how to record RealPlayer live streaming audio, specifically the Metropolitan Opera broadcasts from their site which uses RealPlayer.

Can anyone help me with specific directions? Thanks in advance for any help.

(I am using Ubuntu v. 9.04)

---

### Post by mikewhatever on 2009-09-25
I suppose you could use Audacity or gnome-sound-recorder.

---

### Post by niteshifter on 2009-09-25
Hi,

I use mplayer to do this.
```
mplayer -bandwidth 2000000 -cache 3000 *rtsp://somesite.com/somestream.rm* -ao pcm:waveheader -vc null -vo null

```
The above gets a RealPlayer stream at high speed - faster than just listening to it - and writes to a file, audiodump.wav (mplayer default name).

```
lame -h -b 128 audiodump.wav *somefile.mp3*
```
The above converts the captured stream .wav file to an .mp3 file. Then delete audiodump.wav
```
rm audiodump.wav
```

The part above in italics you need to supply. The first one (rtsp://....) may take some digging into a web page to find out.

Edit: Upon re-reading I may have mis-interpreted "live". If the stream really is 'real-time' live we need to change the way mplayer is invoked:
```
mplayer *rtsp://somesite.com/somestream.rm* -ao pcm:waveheader -vc null -vo null

```
The -bandwidth and -cache settings are only useful on pre-recorded streams.

---

