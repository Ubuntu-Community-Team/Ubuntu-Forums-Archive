---
title: "I'm having a terrible time with Ubuntu"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by jermza on 2010-01-06
I've spent hours upon hours trying to come right, and getting more frustrated.  I'm ready to revert to Windows.

1.  Ubuntu's sound is ridiculous.  When it starts up, it's so loud that the next suburb can hear it.  The volume control makes no difference.  Wherever I slide it, the sound is fully blast.  Unless it's muted.

2.  Firefox is slow.  I'm used to using Chrome, which is way faster.

3.  My graphics display is a disaster.  The ATI Catylist Control Centre works fine in Windows.  In Ubuntu, it tells me that it can't find the driver.  I've downloaded the driver (or a legacy set from the AMD site), but have no idea what to do next.

4.  MP3s play when I double click on them.  But when I try play them in Ryhmbox, it throws some error and puts a little 'no entry' sign next to the track.

5.  F-spot is useless.  Whenever I click on "import", it closes.

I'm hoping someone can help, because I like the idea of Ubuntu and want to give it a shot.

---

### Post by marco123 on 2010-01-06
> **jermza said:**
> I've spent hours upon hours trying to come right, and getting more frustrated.  I'm ready to revert to Windows.

1.  Ubuntu's sound is ridiculous.  When it starts up, it's so loud that the next suburb can hear it.  The volume control makes no difference.  Wherever I slide it, the sound is fully blast.  Unless it's muted.

2.  Firefox is slow.  I'm used to using Chrome, which is way faster.

3.  My graphics display is a disaster.  The ATI Catylist Control Centre works fine in Windows.  In Ubuntu, it tells me that it can't find the driver.  I've downloaded the driver (or a legacy set from the AMD site), but have no idea what to do next.

4.  MP3s play when I double click on them.  But when I try play them in Ryhmbox, it throws some error and puts a little 'no entry' sign next to the track.

5.  F-spot is useless.  Whenever I click on "import", it closes.

I'm hoping someone can help, because I like the idea of Ubuntu and want to give it a shot.

1. If you are talking about the startup sound go to: System>Preferences>Startup Applications and uncheck the box for "Gnome Login Sound"

