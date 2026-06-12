---
title: "Internal mic does not work - Sony Vaio VGN-CS215J"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by MockY on 2009-01-18
The sound on this machine works just fine. However, the internal mic does not. After alot of tinkering, I got the external mic (used when you plug in a headset or a mic) to barely work. I can hear myself but very low. But without the internal mic, this laptop is useless in Ubuntu since Skype is the most frequent used software.

I have tried with replacing Pulseaudio with Esound, but the same issue is still present.

Since this is my wifes computer, I now almost regret that I introduced Ubuntu to her. She is now used to it and have no desire what so ever to go back to XP, which has somewhat killed the excitement about a new laptop for her. So I'm feeling kind of desperate. It's too bad that such a simple thing doesn't work. It sounds like such a trivial thing, especially when everything else works out of the box.

cat /proc/asound/card0/codec#* | grep Codec gives me:
```

Codec: Realtek ALC262
Codec: Conexant ID 2c06

```
and aplay -l gives me:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Could someone please help me.

---

### Post by stderr on 2009-01-18
Silly question, but best to rule it out first:

Have you adjusted audio levels on the mixers to unmuted & full? e.g. System->Prefs->Volume Control

---

### Post by MockY on 2009-01-18
yup. All options are unmuted and turned up to max. Still no go. I booted up in openSuSE as well, and the same issue there. Everything works like it should but not the internal mic.

---

### Post by empty_spaces on 2009-01-18
also, type alsamixer in the terminal and make sure that all the sound levels are unmuted and the levels are raised.

---

