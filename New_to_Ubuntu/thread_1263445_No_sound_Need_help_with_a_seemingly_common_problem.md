---
title: "No sound: Need help with a seemingly common problem"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by cguwilliams on 2009-09-11
Hey there community,

I, like most here, am pretty new to Linux and Ubuntu. I use 8.10 at work and have just installed 9.04 on my Dell at home. Actually, I ordered the machine specifically for Linux, though if I had researched it more, I wouldn't be having this problem now. Anyway, on to my question.

Originally my machine came with Windows Vista preinstalled. I had no interest in this operating system, so I installed Fedora 11, just to see if I would like it as much, or better, than Ubuntu. I didn't, so I switched to Ubuntu (as I said, I use it at work).

Now my problem is that the sound on my system worked in Fedora, but doesn't work in Ubuntu. I have two sound cards, apparently, as evidenced by lspci -v. I won't post the whole output, but here it is for the two 'audio' entries:

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Dell Device 02ac
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at fe7f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
	Subsystem: ATI Technologies Inc HD48x0 audio
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fe8ec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

Now, I have tried a lot of things to fix this problem, from various google searches and forum posts, but nothing has worked. Unfortunately I did not keep a record of my attempts, but I have reinstalled a couple of times. My latest attempt to fix it involved downloading the latest drivers from the ATI website, and installing it according to their instructions. Doing so set me back more than it moved me forward. That is, the command 'aplay -l' used to display an ALC888 driver, whereas now it gives me the following message, "aplay: device_list:217: no soundcards found...".

Well, that's my problem. No sound and no idea how to fix it. It really just seems like a driver problem, as it worked fine in Fedora. Please lend a hand if you will. I will be happy to paste any output here that you may need to further diagnose (and hopefully to help fix) my sound problem.

--Patrick

---

### Post by cguwilliams on 2009-09-11
Bump?

---

### Post by ankspo71 on 2009-09-11
Hi,
I'm not too experienced with technical things about linux yet, but many new ubuntu users (myself included) have had trouble with the sound mixer channel volumes being set too low. If you haven't done so already, click on your volume control button on the top panel (taskbar). Next, after it opens, click on the button that that says "volume control". Here you can adjust your channel volumes and select which sound mixer works best for you. I believe the lastest Fedora is using PulseAudio, so you might want to try that if ALSA doesn't work for you.
Hope this helps.
James

---

### Post by cguwilliams on 2009-09-11
Thanks for your suggestion. I had tried that before I tried updating ALSA. For now I am backing up my files and am going to reinstall for a fresh start. I'll update then.

---

### Post by mangurt on 2009-09-11
Try turning off your sound card that is on your motherboard off via bios.  I had the same problem with my tower, and once I did that, I had no problem.

---

### Post by cguwilliams on 2009-09-11
Well, after a clean install, and after switching to PulseAudio Mixer for playback, I didn't see any results (or hear them for that matter). I also tried turning off sound in bios (F2 to enter setup at startup). I'm still not hearing anything.

the aplay -l command now gives the following output:

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Patrick

---

### Post by ankspo71 on 2009-09-11
Hi Again,
I have another thought.
> I have two sound cards, apparently, as evidenced by lspci -v.
I see you just learned that you have 2 sound cards.

Do you have your speakers plugged into the right sound card that Ubuntu is trying to use? This is only a wild guess, but I think your ATI card plugins are towards the bottom of your tower in the expansion slots. If you can't get any sound from one sound card, plug your speakers into the other and see what happens.
James.

---

### Post by cguwilliams on 2009-09-11
That's an excellent theory. Unfortunately, it didn't work.

There are six possible places to plug the speakers into, all arranged in a rectangle, with three inputs on one row, and three on a bottom row... Basically, like this:
 _ _ _
|0|0|0|
 _ _ _
|0|0|0|

These are placed right above where my monitor plugs in.

I tried all six (yes, even the one with the microphone icon), with both the Alsa sound option and with the PulseAudio option under Volume Control, while playing a random YouTube video in FireFox. None of the slots worked in either mode. Each input has a different color to it and the icons are each slightly different. One looks like it is for a back and front speaker, one looks like it is left channel, another for a right channel, etc... The one that worked with Fedora 11 was the one that matched colors with the speaker plug (green).