2. Install Chrome: [http://www.google.co.uk/chrome](http://www.google.co.uk/chrome)  It's a .DEB file which you is kind of like a .exe

3. System>Administration>Hardware Drivers and enable them.

4. Run 

> sudo apt-get install ubuntu-restricted-extras

in the terminal. Applications>Accessories>Terminal.  This installs Flash, Java and all the codecs you will need.

5. I've been having problems with FSpot too. Try using Digikam "sudo apt-get install digikam"

Marco.

---

### Post by mkoehler on 2010-01-06
Here's some answers for 1, 2, & 5.

1. Turn down the PCM volume.  If that doesn't work, we'll try some other things.

2. Download google chrome for linux.  It's what I use.  Find it here:

[http://www.google.com/chrome](http://www.google.com/chrome)

5. FSpot is useless.  I use picasa for linux and it works flawlessly (note: it cannot import videos at this time):

[http://www.google.com/picasa/linux/](http://www.google.com/picasa/linux/)

---

### Post by RedSingularity on 2010-01-06
+ 1 for google chrome 

Oh and as for the sound try this in a terminal

alsamixer

---

### Post by tom.swartz07 on 2010-01-06
You could turn down your boot up sound from the sound options in settings.

In regards to your graphics card, if you have an ATI- it might not be supported. ATI is notoriously terrible with support for their cards. The reason that your computer is snapping out with the graphics, is because the Catalyst Control Center is meant for the newer cards, rather than your older card.

Sorry about your bad experiences so far. When I first installed Ubuntu, I broke it completely because I installed the same CCC for my outdated graphics card. 

The learning curve is slightly steep coming from windows, but trust me- its such a joy to use once you get used to the OS

---

### Post by Guitar John on 2010-01-06
> **jermza said:**
> I've spent hours upon hours trying to come right, and getting more frustrated.  I'm ready to revert to Windows.

4.  MP3s play when I double click on them.  But when I try play them in Ryhmbox, it throws some error and puts a little 'no entry' sign next to the track.


What version of Ubuntu are you using?

Are your MP3's in your "Music" folder?

In Rhythmbox, click Edit>Preferences>Music Tab
"Music files are placed in ______"  <<<make sure that it is looking in your "Music" folder. 
Tick the box that says "Watch my library for new files."

---

### Post by laidback on 2010-01-06
> **mkoehler said:**
> Here's some answers for 1, 2, & 5.

2. Download google chrome for linux.  It's what I use.  Find it here:

[http://www.google.com/chrome](http://www.google.com/chrome)



mkoehler,

Just took your suggestion and downloaded Google Chrome. Impressive, thanks for the info. Up and running in just 2 mins at the most.

Happy New Year

laidback

---

### Post by Bartender on 2010-01-06
Everybody talks about how Chrome is faster.  Maybe with broadband, but it feels slower than FF on dial-up!

---

### Post by k64 on 2010-01-06
> **Bartender said:**
> Everybody talks about how Chrome is faster.  Maybe with broadband, but it feels slower than FF on dial-up!

If you want Chrome, [the best way to go on Linux is building Chrome OS]("http://www.chromium.org/chromium-os"). The build process involves shell scripts, which ease the build process. I've done this, and booted Chrome OS (not to mention installed it) on my Acer Aspire One, and it booted flawlessly. That is, on the AOA110-1545.

Oh, and Canonical partnered with Google on Chrome's initial build. Google and Ubuntu, therefore, are friends.

---

### Post by jermza on 2010-01-07
Thanks for the replies.

1.  Rythmbox issue resolved.  I needed to put the music into the Music folder.  Thanks.

2.  Sound is still a problem.  There is no startup sound, thankfully.  But the volume bar at the top right doesn't work.  At lowest or highest (other than mute), the actual volume output doesn't change.  And by default it's at full volume.  At this rate, Ubuntu is going to blow my speakers.  Not cool.  So if I play a MP3, its default is full volume.  I then have to go to Terminal and adjust the outputs there.  Which, inevitably, don't save after a reboot.

- sound is too loud;
- volume control does nothing

3.  Chrome is now installed, thanks.

4.  Ubuntu doesn't find the ATI legacy driver set that I downloaded, after clicking on System > Admin > Hardware Drivers.  This is so that my Catylist Control can work (like it does in Windows).  My display is terrible and I can't work like this.

Ideas?

---

### Post by jermza on 2010-01-07
Not only does F-spot crash when I click "import", Picasa doesn't even start up (I've installed it too).

I've installed the Restricted Extensions (or whatever it's called) with all the codecs etc, and I tested it now in Facebook - in the Upload Photos section - and am unable to upload any pictures.

---

### Post by melrokz on 2010-01-07
for the sound problem, try lovering the PCM volume. If this works 4 u, right-click on the volume control icon > Preferences > PCM. Good luck!

---

### Post by jermza on 2010-01-07
I'm back on Windows now, and everything is so much smoother.  I really want to migrate to Ubuntu, but the amount of time I'm spending simply trying to make it work (combined with googling and searching for help) is worrying.

Regarding the sound, I'm going around in circles.  I keep being told to lower the PCM, which I do.  It doesn't save after rebooting, firstly, and secondly, the volume slider at the top right of the desktop does nothing except for mute.  I can scroll it left and right, and the volume stays at where it is.

My hassles are in my previous post.

There are good points, I might add (which, sadly, are being drowned by my hassles).  I love the layout of Ubuntu; that it's free; that GIMP is quick and amazingly sees my exact Wacom tablet (impressive!).

---

### Post by thatguruguy on 2010-01-07
I have no idea what your sound setup is, since you haven't given any specs of your system.

However, this is what works for me.  I run Ubuntu 9.10 on a Dell notebook which is docked most of the time.  When it's docked, sound is ported through the dock and needs to use digital sound.  When it's not docked, it uses the internal hardware, which is analog.  If I'm running in analog mode when docked, sound is either all the way up or off.  It's possible that your problem is similar in nature.

Try this, and see if it works.  Right click on the volume button in your panel.  Choose "Sound Preferences".  A dialog should pop up. Click on the "Hardware" tab.  You should see a "Profile" drop-down towards the bottom of the dialog box.  If it is currently showing something like "Digital Stereo Duplex" change it to "Analog Stereo Duplex".  Or vice-versa.  Play with it and see if you get something that works.

---

### Post by jermza on 2010-01-07
> **thatguruguy said:**
> I have no idea what your sound setup is, since you haven't given any specs of your system.

Try this, and see if it works.  Right click on the volume button in your panel.  Choose "Sound Preferences".  A dialog should pop up. Click on the "Hardware" tab.  You should see a "Profile" drop-down towards the bottom of the dialog box.  If it is currently showing something like "Digital Stereo Duplex" change it to "Analog Stereo Duplex".  Or vice-versa.  Play with it and see if you get something that works.

I will try that and let you know.  I did see all that stuff, but don't know what it is.  I'm not a techie.

---

### Post by iMisspell on 2010-01-07
If you try it again, maybe this will help you (if you havnt already been there) with your video drivers.
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)


Providing alittle more info in the furture might help alittle, what version of Ubuntu, what ATI card you have and the version number on the drivers you have tried.


_

---

### Post by jermza on 2010-01-07
> **iMisspell said:**
> If you try it again, maybe this will help you (if you havnt already been there) with your video drivers.
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)


