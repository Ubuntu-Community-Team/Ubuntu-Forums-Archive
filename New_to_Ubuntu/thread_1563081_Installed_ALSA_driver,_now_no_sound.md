---
title: "Installed ALSA driver, now no sound"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by robfuller on 2010-08-28
Hello,

I have just installed ALSA from this page [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) in an attempt to get the internal microphone on my Lenovo ThinkPad x100e to work. (ALSA was suggested as a solution to the microphone problem here [http://www.thinkwiki.org/wiki/Category:X100e](http://www.thinkwiki.org/wiki/Category:X100e) and elsewhere.)

Having done that, I now do not have any sound on my laptop at all. Detailed symptoms are:
* The volume indicator applet shows the sound as muted, but it does not respond to clicking or to keyboard shortcuts for volume.
* Rhythmbox and Banshee just go gray if I try to play any music, and I have to "force quit" out of them.
* When click on System > Preferences > Sound, I get a "starting sound box on the lower panel for a few seconds, but the sound preferences box does not appear.
* I installed the GNOME ALSA Mixer, but can't open it. When I click on it in the Applications menu, I similarly get a "starting GNOME ALSA Mixer" message for a few seconds, then nothing. If I try to run alsamixer from a terminal, the terminal just freezes.

Any ideas what is happening, and what I need to do? Should I not have tried to install ALSA? Sorry if the answers are obvious - I haven't been able to find anything useful by searching.

Thanks,
Rob

---

### Post by robfuller on 2010-08-31
Since my last message, I was having severe performance problems with other software on the laptop, so I uninstalled alsa-driver-linuxant. Now everything is back to normal, except that I still have no sound at all. Under System > Preferences > Sound, there is nothing listed under the "Hardware" tab.

Can anyone help me with this?

Also, I*made an error in my original message:*installing the linuxant driver was an attempt to get the headphone jack to work, not the internal microphone. Neither have worked since I installed Ubuntu. But both are now lower priorities since I*don't have any sound at all...

Thanks,
Rob

---

### Post by robfuller on 2010-09-07
In case anyone else in a similar position reads this:

I never found out how to restore my sound in 10.04. Even after reinstalling ALSA (using this script [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)), I still had problems. Finally, I upgraded to the 10.10 beta, and found that sound works normally.

The headphone jack and the internal microphone still aren't working, but I'm glad that I at least have sound output through the internal speakers.

Rob.

---

### Post by juliobahar on 2010-09-11
this x100e is really giving me a hard time.

I'm able to get sound and make the internal mic. work using the alsa linuxant driver - as been mentioned by you previously - 

The problem is that this driver is quite unstable. The sound driver just stops responding and can't recognized the conexant sound card after opening some programs, of which recently I experiences are pidgin, virtualbox and google chrome with the googletalk plugin.

I have to restart ubuntu whenever this thing happens.

I personally don't think upgrading to beta 10.10 isn't a good idea. As we are experiencing problem with the fully-fledged distros.


We need serious help with these x100e thinkpads

---

### Post by juliobahar on 2010-09-11
This post shouldn't be labelled as SOLVED!!!

---

### Post by stmiller on 2010-09-11
> We need serious help with these x100e thinkpads

x100e looks to be using a relatively new AMD based chipset, etc, and from [what I can find]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=x100e#sclient=psy&hl=en&q=x100e+linux") is not so Linux friendly unfortunately. 

Anything Intel based works out of the box in Linux, but AMD/ATI based - not so well. :/

For audio specifically, you may have better luck on an alsa mailing list, or finding some of the various 'linux on x100e' websites out there.

Some laptops just aren't very Linux friendly unfortunately due to hardware manufacturers either not releasing specs for drivers to be written, or perhaps being a bleeding edge product that hasn't had time to mature in the Linux world.

---

### Post by robfuller on 2010-09-24
Hello again,

Now I finally have all my sound devices (including internal mike and the headphone jack) working correctly. The key was to edit /etc/modprobe.d/alsa-base.conf to add the following two lines:

options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes

...as suggested by jeffmings in this thread: [http://ubuntuforums.org/showthread.php?t=1489185&page=4](http://ubuntuforums.org/showthread.php?t=1489185&page=4)

Unlike jeffmings, I'm not using the linuxant driver. But I am running the Ubuntu 10.10 beta (kernal 2.6.35), so maybe that's the difference.

Hope this helps you too!
Rob

---

### Post by lkjoel on 2010-09-24
> **robfuller said:**
> Hello,

I have just installed ALSA from this page [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) in an attempt to get the internal microphone on my Lenovo ThinkPad x100e to work. (ALSA was suggested as a solution to the microphone problem here [http://www.thinkwiki.org/wiki/Category:X100e](http://www.thinkwiki.org/wiki/Category:X100e) and elsewhere.)

Having done that, I now do not have any sound on my laptop at all. Detailed symptoms are:
* The volume indicator applet shows the sound as muted, but it does not respond to clicking or to keyboard shortcuts for volume.
* Rhythmbox and Banshee just go gray if I try to play any music, and I have to "force quit" out of them.
* When click on System > Preferences > Sound, I get a "starting sound box on the lower panel for a few seconds, but the sound preferences box does not appear.
* I installed the GNOME ALSA Mixer, but can't open it. When I click on it in the Applications menu, I similarly get a "starting GNOME ALSA Mixer" message for a few seconds, then nothing. If I try to run alsamixer from a terminal, the terminal just freezes.

Any ideas what is happening, and what I need to do? Should I not have tried to install ALSA? Sorry if the answers are obvious - I haven't been able to find anything useful by searching.

Thanks,
Rob
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by juliobahar on 2010-09-25
> **robfuller said:**
> 

Unlike jeffmings, I'm not using the linuxant driver. But I am running the Ubuntu 10.10 beta (kernal 2.6.35), so maybe that's the difference.



This statement looks promising as we are expecting improvement in ubuntu 10.10. But for those using older kernel I guess the right thing to do is to install the linuxant driver.

Btw I have my sound working fine but the only problem is that I have to recompile the driver every time the kernel is updated. I did NOT modify the /etc/modprobe.d/alsa-base.conf file.

---

