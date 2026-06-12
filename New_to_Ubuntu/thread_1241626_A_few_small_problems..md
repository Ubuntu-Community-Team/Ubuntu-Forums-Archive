---
title: "A few small problems."
date: 2009-08-16
forum: New to Ubuntu
---

### Post by Jenked on 2009-08-16
My PC is an HP Pavilion Slimline s7700n with onboard GeForce 6150 LE (512). I dual boot Ubuntu Jaunty Jackalope and Vista Home Premium.

I'm about ready to give up on windows altogether (now I've got pidgin working), except, as far as some of my favourite websites go, things are not all well and good. I'm using Firefox and I installed flashplugin-nonfree. YouTube is persistently choppy (every video will stutter at east twice during it's duration, and some take time to display any video) and other flash video sites (The Excapist's Zero Punctuation vids being a partucularly irksome example) simply don't play at all and only show a blank box. Not even the grey box with the circled play arrow. Still other sites do show that arrow.

I've also noticed some audio glitching with application sounds. Like when I enabled some sounds in Pidgin, just so I would know when a new IM tab had opened up (I kept missing messages), when they play there is always a little distortion or a buzz. But MP3s and videos from the HD play fine with VLC or the proprietary media player, Totem.

When youtube vids play, they get the same audio glitching which can screw up the audio/video sync. Also, when I pause a video (a habit I got into to pre-load vids so I could then watch then with no interruptions) on youtube, sometimes it doesn't pre-load. So that can obviously lead to even more stuttering and glitching.

Another thing I have noticed is that the suspend and hibernate options do not work. Maybe I'm expecting them to work like they do in Windows, but despite that if I choose one the monitor will shut off but the PC towers stays on and no input will do anything other than swithcing the tower off! I had similar problems in windows trying to use teh Sleep finction (it never stayed asleep for more than two or three seconds), so I downloaded "Shutter", a small app that gave all the shutdown options any PC user could ever want and I started using Hibernate, which wasn't a default for my desktop system. If there's a fix or similar workaround for Linux that anyone knows about that would be great.

I'd also like to know if there is a good alternative to iTunes for Linux. By which I mean, something that works as much like iTunes as is possible. I already have a full iTunes library and would like something that could access it and play the whole library on shuffle if I wanted to, without it having to copy any music files into its own file-system.

Finally, every time Ubuntu plays an "error" or "you can't do that" sound, it comes out of the computer speaker (the one on the motherboard that just goes beep) and I can't work out how to stop or change it. I've opened up the sound options tool and every preview sound is present as a played sound, not a beep, and there is no system bell tab.

Sorry about the somewhat disjointed style of my post, I've been compiling this list since I installed Linux.

Any and all help MUCH appreciated.

---

### Post by Barafu Albino Cheetah on 2009-08-16
Thefirst thing i'm thinking about is PulseAudio. I remove it altogether and have never seen such problems. Find a good howto if you think of doing the same.
About ITunes - what functions do you need? There are amarok, banshee, rythmbox, many others.

---

### Post by llamabr on 2009-08-16
Just a thought about your youtube problem.  I remember that mine came with something like swf plugin and gnash.  They are flash plugins, and they're crap.  I had to remove both of those and install the adobe flash instead.

Look for them in top while you're running a video and kill them, or uninstall them.

Just a thought -- hope it helps.

---

### Post by CatKiller on 2009-08-16
> **Jenked said:**
>  I've also noticed some audio glitching with application sounds. 

PulseAudio configuration can be a bit of a pain if the defaults don't just work. There are some settings in /etc/pulse/daemon.conf that might help. Or you could just switch to ALSA for the time being.

> But MP3s and videos from the HD play fine with VLC or the proprietary media player, Totem.I don't think proprietary means what you think it means in this context.

>  Another thing I have noticed is that the suspend and hibernate options do not work. It's probably to do with hardware support for suspend and hibernate, especially since you mentioned that it hadn't worked in Windows, either. I configured something called uswsusp to do it on mine (which also doesn't have hardware support), although I can't remember the details because it was about three years ago.

> 
I already have a full iTunes library and would like something that could access it and play the whole library on shuffle if I wanted to, without it having to copy any music files into its own file-system.That would be all of them. I have no idea why Windows software insists on copying everything somewhere else, but I agree that it's stupid.

Personally, I use Amarok, but others have recommended Exaile, Banshee, Rythmbox, Audacious, Songbird... They're all good.

> 
Finally, every time Ubuntu plays an "error" or "you can't do that" sound, it comes out of the computer speaker (the one on the motherboard that just goes beep) and I can't work out how to stop or change it. If you want the PC speaker to stop and never start again (a lot of people do) you can use 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` to add in the line ```
blacklist pcspkr
```

---

### Post by Jenked on 2009-08-16
> **llamabr said:**
> Just a thought about your youtube problem. I remember that mine came with something like swf plugin and gnash. They are flash plugins, and they're crap. I had to remove both of those and install the adobe flash instead.

Look for them in top while you're running a video and kill them, or uninstall them.

Just a thought -- hope it helps.
I don't know what you mean by looking for them in top. Could you explain this in an idiot-proof way please?

> **CatKiller said:**
> I don't think proprietary means what you think it means in this context.
I just meant the player that comes with the distro I have.

---

### Post by DivisionMatrix on 2009-08-16
I messed up and installed a bad flash plugin, to fix it I went to Synaptic Package Manager, searched for flash till I found the active plugins, removed them, and added the adobe flash player one. Not sure if thatll help you, but maybe?

Also, look up ubuntu restricted extras in add/remove, it has support for flash, mp3's, and all kinds of formats...

---

### Post by wojox on 2009-08-16
Put this in the terminal:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Jenked on 2009-08-16
That did it! All the flash based sites I visit now work flawlessly! Thank you so much.

---

### Post by jrox717 on 2009-08-16
>  I don't know what you mean by looking for them in top. Could you explain this in an idiot-proof way please? 

Top is a terminal command (well, program) which shows you all the running processes along with how much CPU and RAM they are using, in realtime. To access it open up a terminal by going to Applications > Accessories > Terminal and type in "top". To exit press "q" and to kill a process type
```
 sudo kill <process id> 
```

About your hibernation problem, this may not (probably won't) solve anything, but you should make sure that you have swap space available, in that you need to have a swap partition (probably created during installation) and swap enabled. In top you can see how much swap is available, and if it says 0%, look at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

>  I don't think proprietary means what you think it means in this context. 
[http://en.wikipedia.org/wiki/Proprietary_software](http://en.wikipedia.org/wiki/Proprietary_software)


Good luck and welcome to ubuntu!

---