Providing alittle more info in the furture might help alittle, what version of Ubuntu, what ATI card you have and the version number on the drivers you have tried.


_
I've got an old 9600 card.  And Ubuntu 9.10 (the one from the website's home page).

---

### Post by k3lt01 on 2010-01-07
> **jermza said:**
> I've got an old 9600 card.In your first post you say you downloaded a legacy driver from the AMD site.
> **jermza said:**
> 3.  My graphics display is a disaster.  The ATI Catylist Control Centre works fine in Windows.  In Ubuntu, it tells me that it can't find the driver.  I've downloaded the driver (or a legacy set from the AMD site), but have no idea what to do next.Why did you do that when there is a Linux option? The legacy drivers are for Windows 98 and ME and are not going to be of any help to you in Linux. Download the Linux x86 if you are using a 32 bit system or the Linux x86_64 of you are using a 64 bit system.

Then you need to know if its a Radeon 9600, an All-In-Wonder 9600 or a Mobility Radeon 9600 card. After you have got that worked out click GO and download the correct driver.

---

### Post by jermza on 2010-01-07
> **k3lt01 said:**
> In your first post you say you downloaded a legacy driver from the AMD site.
Correct.  I googled it and that's where I landed up.

> Why did you do that when there is a Linux option? The legacy drivers are for Windows 98 and ME and are not going to be of any help to you in Linux. Download the Linux x86 if you are using a 32 bit system or the Linux x86_64 of you are using a 64 bit system.
What does "Download the Linux x86" mean?  I'll happily do it if I know what I means. :(

---

### Post by Ubu2010 on 2010-01-07
Pardon me for interrupting, but that is the Linux-specific driver.

---

### Post by zine92 on 2010-01-07
Anyway for first time linux users, what i recommend is to dual boot like me. My hybrid ati drivers is the reason i kept windows among other things. But i do think ubuntu is easier to learn than that of windows because of the flexibility offered in linux. Take it slowly, some googline along the way. And anyway i know chrome is fast, people are using it saying how fast it is, but what i think personally is that firefox is still the superior for me because it it free and its community of folks down at the mozilla is also very warming and friendly. Though i love google and their products but i just don't feel like using chrome all the time.