I also now have the audio turned back on under BIOS, so my 'aplay' looks different:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thank you again for your help. I won't give up!

Patrick

---

### Post by ankspo71 on 2009-09-11
Hi,
According to my lspci -v output, it looks like neither of your sound cards are enabled. See the red line in my output below.

> **cguwilliams said:**
> 

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Dell Device 02ac
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at fe7f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
	Subsystem: ATI Technologies Inc HD48x0 audio
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fe8ec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel



My output for a single sound card computer:

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: Biostar Microtech Int'l Corp Device 8218
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	**[COLOR="Red"]Kernel driver in use: HDA Intel[/COLOR]**
	Kernel modules: snd-hda-intel

Hopefully someone with more technical skills will jump in here and know what's wrong. I just thought this little bit of info might help somehow.
James.

---

### Post by cguwilliams on 2009-09-11
Wow, that's actually really interesting. I'll start digging around to see if I can get it activated.

edit: I ran 'killall pulseaudio' and 'pulseaudio -vvv' and got this output. I hope it might help in pinpointing my problem.

:~$ pulseaudio -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: nosudo
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is df48647235a35018e08eca404aaa7857.
I: main.c: Using runtime directory /home/patrick/.pulse/df48647235a35018e08eca404aaa7857:runtime.
I: main.c: Using state directory /home/patrick/.pulse.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

I'll keep looking and trying stuff. Thanks again for your help!

Patrick

---

### Post by ankspo71 on 2009-09-11
Hey Patrick.
I just found this link. It looks very useful.
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
James.

---

### Post by cguwilliams on 2009-09-11
Great thanks. I'm currently installing a ton of packages based ([this post here]("http://ubuntuforums.org/showthread.php?t=1130384")), and it sounds pretty promising. Again, I'll update when I have something to update.

Edit: Great news, well, sorta... I know the sound is almost working. I followed the instructions on the list I linked to above and now, in volume control, when I play a streaming radio station, via Rythmbox Music Palyer I get activation in my Output Devices panel of Volume Control. The bad news is that I still have no actual sound coming out of my speakers... So, I'm not out of the woods yet :(

Patrick

---

### Post by cguwilliams on 2009-09-12
The problem seems to be with Alsamixer. Both the CL alsa mixer, as well as Gnome-alsamixer come up blank... Anyone know of a solution to this problem? Pulseaudio is showing sound output, there is no sound coming out of the speakers, and alsamixer is just an empty applet.

Patrick

---

### Post by cguwilliams on 2009-09-12
The problem seems to be with Alsamixer. Both the CL alsa mixer, as well as Gnome-alsamixer come up blank... Anyone know of a solution to this problem? Pulseaudio is showing sound output, there is no sound coming out of the speakers, and alsamixer is just an empty applet.

Patrick

---

### Post by cguwilliams on 2009-09-12
The solution was to add the line:

options snd-hda-intel probe_mask=1 model=6stack-dell

to:

/etc/modprobe.d/alsa-base.conf
-------------------------------

So anyway, if anyone else has a Dell Studio Desktop 540, that is the solution.

How do you add [solved] to a thread?

---

### Post by ankspo71 on 2009-09-12
Hi Patrick,
Hmm, I think you go to your original post click on "thread tools" at the top of the post, then select "mark as solved". I can't see it from here, so I'm going by memory. You'll find it though.

I'm glad you got the problem fixed.
James

---

### Post by ch604 on 2009-10-23
sorry to bump a solved thread, but how did you discover exactly which model to put into that particular line, patrick?

thanks,
AJ

---

### Post by cguwilliams on 2009-10-23
Well, I had to look up my machine specs on the Dell-website. For the Dell Studio that I have, the model happens to be 6Stack-dell. There is a list of different possible models that you can put in that particular line.

I am looking for the list that I took the model from. I believe it was in a stickied post, or in a link from a stickied post. When I find it, I will append it to this reply. One method, with the list, is to just try all the models that you think might work. I got lucky in that there were only two "Dell" models, and I think I tried the right one first.

Patrick

---

### Post by Rayve on 2009-10-31
Here is the thread with the make/model list for entries in the alsa-base.conf file: 
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by cguwilliams on 2009-10-31
Yup! That looks like the same source I used. Next time I solve an issue with my computer, I'll be sure to keep better track of my resources :D

I hope this resolves your sound issues.

Patrick

---

