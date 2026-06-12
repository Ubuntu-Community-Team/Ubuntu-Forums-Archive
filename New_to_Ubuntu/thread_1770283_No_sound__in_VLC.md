---
title: "No sound  in VLC"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by manishlogan on 2011-05-29
I am facing this problem from a couple of days. When I play a video in default movie player, voice comes normally but when I play the same in VLC, there is no audio and only video comes.

The same happens with Banshee Music Player. In its case there is no audio again while if the same song is played in rhythmbox, audio comes.

Can someone help me with this one.

---

### Post by jtarin on 2011-05-29
In VLC go to Tools>Preferences>Audio. Is sound enabled?

---

### Post by webofunni on 2011-05-29
also check the sound output module

---

### Post by manishlogan on 2011-05-30
I have check the Preference->Audio n Sound is enabled.

In Output Module, Alsa Output Module is selected.

I have already tried reinstalling vlc, but it was of no use.

---

### Post by webofunni on 2011-05-30
Try changing that to default output device. Also execute 

```

vlc file.ext

```

in terminal and see, if that shows any error.

---

### Post by manishlogan on 2011-06-02
> **webofunni said:**
> Try changing that to default output device. Also execute 

```

vlc file.ext

```

in terminal and see, if that shows any error.

The output was:

VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x888013c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1307230035)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3841): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[0x8918ddc] signals interface error: signal 17 overriden (0x7c144c0)
[0x8918ddc] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x8918ddc] signals interface error: signal 17 overriden (0x7c144c0)
[0x8918ddc] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]

---

### Post by webofunni on 2011-06-02
That looks good. Go to Tools -> Messages in VLC and set the debug level to 2 and play any file. put the result here. Its better you put that in code tag, so that it will be easy to read

---

### Post by cpcpcp on 2011-07-08
> **webofunni said:**
> That looks good. Go to Tools -> Messages in VLC and set the debug level to 2 and play any file. put the result here. Its better you put that in code tag, so that it will be easy to read

I have the same problem no sound when using VLC (which I have just reinstalled with some difficulty)
Tools> messages I can follow but not setting debug level

Please explain this action you have suggested

---

### Post by jonesints on 2011-09-04
I was having the same problem:

Video plays ok, sound doesn't work. If sound happens to work, it stops as soon as you use the scrolling to seek playback position.


@webofunni here is the Debugging level 2 output (txt file) :

[http://ubuntuone.com/349LeVptcIKjmhHSoVMRQB](http://ubuntuone.com/349LeVptcIKjmhHSoVMRQB) 

I googled "main warning: audio drift is too big dropping buffer" and followed the instructions on the following forum and seems to have done the trick!

[http://forum.videolan.org/viewtopic.php?f=13&t=59269](http://forum.videolan.org/viewtopic.php?f=13&t=59269)

Let me know if it sorts it out

---

### Post by vkadal on 2013-03-09
I also had the same problem. I went to tools / preferences and clicked "reset preferences". Then restarted vlc. The sound came but with very poor quality. Then I opened  /dash/ systems / audio /application tab and the sound become alright.

---

### Post by Yuva Raj on 2013-06-11
I had the same problem in Ubuntu 11.04.
It works fine after i did this.
Tools-> Preferences-> Reset Prefernces. 
Later, adjust the sound level just dragging it..that solves my problem :)

---

### Post by craig10x on 2013-06-11
Did you check to see if the "default" in the VLC preferences is set to Pulse Audio?  That could definitely make a difference...

---

### Post by oldos2er on 2013-06-11
Old thread closed. Anyone still experiencing problems should start a new thread.

---