---

### Post by 3rdalbum on 2010-01-07
1. There's no ATI driver for the 9000 series cards. ATI doesn't make drivers for those cards anymore, and this includes not maintaining the old drivers to work on today's Linux distributions.

So in other words, you need a newer graphics card (Radeon HD 2400 or above, but preferably something from Nvidia) or you are stuck with the open-source video driver which is improving all the time.

2. Your issue with the Java-based photo uploader on Facebook is atypical. I just discovered this photo uploader a couple of minutes ago! I'm sorry I can't give any sort of solutions to this, because I've only ever seen the photo uploader NOT work when Java is not installed.

---

### Post by Perturbed Penguin on 2010-01-07
I am sorry you are having such problems with Ubuntu, I have never had so many issues! I guess it just doesn't like some systems. Anyways as far as downloading your drivers go you will want to download them from here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

The x86 means that it is compatible with a 32bit processor/operating system whereas the x86_64 means it is compatible with a 64bit processor/operating system. We need to know if you are using 64bit Ubuntu or 32bit, do you remember which you installed? The 64bit for Ubuntu is known as something like 'Ubuntu 9.10 amd64'

As stated by the previous poster you will need to know more specifically what card you have, aka radeon, radeon mobility, et cetera. Unfortunately I have never dealt with ATI drivers on any OS ever before so I do not know for certain what you need to do to install those drivers once you have them downloaded... a google search should bring up many how-tos showing what to do though.

As far as your flash or Java woes go I am not sure what to tell you, perhaps you are using the free version of flash from the repos instead of Adobe's version? If you get a chance search in Synaptic for 'flash' and see if 'flashplugin-installer' is marked as installed. If it is not then you are probably currently using the free version and I would suggest searching this forum for how to remove the free flash and install the real Adobe flash. I am not certain what your problem was in this regard, was it with fspot or facebook or something else? Anyways if it is Facebook you were having trouble with try using Firefox, Chrome still does not have perfect flash support so sometimes things do not work perfectly in Chrome, but in Firefox it should work fine!

...Also if you plan on using Ubuntu or any other Linux distro in the future I would recommend buying/building a computer with an Nvidia card rather than an ATI card as Nvidia, at least currently, has better Linux support. That could perhaps be changing as ATI is working on bettering their Linux support from what I've heard.

---

### Post by ptviperz on 2010-01-07
> **jermza said:**
> I'm back on Windows now, and everything is so much smoother.  I really want to migrate to Ubuntu, but the amount of time I'm spending simply trying to make it work (combined with googling and searching for help) is worrying.

It's tough when you start, everything is different and it can get very frustrating. I can promise you that after you get things figured out, you'll never want to go back. 

Keep pegging away at it!

---

### Post by zkriesse on 2010-01-07
> **jermza said:**
> Correct.  I googled it and that's where I landed up.


What does "Download the Linux x86" mean?  I'll happily do it if I know what I means. :(

Linux x86 is the version for operating systems running 32-bit processing. Linux x86_64 is the version for 64-bit systems...just a little note.

---

### Post by Perturbed Penguin on 2010-01-07
I agree it is overwhelming when you first make the move, there are many things which are done so differently than in Windows. I however also attest to the fact that once you get things figured out more you won't want, you may have to for certain programs, but you won't WANT to go back to Windows. ...and it just keeps getting better in every way! :)

---

### Post by starcannon on 2010-01-07
For your hardware issues, everyone here could probably help a bit more if we had a hardware list.

Please open a terminal:[INDENT]Applications>Accessories>Terminal
[/INDENT]Then please run the following command:
```

sudo lshw -sanitize > ~/Desktop/hardware.odt

```Then please attach that file to a post in this thread. After running that command you will find a file named hardware.odt on your desktop, it will contain a detailed list of your computers hardware.

