---
title: "GFCE Ultra Freezing"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Excedio on 2009-11-22
Hey guys...ever since I upgraded to 9.10, my GFCE Ultra freezes every time I try to play a game. Is anyone else seeing this? Has anyone solved this?

I'm not getting any error messages when I run a game through the terminal. Any help possible please...my wife needs her Bubble Bobble fix...

---

### Post by cariboo on 2009-11-22
I think you're goning to have to give us a little more information. What is a GFCE?

---

### Post by Excedio on 2009-11-22
> **cariboo907 said:**
> I think you're goning to have to give us a little more information. What is a GFCE?

Sorry, thought it was a better known program. :-)

[**GNOME FCE Ultra 0.6.1**]("http://www.youtube.com/watch?v=UwkqsBT0Sms")
A GNOME front-end end for the FCE Ultra Nintendo Entertainment System emulator

It worked perfectly in 8.04, 8.10 & 9.04.

Here is what I get in the terminal:
```
gfceu message:  Using: /usr/games/fceu
/usr/bin/gfceu:510: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.widgets = gtk.glade.XML(glade_file)
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 0 -opengl 0  "/home/jmaltmann/Downloads/ROMS/Adventure Island.nes"

Starting FCE Ultra 0.98.12...
Loading /home/jmaltmann/Downloads/ROMS/Adventure Island.nes...

 PRG ROM:    2 x 16KiB
 CHR ROM:    4 x  8KiB
 ROM CRC32:  0xf8a713be
 ROM MD5:  0x248ba1acbfed28be4e6839a858a5c60a
 Mapper:  3
 Mirroring: Vertical

Initializing video... Video Mode: 512 x 448 x 32 bpp 

Initializing sound...
 Bits: 16
 Rate: 48000
 Channels: 1
 Byte order: CPU Native
 Buffer size: 1024 sample frames(21.333333 ms)

```

Everything there looks perfectly normal, but every game I try to play just freezes as it begins.

---

### Post by Flecko on 2009-12-24
I'm seeing the same issue as well. The only way I can seem to get it to work without freezing is to disable sound?!

Not optimal, but I see no other way to fix it for the time being.

Anyone else?

---

### Post by Zzl1xndd on 2009-12-24
I have been having the same issue, but I have not yet been able to solve it. Disabling the sound works for me as well.

---

### Post by Keith Fox on 2010-01-19
Has anybody solved this issues yet?  Disabling sound is the temporary work around.  Has anybody *filed a bug* for this problem? I didn't know that disabling the sound fixes it until I read this thread.

---

### Post by Keith Fox on 2010-01-19
[FONT=Courier New]super mario bros 3 with GFCE in Ubuntu 9.10[/FONT].  it appears ever so slightly choppy.

---

### Post by hackerseraph on 2010-02-05
disabling sound, oddly, worked for me as well o.O

---

### Post by doctorbighands on 2010-02-11
I wasn't having trouble with freezing. An entirely different problem brought me here: it was being SUPER choppy! I was ready to chalk it up to my weak integrated graphics, until I found this thread.

I disabled sound, and now all is well. No more chop.

If I knew how to properly file a bug report, I would. It certainly seems that one needs to be filed.

---

### Post by LunaticHiatus on 2010-02-11
an older version of gfce might be more stable

---

### Post by beingthehero on 2010-12-01
I'm having the same problem. There's some sound if you crank up the volume, but it's a distorted, white-noise-esque mess. Was there any solution beyond disabling the sound, which really isn't much of a solution? I'd like to hear my Mega Man music while I play it. ;_;

---

### Post by mister_playboy on 2010-12-02
FCE Ultra is deprecated... the current version of the emulator is FCEUX 2.1.4a and can be found in the Software Center.

I don't have any freezing issues with it, but I haven't been able to get the sound working correctly in 10.10.

I recommend people try out Nestopia.  Some fellow forum users have made .deb packages available: 64 bit [here](http://ubuntuforums.org/showpost.php?p=10153858&postcount=71) and 32 bit [here](http://ubuntuforums.org/showpost.php?p=10175811&postcount=73).

---

