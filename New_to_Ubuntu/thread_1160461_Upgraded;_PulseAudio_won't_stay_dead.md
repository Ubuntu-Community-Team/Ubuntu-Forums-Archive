---
title: "Upgraded; PulseAudio won't stay dead"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by AmandaKerik on 2009-05-15
The title covers most of it, but here are the details:

My computer's always had an issue with pulseaudio and killing it became a daily ritual right before I start up Firefox.

Now after upgrading to Jaunty... pulseaudio fights being killed (before I could just killall pulseaudio, now I have to stop it then kill it) and won't stay dead. Unfortunately, I NEED it dead to get any form of sound in flash and the moment I start Firefox pulseaudio restarts itself.

I've fought with this ******* before and nearly borked my computer doing so.

Why would Ubuntu make something like PulseAudio a dependency for ubuntu-desktop? Especially when so many people have problems with it? I thought Linux and Ubuntu were about choice. :(

Please help [-o<

---

### Post by Didius Falco on 2009-05-15
> **AmandaKerik said:**
> The title covers most of it, but here are the details:

My computer's always had an issue with pulseaudio and killing it became a daily ritual right before I start up Firefox.

Now after upgrading to Jaunty... pulseaudio fights being killed (before I could just killall pulseaudio, now I have to stop it then kill it) and won't stay dead. Unfortunately, I NEED it dead to get any form of sound in flash and the moment I start Firefox pulseaudio restarts itself.

I've fought with this ******* before and nearly borked my computer doing so.

Why would Ubuntu make something like PulseAudio a dependency for ubuntu-desktop? Especially when so many people have problems with it? I thought Linux and Ubuntu were about choice. :(

Please help [-o<

Hi,

I think you'll be pleasantly surprised at the advances in Pulse audio that were made in both 8.10 and especially 9.04. Go to this How To and follow it closely. By the time you finish it, you should have the sound working very well, and not need to worry about killing Pulse just to use Flash in Firefox:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working)

I hope this helps...please post back and let us know how it is working.

Regards,

Didius

---

### Post by AmandaKerik on 2009-05-15
I got as far as part 5 in section A

> a@ubuntu:~$ pulseaudio & pavucontrol
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[1] 13904
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[1]+  Exit 1                  pulseaudio

I take it I get to join the pulse-rt group to proceed (doing this now and trying again)

[Edit] I added myself to pulse and pulse-access groups as well

[Edit 2]
> a@ubuntu:~$ pulseaudio & pavucontrol
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[1] 14352
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[1]+  Exit 1                  pulseaudio
a@ubuntu:~$ sudo pulseaudio & pavucontrol
[1] 14365
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

*headdesk*

---

### Post by AmandaKerik on 2009-05-15
A hard reboot later and it's starting up the configuration in step 5 of that how-to and system sounds are working, but flash... nope; silence.

On a tangent, I've found that the latest kernels make my sound card disappear from nearly all options / probes, but an older kernel (what I've set it to use) usually has sound.

So it's an improvement, but still needs work. 

Perhaps it's that Firefox is stuck on Flash 9 despite upgrading my system to flash 10 AND telling it to use the libflashwhatever.so that I unpacked into my /.mozilla/firefox/ folder (in my home folder).

I'd like to get some help straightening that out... ;)

---

### Post by markbuntu on 2009-05-15
Do this to get flash working

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by AmandaKerik on 2009-05-15
> **markbuntu said:**
> Do this to get flash working

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I'll take a look at the link later, but I'm soooo happy atm! I got it working on my own.

I looked for the libflashwhatsits.so in any and all folders relating to mozilla or firefox (long story short: I used to have many different versions of Firefox on my computer for testing of various things I write)

I relogged and it said I didn't have flash installed, so I then grabbed the flash player plugin version 10 (.deb) from the adobe site and installed it, noting it put the libflashwhatsits.so in my .mozilla folder.

I relogged (old XP habit heh) and started up Firefox... I have flash (!) and it's version 10 (!) AND I have sound (!).

So yeah, I'll mark this thread solved and thank you soooo much for the help! :D

On a tangent, will I have to manually update the flash I have installed this way? Can someone tell me where the Ubuntu version of the flash install has the libflashwhatsits.so so I can point Firefox at it?

---

### Post by kansasnoob on 2009-05-15
I agree with Markbuntu! He's done great work!

But I must personally say that I've added Luke Yelavich's PPA's:

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

And I've had no problem since following Markbuntu's instructions or the Jaunty specific steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Didius Falco on 2009-05-16
> **AmandaKerik said:**
> I'll take a look at the link later, but I'm soooo happy atm! I got it working on my own.

I looked for the libflashwhatsits.so in any and all folders relating to mozilla or firefox (long story short: I used to have many different versions of Firefox on my computer for testing of various things I write)

I relogged and it said I didn't have flash installed, so I then grabbed the flash player plugin version 10 (.deb) from the adobe site and installed it, noting it put the libflashwhatsits.so in my .mozilla folder.

I relogged (old XP habit heh) and started up Firefox... I have flash (!) and it's version 10 (!) AND I have sound (!).

So yeah, I'll mark this thread solved and thank you soooo much for the help! :D

On a tangent, will I have to manually update the flash I have installed this way? Can someone tell me where the Ubuntu version of the flash install has the libflashwhatsits.so so I can point Firefox at it?

Glad it all worked out for you in the end! The beswt part is when you figure out something yourself - that's always satisfying!!

So, how's the sound? Personally, the sound in 9.04 was much better to me, once I got it configured properly.

I'll have to have a look at that guide Markbuntu linked. Everything is working fine on mine - except I can't get the comedy Central (Daily Show and Colbert Report) to work - it won't even load the videos. I still have an 8.10 setup, and it plays those sites perfectly, but no-go on my 9.04.

I'll get around to it - too much going on to bother with it at the moment.

Regards,

Didius

---

### Post by markbuntu on 2009-05-16
I watch the Daily Show at Hulu myself.

---

### Post by juanspeed on 2009-06-14
So up until today my sound in 9.04 had worked better than it ever had. Executed my daily "sudo apt-get update" and low and behold there was a new firefox update. And I proceeded to update it. That was the the last time sound worked on my system. I followed the set of instructions numerous times listed here: 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) 
Running 9.04 btw, upgraded from 8.10 about 2 months ago.

Part A Section 1
Results:
juanspeed@villin:~$ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
[sudo] password for juanspeed: 
rm: cannot remove `/home/juanspeed/.asound*': No such file or directory
rm: cannot remove `/etc/asound.conf': No such file or directory
juanspeed@villin:~$ 

Moving along. The rest of the steps went accordingly. Everything was pretty much set up properly, though after earlier tinkering I was getting the "connection refused error" 

Manually ran the "pulseaudio & pavucontrol" from prompt and received
juanspeed@villin:~$ pulseaudio & pavucontrol
[1] 4982
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

At this point I did a hard reboot logged back in and was able to launch Pulse Volume Control, it began to load for a split second and then only showed mono options and nothing pertaining to ALSA. The ALSA options flashed for a minute and then defaulted to what appears to be a degraded sound setup with no sound once again. I am still in the process of capturing more details however I am really fed up, like ready to throw my laptop at something. More a thought than an action.

The most frustrating thing was I so impressed with how decent the sound was. It was really terrible for a while. Sometimes I'll run movies off of this 1330 to our LCD and you have to crank the volume way up on the stereo and it crackles. Especially on the laptop itself. The sound has been extremely lackluster under any linux distro. Though for the last 2 weeks it had been rock solid. That is, until today.

Any thoughts? I have followed about 8 different manuals today all retracing my steps to put back whatever I had changed. At one point OSS actually worked when everything else bombed out.

best,

Keefer

---