Give yourself time to learn Ubuntu, a dual boot setup is the best thing to do for starters; after all one needs to get work done during the "how does it work" phase. I also recommend replacing that video card with an nVidia video card, any 6 series or later nVidia card will work much better, and be very easy to install using the hardware driver manager located in *System>Administration>Hardware Drivers*. I hope you don't give up, just dual boot, and take your time. I also encourage you to keep your dual boot system once you know your way around Ubuntu, I think you'll find that from time to time, there will be a Windows-centric application that you want to use, and while there are ways to run Windows applications on Ubuntu, there are times when it is not practical, or possible to do so; so, having windows waiting in the wings is definitely a good idea. For now I'd recommend using Ubuntu in your spare time, learn your way around, use it to surf the web, play some free games, etc...

GL and HF and no matter what OS you use, its all good so long as you can enjoy your computer.

---

### Post by k3lt01 on 2010-01-07
> **jermza said:**
> Correct.  I googled it and that's where I landed up.


What does "Download the Linux x86" mean?  I'll happily do it if I know what I means. :(You really need to know what type of system you have. Starcannon has given you some advice so you can tell us what type of system you have with regards to hardware. Follow his instructions and that will help us to help you. What version of Ubuntu did you download and install, I know it's 9.10 but is it i386 or amd64? If it is i386 then you will need x86 drivers, if it is amd64 then you will need x86_64 drivers.

Now go to [this page]("http://support.amd.com/us/gpudownload/Pages/index.aspx")(also see the attached screenshot) click on the correct version of Linux for your system. Follow the prompts on the page and download the correct driver if it is available. Once you have done that let us know if you need further assistance.

---

### Post by DrMelon on 2010-01-07
The graphics driver, eh? I've always found EnvyNG to be of help here.

```
sudo apt-get install envyng-gtk
```

I think...

---

### Post by buddyd16 on 2010-01-07
For your sound issues have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

My system was experiencing the same issues as you with the volume getting reset to maximum at reboot. After using the equalizer in that thread my systems sound is now more normal. Certain applications still have terrible audio on my end however.

The sound issue seems to be something that is effecting a lot of people. What really confuses me is why they can't have the live cd run the volume at like 50% or less currently all live cd's set volume to max which can potentially ruin peoples speakers.

---

### Post by jermza on 2010-01-10
I'm back in Windows XP for the time being, and it's amazing how much faster my internet browsing is, using Chrome.  It is heaps faster than my Firefox in Ubuntu.  I tried Chrome in Ubuntu, and it's a bit dodgy.

And everything is rendered better in WIndows Chrome.  Fonts are crisper and less funky.

Why is this?  Shouldn't it be better in Ubuntu?

---

### Post by stinger30au on 2010-01-10
> **jermza said:**
> I'm back in Windows XP for the time being, and it's amazing how much faster my internet browsing is, using Chrome.  It is heaps faster than my Firefox in Ubuntu.  I tried Chrome in Ubuntu, and it's a bit dodgy.

And everything is rendered better in WIndows Chrome.  Fonts are crisper and less funky.

Why is this?  Shouldn't it be better in Ubuntu?


depends on your hardware

unfortunately there is a lot of manufacturers that dont fully support linux or support linux at all

on my old rigs i use, ubuntu runs just nicely
my main pc is a pentium 4 HT 3.4 Ghz prescot socket 478 with 2 gig of ram , a 10 gig hdd out of an old xbox for my main boot drive and a 160 gig drive for my data/games/etc and a dvd write and a nvidia fx5500 agp video card

this does me just nicely and ubuntu runs just fine on it

xp runs on it as well, but ubuntu definately feels quicker then xp on this machine for sure

---

### Post by jermza on 2010-01-10
For some reason, my Fifrefox in Ubuntu is having a hard time loading Gmail.  I've been working in Windows all day and Gmail has been fine.  My internet connection is fine.

Even once I've refreshed the page and Gmail loads thereafter, it eventually times out and requests that I go into non-HTML mode.

This is besides the error page showing in huge fonts, which isn't normal either.

Ideas?

---

