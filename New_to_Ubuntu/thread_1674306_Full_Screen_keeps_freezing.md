---
title: "Full Screen keeps freezing"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-01-23
When i am playing some of the games on Facebook (Frontiervile, Cityville etc... yes, sad i know lol) more often than not when i use the go to full screen link, the game freezes, well rather the screen does. The cursor is still active but has no effect. Pressing escape, takes me back to normal screen as it should and everything works fine.

Anyone have any ideas ? 

i am using the latest Flash player (Adobe Flash Player 10.1.102 i think). Like i say, it is not all the time, about 75% it freezes, but i never had this problem with Windows :(

Have only been using Ubuntu 10.10 a few days (this time around)

Thanks in advance anyone ;)

---

### Post by Sleven7 on 2011-01-24
Since you have just started, I will assume you are using Firefox as a browser.  

Just a suggestion, download Google Chrome browser.  You will need to get the deb 32 bit or 64 bit package, which every applies to your OS.  When it has downloaded, open the download folder and right click on the package and use the Gdebi package installer.

See if you have the same problem in Chrome.

I had Firefox do the same thing on a machine running LM10-32bit, Chome solved the problem.

---

### Post by MadMonkey1966 on 2011-01-24
Thanks for replying :)

I have Chrome on here as well, and sadly it does it with that as well. I am at a loss. OK i can stop using full screen but makes some games hard to play.

It is funny that sometimes it works fine, and like i say it is only the screen that freezes, the cursor moves about ok, but will not click on anything.

Do not know what else to try, as i guess it is something that is common between browsers ](*,)

---

### Post by Sleven7 on 2011-01-24
Since it does it in Firefox and Chrome, try turning off all the extra compiz fusion effects, and then test it.

---

### Post by MadMonkey1966 on 2011-01-24
> **Sleven7 said:**
> Since it does it in Firefox and Chrome, try turning off all the extra compiz fusion effects, and then test it.
I have never heard of that, so i looked it up lol.

I do not think it is installed, well Simple CompizConfig Settings Manager is not if that is what i am looking for.

I have set **Visual Effects** to none, which had no effect.

---

### Post by Sleven7 on 2011-01-24
:-k what graphics card are you using?

---

### Post by MadMonkey1966 on 2011-01-24
> **Sleven7 said:**
> :-k what graphics card are you using?
I think i know how to do that, from Terminal ?

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: IBM Device 0287
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Memory at e8000000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

It is the same card as i have always had, and never had this with Windows, but i am determined to get round this :)

---

### Post by Sleven7 on 2011-01-24
From the terminal run

```
xrandr
```

see if you get a "+" and "*" on the same resolution line

---

### Post by MadMonkey1966 on 2011-01-24
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2048 x 2048
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 359mm x 287mm
   1280x1024      60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  

ok done :)

---

### Post by Sleven7 on 2011-01-24
That means the resolution is set correctly. I enjoy puzzles, we'll get this yet.  Give me a bit, I'm reading up on it.
We have almost the same graphic card, you have the 82865 and I have the 82965 and I don't have the issue you have. Let me check something else, bbib

---

### Post by MadMonkey1966 on 2011-01-24
No problem, i am grateful for the help and i like learning. 

I often get people giving me PC's and laptops to sort out for them, but most them problems are Windows related....in fact most the time i just install new systems for them lol

I have wanted to start using Ubuntu for ages, and now i am out of work, i thought it would be a good time to install it beside Windows XP and start learning :)

---

### Post by Sleven7 on 2011-01-24
I'm still looking, but have to run out for a bit, didn't want you to think I gave up. I'll look more when I get back.

---

### Post by Sleven7 on 2011-01-24
Is your Meerkat of the 32bit or 64bit variety?  Depending on that I have some commands fro you to try.

---

### Post by SEisch on 2011-01-24
Have you tried using a different driver for that video card?  I had to do that on my computer.  It had a similar problem.

---

