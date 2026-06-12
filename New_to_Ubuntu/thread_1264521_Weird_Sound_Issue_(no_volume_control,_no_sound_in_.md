---
title: "Weird Sound Issue (no volume control, no sound in browser)"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by llamabr on 2009-09-12
Hi, folks.  I've recently completed a fresh install on my laptop of karmic.  Sound does not work when playing videos, music, etc from within browsers.  I've tried it in both firefox and konqueror.  For example, no sound in youtube videos.

However, I'm able to hear sound using other apps, such as mplayer, and I can even dload the afore-mentioned youtube videos, and play them in mplayer.

Furthermore, the little volume control thingy on the bar at the top doesn't adjust the volume at all.   However, I'm able to adjust the volume using alsamixer, from the cli.

I've looked in System > Preferences > Sound and see "Alsa Plugin for Firefox" under applications.  But it's turned up, and not muted.

This occurs for all users, including one fresh user created just to test this behavior.  So I'm stumped.  Please help: there's a football game on tonite at 7 that I'd like to catch.

---

### Post by llamabr on 2009-11-08
A fresh install of 9.10 after the release, and I'm still having this strange behavior.  Any help?

---

### Post by llamabr on 2009-11-13
still unsolved by me, so would still appreciate advice

---

### Post by anewguy on 2009-11-13
I saw your post and decided to see if I had any sound since installing 9.10.  So far, I don't have sound, but knowing myself well enough I for now am going to assume it's something silly I just didn't find yet.  I'll keep you posted if I think there is something that might help you.

Dave :)

---

### Post by camaron1 on 2009-11-13
> **llamabr said:**
> Hi, folks.  I've recently completed a fresh install on my laptop of karmic.  Sound does not work when playing videos, music, etc from within browsers.  I've tried it in both firefox and konqueror.  For example, no sound in youtube videos.

However, I'm able to hear sound using other apps, such as mplayer, and I can even dload the afore-mentioned youtube videos, and play them in mplayer.

Furthermore, the little volume control thingy on the bar at the top doesn't adjust the volume at all.   However, I'm able to adjust the volume using alsamixer, from the cli.

I've looked in System > Preferences > Sound and see "Alsa Plugin for Firefox" under applications.  But it's turned up, and not muted.

This occurs for all users, including one fresh user created just to test this behavior.  So I'm stumped.  Please help: there's a football game on tonite at 7 that I'd like to catch.

Have you tried uninstalling pulseaudio? It is causing lots of trouble with Karmic.

---

### Post by llamabr on 2009-11-15
that's it.  i removed pulseaudio, and it's fine.  thanks.

---

### Post by camaron1 on 2009-11-16
> **llamabr said:**
> that's it.  i removed pulseaudio, and it's fine.  thanks.
Great :grin:

---

### Post by wodr on 2009-12-02
> **llamabr said:**
> that's it.  i removed pulseaudio, and it's fine.  thanks.

Hey, 

I had the same problem and your solution worked for me too, thanks. I got two questions now. 

1. Is Totem working for you? If not what do you using for listening music and watching movies...

2. After uninstalling pulseaudio the volume menu disapeared and I cannot access the sound setting in System>Preferences>Sound

It is just writing "Waiting for sound system to respond".

I found the way how to change the volume, just I have to open terminal every time.

---

### Post by llamabr on 2009-12-02
after uninstalling pulseaudio, yes, I believe totem now works.  i use mplayer almost exclusively.

why did you reinstall pulseaudio?

---

### Post by wodr on 2009-12-02
> **llamabr said:**
> after uninstalling pulseaudio, yes, I believe totem now works.  i use mplayer almost exclusively.

why did you reinstall pulseaudio?

I meant uninstall of course and I corrected it. Totem does not work for me, any suggestions?

---

### Post by wodr on 2009-12-02
mplayer is much better than totem, thank you very much man

One more silly question. Is there any way how to get the volume icon somewhere to be able to change the sound volume or do I have to start terminal and alsamixer every time?

