---
title: "Laptop speaker problem"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by sweb on 2009-11-09
Hello,
I have a dell vostro 1520. I have no sound but when I plug my headphones in there is sounds. how do I get my speakers to work. nothing is muted. :(

---

### Post by ctdahle on 2009-11-29
I have this same problem.

I am running Karmic Koala on a Hewlett Packard G-61 laptop. The earphones work fine, but there is no sound from the built-in speakers. 

From other searches I have learned how to use terminal to access and adjust settings in alsa mixer. I followed a very carefully documented process of changing all of the settings and levels but to no avail.

I have seen this problem referenced in a number of places as affecting machines running both Jaunty and Karmic and the the advice to max out all of the settings in alsa mixer seems to work for SOME new linux users, but not for me.

I have double checked that the speakers work when I load that "other" operating system.

I ran a couple of searches here for solutions but was not successful at finding a solution, so I sure would appreciate any guidance I can get here.

Music from the computer puts my little ones to sleep at night, so I am feeling a bit pressed to get this figured out!

---

### Post by ctdahle on 2009-11-30
To recap: Sound plays through the headphone jack, but the onboard speakers do not play sound at all. Not on startup or login, and not through any application such as rythmbox or movie player.

I've now spent a few hours on this, but no success. I have discovered that it is a fairly common problem on a wide variety of laptop computers running both Jaunty and Karmic.

I have tried adjusting alsamixer settings from a terminal and using several of the available alsamixer gui utilities.

I have verified working speakers by loading a different operating system.

I have read a few threads that suggest throwing lines of code at the problem, but none of them ended with the original poster reporting that the problem was solved. Absent an original poster's report that she tried step x, then y, then z and had success, I'm reluctant to start sending commands from the terminal without understanding what the problem is or what the commands are supposed to do.

I am immediately skeptical of any proposed solution that includes forced commands to remove files and directories...

Anyway, I keep trying...

---

### Post by John Bean on 2009-11-30
[FONT=Arial]Adding the line[/FONT] *[FONT=Lucida Console]options snd-hda-intel model=laptop[/FONT]* to the end of /etc/modprobe.d/alsa-base.conf worked for me.

---

### Post by .xX Weedle420 Xx. on 2009-11-30
How do the edit the file? i searched for it, found it and when i try saving it i get a error saying "Could not save the file /etc/modprobe.d/alsa-base.conf. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by Geoff918 on 2009-11-30
> **.xX Weedle420 Xx. said:**
> How do the edit the file? i searched for it, found it and when i try saving it i get a error saying "Could not save the file /etc/modprobe.d/alsa-base.conf. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

The only directory *you* can edit anything in is your home directory.

What you'll need to do is the following:

sudo [whatever editor] /etc/modprobe.d/alsa-base.conf

I personally use vi or nano in the [whatever editor]. You may find nano easier than learning some of the multimodal commands in vi.

or, alternately you could:

Alt-F2 gksudo gedit /etc/modprobe.d/alsa-base.conf

that's pretty simple there and you don't have to brave the CLI or learn old editors.

One side-note, this works for Jaunty and previous. Karmic seems to have moved completely to pulse audio, I'm pretty sure?

---

### Post by ctdahle on 2009-11-30
Thank you John and Geoff. This finally looks like something promising. I've found the file and I have a general idea of what your instructions are intended to do and how to undo it if it doesn't go right. I see that to edit ../../alsa-base.conf, I need the powers of root, ergo the use of sudo.

John, I wonder if the "intel" in the options code is generic for PCs or if I need to change anything because I have an AMD processor. I assume the former, but let me know if I am wrong.

I need to play with vi and emacs a bit before I actually try to edit any system files.

I'm kind of glad that this isn't just a simple "tick the box" problem. gives me an opportunity to dive in and really get a better understanding of how the system works. I *want* to learn my way around the command line actually.

I'll check in later and let y'all know how it goes.

---

### Post by ctdahle on 2009-11-30
OK, I am way too brain dead to work my way through vi or emacs, so I am wondering...admitting that this is the wimpy way out, can I just open the .conf file from within gedit, authenticate at the prompt, then paste in the line and save...?

What the heck, I'm going to try it.

I can always just reinstall the whole works right!!??

---

### Post by ctdahle on 2009-11-30
OK, I get a password prompt to open the file, but I see that it opens read only and I don't have permission to save. Have to explore to see if I can execute superuser powers from the gui.

Must...face...my...fear of the command line...

---

### Post by ctdahle on 2009-11-30
[FONT=Arial]Darn...I thought I had it...

I figured out what gksudo does, and why I needed to hit [Alt-F2] so I opened a terminal window and hit Alt-F2.

At the prompt I entered [I] gksudo gedit /etc/modprobe.d/alsa-base.conf

[/I]The password prompt came up and after I entered my root password, the file opened. I added *options snd-hda-intel model=laptop *[/FONT][FONT=Lucida Console][FONT=Arial]to the end of the file and successfully saved it.

I rebooted and heard the drumbeat in the headphones and then pulled the plug during the chord. No dice. Still get sound from the headphones but not from the laptop's built in speakers. Ran a couple of audio files just to be sure.

So, sound problem remains, but at least I know how to edit system files now.

I'm going back in to remove the [/FONT][/FONT]*[FONT=Lucida Console]options snd-hda-intel model=laptop [/FONT]*[FONT=Arial]line just to put everything back to the starting point.

Anyway, thanks for the suggestions. Any other ideas?


[/FONT]

---

### Post by sandyd on 2009-11-30
welcome to the world of bugs
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)