### Post by MadMonkey1966 on 2011-01-25
> **Sleven7 said:**
> Is your Meerkat of the 32bit or 64bit variety?  Depending on that I have some commands fro you to try.
madmonkey                 
    description: Low Profile Desktop Computer
    product: 8183D7G
    vendor: IBM
    serial: KDYCK1A
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=low-profile cpus=1 keyboard_password=enabled power-on_password=disabled uuid=BE92CB08-714B-33A2-864B-B12C326B19E4

Had to look that up as well, learning lots of new things to do in Terminal :)

Also, this morning, even trying to enlarge to full screen would not work at all, it just turned the game window black and sat there.

---

### Post by MadMonkey1966 on 2011-01-25
> **SEisch said:**
> Have you tried using a different driver for that video card?  I had to do that on my computer.  It had a similar problem.
Not yet, may come to that if we get knowhere. Thanks

---

### Post by Sleven7 on 2011-01-25
Hey Mad M,

Make sure your system is updated before doing this.

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

Let me know if you get any error messages after the second command and we will address them before proceeding.

---

### Post by MadMonkey1966 on 2011-01-25
> **Sleven7 said:**
> Hey Mad M,

Make sure your system is updated before doing this.

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

Let me know if you get any error messages after the second command and we will address them before proceeding.
OK chap....the first command made loads of stuff go through, and then stopped. I entered the next line, but did not get any error messages, got loads for lines of text, then it wanted to install something and asked if it was ok to use then disk space (i said yes of course lol), then load more text went up the screen lol.

when it ended the terminal screen has now turned into a big Grey box entitled

> Configuring ttf-mscorefonts-installer
TrueType core fonts for the Web EULA                                                                                               
 &#9474;                                                                                                                                    
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE  

at the bottom of the box it says OK, but there is nothing to click on, all i can do is close the Terminal by the looks of it.

---

### Post by Sleven7 on 2011-01-25
Thats for MS fonts, don't agree and it should dump you out.

You are running Ubuntu 10.10 32bit right?

Did the terminal tell you to run "dpkg --configure -a"?

---

### Post by Sleven7 on 2011-01-25
When you get to the big gray box, hit tab you highlight the <ok> than hit enter

---

### Post by MadMonkey1966 on 2011-01-25
> **Sleven7 said:**
> When you get to the big gray box, hit tab you highlight the <ok> than hit enter
OK, well before i did that i went and had a go at a few games in Full Screen, didnt not freeze once :)

Now i have hit the <ok> and it did loads of Setting up, Installing, resolving & extracting and finished with

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
Setting up unrar (1:3.9.10-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

I will pop and have a play for 5 minutes :) see what happens.

---

### Post by MadMonkey1966 on 2011-01-25
> **Sleven7 said:**
> Thats for MS fonts, don't agree and it should dump you out.

You are running Ubuntu 10.10 32bit right?

Did the terminal tell you to run "dpkg --configure -a"?
OH , did not see that post...sorry

I dont recall Terminal asking me to do that.

---

### Post by Sleven7 on 2011-01-25
Cool, let me know how the gaming goes.

---

### Post by MadMonkey1966 on 2011-01-25
> **Sleven7 said:**
> Cool, let me know how the gaming goes.
I have just a a quick go on the 3 games i mess about with that use full screen, AND no problems so far(ssshhhh  lol) BUT have to say i did not have anything to do in the games them selves as i had played them earlier.
I will give them a proper go in the morning and get back to you if that is ok :)

Is it ok to add you as a friend, would be nice if i knew at least one person here lol

Also, got a book out the library today called 'Everything you need to get started with Ubuntu Linux', so am off to bed now to learn more (i hope).

Thanks for all your help, i will get back to you tomorrow.
Ian (Madmonkey1966)

---

### Post by Sleven7 on 2011-01-25
Glad it seems to be working for you.  :D

The first code enable the Medibuntu repository, the second updated and installed current flash plugins, java, and codecs.

You can certainly add me as a friend, and I will do likewise.  If you have questions feel free to drop me a pm.

---