Thanks a lot for your help :)

---

### Post by togo59 on 2009-12-02
Uninstalling pulseaudio doesn't do it for me.

I did have sound on 9.10 and after a big struggle I got it going again, now it's gone again.

Here's my specs
```
roger@rubi:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DMX6Fire [TerraTec DMX6Fire], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
roger@rubi:~$ lspci | grep audio
00:0e.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```
```
roger@rubi:~$ sudo lshw | grep audio
             description: Multimedia audio controller
                capabilities: removable audio cd-r cd-rw dvd dvd-r
             description: Multimedia audio controller

```
I have a Terratec DMX 6fire sound card
I am running Ubuntu Studio 64bit Karmic

As I said it *was* working under Karmic. I don't remember doing anything that could have stopped it.

I have uninstalled pulseaudio -- no effect
I have reinstalled pulseaudio -- no effect

I have smashed my head against the wall, repeatedly ](*,) -- slight effect

Help?

---

### Post by wodr on 2009-12-02
Do you have alsa installed? Can you hear any sound from your computer or none?

---

### Post by mgmiller on 2009-12-02
The problem is your sound card.  It is a known issue:
[https://answers.launchpad.net/ubuntu/+question/87553](https://answers.launchpad.net/ubuntu/+question/87553)

Perhaps you could try enabling the sound on your mobo instead?

---

### Post by togo59 on 2009-12-03
Many thanks for the heads-up on the Terratec sound-card issue. S'funny, I did have it working for a while under 9:10. I was trying all sorts of things and suddenly I noticed the system sounds, then I tried some music apps (zynsubaddfx, rhythmBox) and it all worked. Next day it didn't.

Of all the versions, Karmic is the worst for me. No sound on my home computer and huge (now resolved) graphics issues on my lap top. The pits.

I'm very close to going back to Suse, from whence I came. But I have a Mint Helena CD next to me, that's going on my daughter's PC.

---

### Post by togo59 on 2009-12-04
..and this morning, having changed PRECISELY NOTHING, it works!! :frown:

Karmic: Non-positive Karma.

[EDIT (about 5 hours later): Re-booted, having touched no system parameter, and no sound again.
If Karmic was a real Koala, I'd stuff him.]

---

### Post by mgmiller on 2009-12-04
I know this is not helpful, but I have found Karmic to have the best sound control of any Ubuntu release to date and I have been using it since 4.10.  It is absolutely flawless on my 4 desktop and 2 notebook computers.  I can plug in an external usb microphone and it just works.  I can control 2.1 and 4.1 (or higher) surround with no problems.

If it's in your budget, can you try different hardware for the sound card?  Isn't the one you have now and external USB sound card?  Do you have one built into your motherboard?

That raises another question, if you do have a built in sound card, you should disable it in BIOS.  I have found having multiple sound cards ofter confuses things.

---

### Post by togo59 on 2009-12-12
The DMX 6fire is a little gem. It's in two parts: a drive-bay mounted unit with optical, MIDI, gold-plated audio ins and outs and a PCI card with 5.1. I recently bought my daugher a Focusrite USB/Firewire unit for much more money and it's nowhere near as good to use. So no, I'm not going to swap it.

I have pulseaudio uninstalled. Sometimes I boot up and the sound works fine and sometimes (most times) it doesn't.

EDIT: (Rant over)

By following [_[COLOR="RoyalBlue"]these instructions[/COLOR]_]("http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/") for a clean build and install; and setting my BIOS to "Music Live" <-- I don't know whether that was necessary because a) it was working fine and dandy in 9.04 and with earlier versions, and b) it was working on and off in 9:10

But installing ALSA 1.0.21 and then running the config and choosing ICE1712 fixed it.

---

### Post by togo59 on 2009-12-16
Bump. Spoke to soon.

Despite recompiling, reconfiguring it's up to its old tricks again. Working fine one time, the next day not a squeak. 

I go to System -> Preferences -> Sound and it just says: "waiting for sound system to respond".

:confused:

---