---

### Post by sandyd on 2009-11-30
> **sweb said:**
> Hello,
I have a dell vostro 1520. I have no sound but when I plug my headphones in there is sounds. how do I get my speakers to work. nothing is muted. :(
and although your laptop isnt a hp one... try here....
[http://ubuntuforums.org/showthread.php?t=1182242](http://ubuntuforums.org/showthread.php?t=1182242)

---

### Post by ctdahle on 2009-11-30
Uh...thanks Carlee...I think. My very little brain hurts...Looks like John is right that I need to modify alsa-base.conf, but with a slightly different line than what John suggests.

I am glad to see that the linux community recognizes this as some sort of bug and that it's not just a result of some personal flaw on my part.

Remind me again...this is fun...right?

Anyway, I appreciate everything so far. Even though I don't have it figured out yet, I do feel like I am moving in the direction of a solution, and learning a lot about Gnu/Linux and Ubuntu in the process.

Great people, great community, and despite this bug, great OS too.

Cheers,

Chris

---

### Post by Thanh-BKK on 2009-11-30
Hi.

So i am adding myself here, too (own thread [http://ubuntuforums.org/showthread.php?p=8417452#post8417452](http://ubuntuforums.org/showthread.php?p=8417452#post8417452)) with the identical problem (sound only from headphone jack) on a Compaq Presario CQ 40-514AU.

When i do the "cat /proc/asound/cards" i get two choices:

0 [SB         ]: HDA-Intel - HDA ATI SB
                 HDA ATI SB at 0x92500000 irq 16
1 [HDMI       ]: HDA-Intel - HDA ATI HDMI
                 HDA ATI HDMI at 0x92410000 irq 19

So what exactly am i supposed to append to /etc/modprobe.d/alsa-base.conf? I have already tried the ones found on the other linked sites however nothing worked.

My laptop has an AMD Athlon 64 processor and an ATI Radeon 3200 graphics card in case that matters. Running Jaunty 9.04 fully updated as of today. 

Kind regards......

Thanh

---

### Post by sandyd on 2009-11-30
> **Thanh-BKK said:**
> Hi.

So i am adding myself here, too (own thread [http://ubuntuforums.org/showthread.php?p=8417452#post8417452](http://ubuntuforums.org/showthread.php?p=8417452#post8417452)) with the identical problem (sound only from headphone jack) on a Compaq Presario CQ 40-514AU.

When i do the "cat /proc/asound/cards" i get two choices:

0 [SB         ]: HDA-Intel - HDA ATI SB
                 HDA ATI SB at 0x92500000 irq 16
1 [HDMI       ]: HDA-Intel - HDA ATI HDMI
                 HDA ATI HDMI at 0x92410000 irq 19

So what exactly am i supposed to append to /etc/modprobe.d/alsa-base.conf? I have already tried the ones found on the other linked sites however nothing worked.

My laptop has an AMD Athlon 64 processor and an ATI Radeon 3200 graphics card in case that matters. Running Jaunty 9.04 fully updated as of today. 

Kind regards......
etc/modprobe.d/alsa-base.con
Thanh
did you try this one? (restart after)
```

sudo echo "options snd-hda-intel model=hp-m4 enable_msi=1" >> /etc/modprobe.d/alsa-base.conf

```
or did you already list that.
p.s. could you tell me which linked sites you tried?
theirs a MILLION linked sites currently. theirs some in the links i gave, their some wandering in google....

---

### Post by ctdahle on 2009-12-01
[COLOR=Purple][SIZE=6]Thank You Carlee, John and Geoff!
[COLOR=Black][SIZE=2]Adding the line [/SIZE][/COLOR][/SIZE][/COLOR]
options snd-hda-intel model=hp-m4 enable_msi=1[COLOR=Purple][SIZE=6][COLOR=Black][SIZE=2] to /etc/modprobe.d/alsa-base.conf solved the problem

Carlee, In the line of code you posted, I don't understand why you added the "echo" command. I just did "gksudo gedit" and the file name after Alt-F2 in the terminal, and then edited the last line to put in the "model=hp..." language.

Could I have just typed all of that in at a terminal...is that the reason for echo ing back to the terminal?

Its not that I don't trust you guys, it's just that I feel this compulsion to understand what every command is going to do before I enter it.

Anyway, I am now almost completely satisfied with my new linux installation. I just have a few little irritating things to clean up, water spots on the windshield, rather than bugs, but nothing left that prevents me from using the machine with all the basic utility I expect.

Really, you folks are great and I haven't enjoyed having a new computer this much since I bought my first one in 1989.

Cheers,

Chris
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by ndefontenay on 2009-12-01
hello,

the echo at the beginning will display the line on the terminal. Then the >> at the end will write the line to the files specified after like this:

echo "I can write anything here" >> /home/nico/anyfilename

this will write "I can write anything here" to a new file called anyfilename in my home folder.

If the file already exists, it will append.

I have the sound problems too. I don't have an internet connection at the moment.

I have a sound card detected but no sound whatsoever, including in headphones : (

It's an intel card.

---

### Post by ctdahle on 2009-12-01
Oh, so it would have appended the text in quotes to the end of the ....conf file. Good shortcut to know...if I can manage to remember it.

Neat how there are so many different ways of doing things, and that things I remember from 30 years ago when I was a kid playing with the school district's UNIX system, still work.

What I hate about that other OS, is that just about the time I became comfortable with a particular way of doing things, they would change everything.

Coolest thing about Linux is that even if it screws up, fixing it is fun.

Thanks.

---

### Post by sandyd on 2009-12-01
> **ndefontenay said:**
> hello,

the echo at the beginning will display the line on the terminal. Then the >> at the end will write the line to the files specified after like this:

echo "I can write anything here" >> /home/nico/anyfilename

this will write "I can write anything here" to a new file called anyfilename in my home folder.

If the file already exists, it will append.

I have the sound problems too. I don't have an internet connection at the moment.

I have a sound card detected but no sound whatsoever, including in headphones : (

It's an intel card.
just dont do it with only one ">"
learned the hard way after i wiped my /etc/apt/sources.list after doing that......

anyways,
it seems to be a collection of problems. theirs a bug report right........ here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/297864](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/297864)

and heres a nice stack for refrence....
[http://ubuntuforums.org/showthread.php?t=1088053](http://ubuntuforums.org/showthread.php?t=1088053)
[http://ubuntuforums.org/showthread.php?t=729859](http://ubuntuforums.org/showthread.php?t=729859)
[http://ubuntuforums.org/showthread.php?t=780029](http://ubuntuforums.org/showthread.php?t=780029)
[http://ubuntuforums.org/showthread.php?t=1199872](http://ubuntuforums.org/showthread.php?t=1199872)
[http://ubuntuforums.org/showthread.php?t=465054](http://ubuntuforums.org/showthread.php?t=465054)
[http://ubuntuforums.org/showthread.php?t=384512](http://ubuntuforums.org/showthread.php?t=384512)
[http://ubuntuforums.org/showthread.php?t=465422](http://ubuntuforums.org/showthread.php?t=465422)
[http://ubuntuforums.org/showthread.php?t=351079](http://ubuntuforums.org/showthread.php?t=351079)
[http://ubuntuforums.org/showthread.php?t=306488](http://ubuntuforums.org/showthread.php?t=306488)
[http://ubuntuforums.org/showthread.php?t=254027](http://ubuntuforums.org/showthread.php?t=254027)
[http://newyork.ubuntuforums.org/showthread.php?p=8188107](http://newyork.ubuntuforums.org/showthread.php?p=8188107)
[http://ubuntuforums.org/showthread.php?t=220854](http://ubuntuforums.org/showthread.php?t=220854)
[http://ubuntuforums.org/showthread.php?t=495330](http://ubuntuforums.org/showthread.php?t=495330)
[http://ubuntuforums.org/showthread.php?t=323675](http://ubuntuforums.org/showthread.php?t=323675)
[http://ubuntuforums.org/showthread.php?t=1196386](http://ubuntuforums.org/showthread.php?t=1196386)
[http://ubuntuforums.org/showthread.php?t=841255](http://ubuntuforums.org/showthread.php?t=841255)
[http://ubuntuforums.org/showthread.php?t=41426](http://ubuntuforums.org/showthread.php?t=41426)
[http://ubuntuforums.org/showthread.php?p=8423606](http://ubuntuforums.org/showthread.php?p=8423606)
[http://ubuntuforums.org/showthread.php?t=967722](http://ubuntuforums.org/showthread.php?t=967722)

might also wanna take look at 
[http://ubuntuforums.org/showthread.php?t=305712](http://ubuntuforums.org/showthread.php?t=305712)
[http://ubuntuforums.org/showthread.php?t=701776](http://ubuntuforums.org/showthread.php?t=701776)

my vostro laptop has the same problem and it was a good thing that that laptop was mine, not my employers....

---

### Post by Thanh-BKK on 2009-12-01
Hi.

Many thanks for the help!!

This "options snd-hda-intel model=hp-m4 enable_msi=1" did the trick, i do now have sound from the speakers AND from thge headphgones (and it mutes the speakers, too, when i plug in the headphone).... however for a trade!

Because now my keyboard-volume-control does not work anymore :..(

I can regulate the volume with mouse/touchpad by opening the sound control thingy, however regardless what mixer or options i try, the keyboard does not work anymore. It still slides the slider however the volume does not respond.

I guess i can live with that but it is still annoying (but better than no sound!)

Is there a solution for that problem, too..?

Kind regards......

Thanh

EDIT please disregard this message... i found the solution for THAT just one minute after writing the message.... changing the "default mixer tracks" in System-Preferences-Sound to "HDA ATI SB (Alsa Mixer)" did it :)

---

### Post by John Bean on 2009-12-02
> **ctdahle said:**
> [COLOR=Purple][SIZE=6][COLOR=Black][SIZE=2]Adding the line [/SIZE][/COLOR][/SIZE][/COLOR]
options snd-hda-intel model=hp-m4 enable_msi=1[COLOR=Purple][SIZE=6][COLOR=Black][SIZE=2] to /etc/modprobe.d/alsa-base.conf solved the problem
[...]
Really, you folks are great and I haven't enjoyed having a new computer this much since I bought my first one in 1989.
[/SIZE][/COLOR][/SIZE][/COLOR]

Glad you got it sorted Chris :-)

---

### Post by DaveHi on 2010-01-01
Just like to add my thanks to Carlee.

Brought a HP G61 for my Parents and have persuaded them to let me install Ubuntu, but, when speakers wouldn't work got that sinking feeling. Never did solve sound problems in 9.04.

Anyway anyone with no sound from speakers, but working headphones, on a HP G61 follow Carlee's instructions. worked for me. Well followed gksudo gedit route, same result.

Cheers

---

### Post by Nerdfest on 2010-02-14
Thanks for the tips for the sound fix.  I recently picked up one of these laptops as well, and am left with 2 problems. The first is that upon resume, I get the num-lock and caps-lock leds flashing. This actually only happens when it resumes from suspending overnight. When it suspends for just a few minutes, it resumes just fine.  the HP site describes the conditions (LEDs flashing twice) as a BIOS corruption error. I actually nave to unplug the laptop and remove the battery to start it up again.  The other remaining problem is the webcam. It works, but can only seem to grab about 1 frame every 5 seconds. I can get it to work at about 5 frames/second in 320x240 mode.  Anyone have any ideas on either of these 2 problems?

---