### Post by linux_tech on 2009-01-18
Open volume control and check all settings as described here:
[http://ubuntufs.wordpress.com/2006/06/08/trouble-with-your-microphone/](http://ubuntufs.wordpress.com/2006/06/08/trouble-with-your-microphone/)

Let me know if there are any issues
__________________

---

### Post by MockY on 2009-01-18
> **linux_tech said:**
> Open volume control and check all settings as described here:
[http://ubuntufs.wordpress.com/2006/0...ur-microphone/](http://ubuntufs.wordpress.com/2006/0...ur-microphone/)


Error 404 - Not Found


I'm reinstalling Ubuntu again, just to get a fresh start and I'll resume from there.

---

### Post by linux_tech on 2009-01-18
oops!corrected url

---

### Post by linux_tech on 2009-01-18
There is no need to re-install ubuntu to go back to original,
you can instead just re-install alsa. I'd be happy to help you if you want, then work on the skype issue with you

---

### Post by nlz on 2009-01-18
did you already added 'vaio-options'?

---

### Post by MockY on 2009-01-18
> There is no need to re-install ubuntu to go back to original

I did anyways because I had tinkered with the system so much that I completely forgot what I had done prior. So now I'm on a fresh install again.

What makes things a little bit harder is the fact that the regular mic works. I can plug in a microphone and it works (though not perfect but good enough) and record myself and it works in Skype. But the internal microphone does not seem to even function a little bit, regardless of what I do.

> did you already added 'vaio-options'
No, I never tried that one. Will do when I get to that point again.

---

### Post by Big Russ on 2009-01-19
If you don't mind me jumping in here.... where do you find "Vaio options"? ... thinking this may help solve a few of my probs

---

### Post by MockY on 2009-01-19
> **Big Russ said:**
> If you don't mind me jumping in here.... where do you find "Vaio options"? ... thinking this may help solve a few of my probs

Add the following line on the bottom of /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=vaio-options
```
save and restart.

---

### Post by Tritonio on 2009-03-10
> **MockY said:**
> Add the following line on the bottom of /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=vaio-options
```
save and restart.

I believe that the correct line is:
```
options snd-hda-intel model=vaio
```

I tried both and the best I got was some more controls but I still cannot use the built-in mic. In Hardy everything worked OK by adding this line. :-| Well, maybe it's just me doing something silly. I will repost if I manage to get everything working.

@OP: The mic not working is probably not the only out-of-the-box problem. Try pluging in a headset and the sound will still come out of the build in speakers.

---

### Post by Alfons81 on 2009-08-14
I found a tread that, finally, is making works the internal mic on my VGN-AR88L!!!

I was trying to fix that in such of different ways...and now only with two commands on my terminal is working:

$ amixer contents  (it lists were is your internal mic and if it is on/off)

and to switch it on:

$ amixer cset numid=5,iface=MIXER,name='Capture Source' 1

$ amixer cset numid=4,iface=MIXER,name='Capture Switch' on

Of course the microphone volume have to be not muted. 

The solution is here:

[http://unknown.dizzy.ro/wiki/Sony_Vaio_VGN-AR41E](http://unknown.dizzy.ro/wiki/Sony_Vaio_VGN-AR41E)

this tutorial is written for a Gentoo Linux installation and also it talks about how-to fix Fn-keys. But I didn't tried it yet because I'm totally flabergasted with my mic working...And now I've a 99% working system with Ubuntu 9.04.:guitar:

Hope it works for everybody, enjoy!

---

### Post by champaign on 2009-08-22
Hi,
So i tried out what you did but I didn't see 'capture source' under the content. My VAIO model is VGN-SR490 and my built-in mic is working perfectly in windows. Here's a screen shot of the amixer content:

weewenleow@VAIO:~$ amixer contents
numid=2,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=1,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=30,step=0
  : values=20,20
  | dBscale-min=-45.00dB,step=1.50dB,mute=0
numid=16,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=255,255
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
numid=4,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=3,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=24,24
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=8,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=10,iface=MIXER,name='Capture Switch',index=1
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=12,iface=MIXER,name='Capture Switch',index=2
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=7,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-12.00dB,step=1.50dB,mute=0
numid=9,iface=MIXER,name='Capture Volume',index=1
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-12.00dB,step=1.50dB,mute=0
numid=11,iface=MIXER,name='Capture Volume',index=2
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-12.00dB,step=1.50dB,mute=0
numid=6,iface=MIXER,name='ATAPI Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=5,iface=MIXER,name='ATAPI Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=25,25
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=17,iface=MIXER,name='Digital Capture Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=120,step=0
  : values=120,120
  | dBscale-min=-30.00dB,step=0.50dB,mute=0
numid=13,iface=MIXER,name='Input Source'
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'CD'
  : values=1
numid=14,iface=MIXER,name='Input Source',index=1
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'CD'
  : values=1
numid=15,iface=MIXER,name='Input Source',index=2
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'CD'
  : values=0


I am really new to linux and I am trying to fix all the problems after installing ubuntu 9.04. Can you please tell me what should I try to change in my case? When I open the GUI for Alsa-mixer, under recording tab, my 'capture' is always muted no matter how many times i tried to unmute, it will be muted again then next time i open it. 

Thanks!

---

### Post by Alfons81 on 2009-08-24
Hi, 

I'm also not so experimented on Linux. I only tried to record something with the software it's coming with Ubuntu ( jaunty ) with my internal mic and it worked. When I run $ alsa contents:

numid=2,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=1,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=127,step=0
  : values=127,127
  | dBscale-min=-95.25dB,step=0.75dB,mute=0
numid=19,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=18,iface=MIXER,name='Headphone Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=31,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=155,155
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
numid=17,iface=MIXER,name='Front Mic Boost'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=3,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=16,iface=MIXER,name='Front Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=15,iface=MIXER,name='Front Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=7,iface=MIXER,name='Front Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=6,iface=MIXER,name='Front Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=17,17
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=11,iface=MIXER,name='Line Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=10,iface=MIXER,name='Line Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=9,iface=MIXER,name='CD Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=8,iface=MIXER,name='CD Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=14,iface=MIXER,name='Mic Boost'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=3,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=13,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=12,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=21,iface=MIXER,name='Mono Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=20,iface=MIXER,name='Mono Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=31
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=5,iface=MIXER,name='Capture Source'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'Mic Jack'
  ; Item #1 'Internal Mic'
  ; Item #2 'PCM'
  : values=1
numid=4,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=23,iface=MIXER,name='Capture Switch',device=2
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=25,iface=MIXER,name='Capture Switch',index=1
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=27,iface=MIXER,name='Capture Switch',index=2
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=3,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=15,step=0
  : values=15,15
  | dBscale-min=0.00dB,step=1.50dB,mute=0
numid=22,iface=MIXER,name='Capture Volume',device=2
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=13,13
  | dBscale-min=-12.00dB,step=1.50dB,mute=0
numid=24,iface=MIXER,name='Capture Volume',index=1
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-12.00dB,step=1.50dB,mute=0
numid=26,iface=MIXER,name='Capture Volume',index=2
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-12.00dB,step=1.50dB,mute=0
numid=28,iface=MIXER,name='Input Source'
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'CD'
  : values=0
numid=29,iface=MIXER,name='Input Source',index=1
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'CD'
  : values=0
numid=30,iface=MIXER,name='Input Source',index=2
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'CD'
  : values=0

Compare it, maybe we have different hardware, the only thing I know is that it worked for me.

Cheers

---

### Post by Marais on 2009-12-18
Hello,
I have a Sony Vaio VGN AW 11/S and as many of us could not get the internal microphone working on Karmic Koala 9.10 Kernel 2.6.31.16 - generic.

My soundcard/chipset info is :
Codec: Realtek ALC889
Codec: Conexant ID 2c06
Codec: Nvidia MCP78 HDMI

After weeks of searching I found the "winning combo" and now my internal mic works (through alsa).
Firstly these instructions need to be followed :
1 - Alsa driver needs to be upgraded to linux-backports-modules-alsa-karmic-generic (2.6.31.16.29)
(easiest to do this with Synaptic Package Manager)
2 - After upgrade find this file =
/.asoundrc

these instructions need to be appended to the file :

pcm.hda-intel {
          type hw
          card 0
       }
       
       ctl.hda-intel {
          type hw
          card 0
       }

3 - In sound preferences choose Analog Stereo Duplex

and yippee all works, speakers, internal microphone and all:popcorn::):guitar:

---

### Post by Marais on 2009-12-22
P.S. After a total system crash I needed to do this again. It works well if you 
1 - update ALSA as stipulated above using the Synaptic Package Manager (search for "linux-backports-modules-alsa-karmic-generic" and the correct version as of this date is (2.6.31.16.29)

2 - the /.asoundrc file needs to be created. I did this by opening / in Nautilus creating a new file in the directory, adding the instructions as stated above and renaming the file to .asoundrc (hidden file need to use control "h" to see it).

3- in a terminal type "alsamixer" to bring up the alsamiser gui then press F4 to view the capture devices, navigate to "capture" (for me the second one) and turn the volume up. I left "Front Mic" all the way down as I'm not using an internal microphone.

As for the total system crash, NEVER I repeat NEVER use this "command of DEATH" =
sudo /etc/init.d/gdm stop
On my machine this destroyed grub to the point where even Supergrub and other utilities could not fix it. I'm sure the solution lay in in UUID numbers but after a whole (wasted) day I just reinstalled a fresh Karmic system (and yes lost all my apps and tweaks :confused::(:frown:

Reboot and all works once again.

---

### Post by faeez on 2010-03-20
It works!!!
Thanks Marais:KS

I've completely given up trying to fix my internal mic problems months ago, but now and then vainly scour the forums for a solution. Marais solution is the only one I've found that works for and it's simple. Love it.

---

### Post by hookfish on 2010-03-28
Marais I would also like to send a thanks to you for the mic solution as well.  It works perfectly.  I wonder if this is a Vaio specific thing.  I used your instructions on a Sony Vaio VGN-FW550F and we are rockin now.  Thanks again.:D:D

---

### Post by Majestic Computing on 2010-04-18
Hi all. I'm very new to Linux but Long in computers. I found this thread trying to get a internal mic working in a Sony VAIO and had no luck untill I read to go to terminal and type alsamixer, then hit f4 to bring up the input screen. when I got to this page on the right I noticed it said <Input So> (I figured this to be input select) , with Front Mi on top of it. I used the arrow keys to go to this then hit up arrow to change it Front Mi to Int Mic, Now the internal mic is active and working. Hope this helps.

---

### Post by diaz8 on 2010-05-04
Only for the records, 

My VGN-NS21S works fine with 

options snd-hda-intel model=toshiba-s06

---

### Post by ajdoakwood on 2010-08-12
This worked perfectly thanks. (Sony vaio vgn-sr39).

---

### Post by MockY on 2010-10-16
I am very happy to say that this is no longer an issue in Ubuntu 10,10. The internal mic works out of the box. Finally I can use my laptop to 100%. Talk about a perfect 10!

---

### Post by rcktsingh on 2011-06-06
> **Tritonio said:**
> I believe that the correct line is:
```
options snd-hda-intel model=vaio
```

This worked like a charm for me. Thank you so much. I use the Sony Vaio - VGN-CS320J

---

