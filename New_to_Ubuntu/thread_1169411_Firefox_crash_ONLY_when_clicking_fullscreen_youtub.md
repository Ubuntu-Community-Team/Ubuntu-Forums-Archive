---
title: "Firefox crash ONLY when clicking fullscreen youtube"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by VitaminBB on 2009-05-25
My firefox crashes every single time I click the fullscreen button on youtube.

The fullscreen function used to work and I have not installed any recent plugins.

ideas?

---

### Post by VitaminBB on 2009-05-26
help? anyone there?

---

### Post by SKYDOS_2 on 2009-05-26
> **VitaminBB said:**
> help? anyone there?

try to reinstall it
i ad such problem too

---

### Post by zeroseven0183 on 2009-05-26
> **VitaminBB said:**
> My firefox crashes every single time I click the fullscreen button on youtube.

The fullscreen function **used to work** and I have not installed any recent plugins.

ideas?

What was your last action before this issue happened? Can you recall?

---

### Post by VitaminBB on 2009-05-26
> **SKYDOS_2 said:**
> try to reinstall it
i ad such problem too

Tried that, tried the non-free and the official flash, both had the same problem.

---

### Post by VitaminBB on 2009-05-26
> **zeroseven0183 said:**
> What was your last action before this issue happened? Can you recall?

I have a nagging suspicion that the upgrade to 9.04 has done this but as I dont fullscreen all the time its not something I immediately noticed but that would be the last big change that happened.

---

### Post by Pappy1911 on 2009-05-27
FWIW, I have the same problem with my 8.04 and another site. Work around is to leave that site on and close down after other sites are finished.

---

### Post by VitaminBB on 2009-05-27
> **Pappy1911 said:**
> FWIW, I have the same problem with my 8.04 and another site. Work around is to leave that site on and close down after other sites are finished.

Not sure what your saying here ...

---

### Post by Pappy1911 on 2009-05-27
> **VitaminBB said:**
> Not sure what your saying here ...

There are several trouble sites that I visit that will shut down FF when I close them.

When I have several other good sites open at the same time, closing one of the trouble sites will crash FF.

For example, site A is a bad one. I can open B,C,D, etc. and if I close A, all will go down. So, I close B,C etc. and A last.

FF lets me restore all sites upon re-starting.

My work-around is to close the good sites first and the trouble sites last.

I saw a similarity with the OP and my experience.

---

### Post by VitaminBB on 2009-05-27
> **Pappy1911 said:**
> There are several trouble sites that I visit that will shut down FF when I close them.

When I have several other good sites open at the same time, closing one of the trouble sites will crash FF.

For example, site A is a bad one. I can open B,C,D, etc. and if I close A, all will go down. So, I close B,C etc. and A last.

FF lets me restore all sites upon re-starting.

My work-around is to close the good sites first and the trouble sites last.

I saw a similarity with the OP and my experience.

Thanks for the reply but I think we are talking about two different things.

My problem is when I click MAXIMIZE on a youtube video my FF crashes, thats it.

So your suggestion might work if there was an entire website that crashed FF when I closed its tab but it doesnt apply to my particular situation.

---

### Post by Pappy1911 on 2009-05-27
Don't know...just thought there may be a relationship here....

---

### Post by VitaminBB on 2009-05-28
Thanks for the idea, the problem has me baffled but im sure someone else must have had the same problem.

---

### Post by chiques on 2009-06-12
I have Jaunty 9.04 and I have the exact same problem. Watching youtube videos in default mode is no problem. When I click on "full screen" it simply closes firefox without any prompts. 

I spoke to the ubuntu irc channel people and one of them recommended it might be the flash plug in which enable videos to be watched in firefox. Basically it might be a problem with Adobe Flash Player. ;)

---

### Post by VCoolio on 2009-06-19
[Solved]("https://bugs.launchpad.net/firefox/+bug/333127"): load the flash plugin before firefox or swiftfox. It's a NVidia driver issue. (edit: not only... ATI users seem to benefit from this too).
Easiest fix: modify the startup script of your browser, e.g. in case of Minefield (firefox-3.6):

gksudo gedit /usr/lib/firefox-3.6a1pre/firefox.sh

Find your browser script in the same area, somewhere in /usr/lib/yourbrowser; (edit: other possible locations are like /usr/local/lib/firefox-3.5/firefox or for install with ubuntuzilla it is /opt/firefox/firefox; using a run-mozilla.sh file if that is available also seems to work);
then add as 2nd (NOT 1st) line:
```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

I'm not sure if this will keep working after an update of the browser (then do it again). 

This doesn't seem to work for 64-bit; you'll need to rightclick flash video and disable hardware acceleration (thx [Garyhans]("http://ubuntuforums.org/showpost.php?p=7632563&postcount=43")). 

If you now have the problem that when you press full screen in youtube you see your compiz animation for opening a window, it very briefly shows video full screen (less than a second) and then the full screen window closes, then do the following (thx [Danbo19]("http://ubuntuforums.org/showpost.php?p=7612932&postcount=41")): in compiz config settings manager go to Effects > Animation > Open Animation  > Add and add "!(name=firefox)" (without "", but with !).
###########
SCRIPT OPTION
###########
If this doesn't work or you don't like this solution try the following:
I couldn't get it done in a launcher command but I used the script option (copypaste in gedit and save):

```
#!/bin/sh
## replace firefox-3.6 with what you use, e.g. firefox, firefox-3.5, swiftfox
LD_PRELOAD=/usr/lib/libGL.so.1 firefox-3.6
```

or when you run from an extracted tarball:

```
#!/bin/sh
export LD_PRELOAD=/usr/lib/libGL.so.1
/path/to/firefox
```

Now to run your browser make a launcher with as a command:
sh /path/to/script

---

### Post by jmdsdf on 2009-06-22
Adding:

export LD_PRELOAD=/usr/lib/libGL.so.1

To the second line of /usr/lib/firefox-3.5/firefox.sh worked perfectly with the latest release candidate of Firefox! A big thank you! I was sick of using the Compiz enhanced zoom feature as a work around. Again, thanks!

---

### Post by ankle on 2009-06-24
Finally! Thanks VCoolio.

(BTW, I have ATI, not nVidia, but still had this problem until now)

---

### Post by infoaddicted on 2009-06-30
Thanks VCoolio!  That worked for me!):P

---

### Post by el-mar01 on 2009-07-02
Thanks a lot VCoolio, its unbeleivable that Mozilla didn't pick this HUGE bug up during development, come on Mozilla !! people use Firefox on other platforms other than Windows !!

---

### Post by lovinglinux on 2009-07-02
> **VCoolio said:**
> [Solved]("https://bugs.launchpad.net/firefox/+bug/333127"): load the flash plugin before firefox or swiftfox. It's a NVidia driver issue. (edit: not only... ATI users seem to benefit from this too).
Easiest fix: modify the startup script of your browser, e.g. in case of Minefield (firefox-3.6):

gksudo gedit /usr/lib/firefox-3.6a1pre/firefox.sh

Find your browser script in the same area, somewhere in /usr/lib/yourbrowser;
then add as 2nd (NOT 1st) line:
export LD_PRELOAD=/usr/lib/libGL.so.1

I'm not sure if this will keep working after an update of the browser (then do it again). 

If this doesn't work or you don't like this solution try the following:
I couldn't get it done in a launcher command but I used the script option (copypaste in gedit and save):

```
#!/bin/sh
## replace firefox-3.6 with what you use, e.g. firefox, firefox-3.5, swiftfox
LD_PRELOAD=/usr/lib/libGL.so.1 firefox-3.6
```

or when you run from an extracted tarball:

```
#!/bin/sh
export LD_PRELOAD=/usr/lib/libGL.so.1
/path/to/firefox
```

Now to run your browser make a launcher with as a command:
sh /path/to/script

I don't have /usr/lib/firefox-3.5/firefox.sh

I have compiled Firefox and it was installed at /usr/local/lib/firefox-3.5 and there is no firefox.sh there. The only similar file available is plain firefox, but it doesn't work. Do you how do I find it or if this can be done another way?

---

### Post by VCoolio on 2009-07-02
search in /usr/bin or try the script option I gave as alternative.

---

### Post by hamidoo on 2009-07-02
Many thx man!
It worked with Mozilla's Firefox 3.5 tar ball (the one downloaded from mozilla).
I just added the line:
```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

after the line:
```
moz_libdir=/usr/local/lib/firefox-3.5
```

And it worked like a charm!

---

### Post by lovinglinux on 2009-07-02
> **hamidoo said:**
> Many thx man!
It worked with Mozilla's Firefox 3.5 tar ball (the one downloaded from mozilla).
I just added the line:
```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

after the line:
```
moz_libdir=/usr/local/lib/firefox-3.5
```

And it worked like a charm!

Thank you. That worked like a charm for me too.

---

### Post by sdowney717 on 2009-07-03
simply for 3.5 did this
gksudo gedit /usr/lib/firefox-3.5/firefox.sh

added line 

```
MOZDIR=$HOME/.mozilla
LIBDIR=/usr/lib/firefox-3.5
export LD_PRELOAD=/usr/lib/libGL.so.1
APPVER=3.5
META_NAME=
GDB=/usr/bin/gdb
DROPPED=abandoned
```

---

### Post by grindboy on 2009-07-04
Thanks the script version worked perfectly :-)

---

### Post by Danbo19 on 2009-07-08
This *almost *worked for me. Both the gedit and script options fixed the crashing anyway. However, now when I press full screen in youtube I see my compiz animation for opening a window, it *very* briefly shows video full screen (less than a second) and then the full screen window closes.

I'd like to be able to see youtube videos in full screen but, at least it won't crash Firefox anymore...

---

### Post by mac-duff on 2009-07-08
Hi,

I ve updated Firefox with the ubuntuzilla installer and I can not find the firefox.sh because a folder in /usr/lib/firefox-3.5 does not exist.

Can someone confirm this

Thx

---

### Post by VCoolio on 2009-07-08
@ mac-duff: what you mention IS the folder in which the firefox file could be stored. Check for one of these:
/usr/lib/firefox-3.5/firefox.sh
/usr/local/lib/firefox-3.5/firefox.sh
/opt/firefox-3.5/firefox.sh

@ Danbo19: in compiz-config settings manager click the animations plugin and edit the animations to skip firefox. Add something like 
!(name=firefox)
Maybe it needs to be !(name=firefox-3.5), but you'll figure it out. Or add an animation setting for firefox that doesn't give problems with flash. I use Glide1 if it's any help. Good luck with it.

---

### Post by mikedomo on 2009-07-09
I fixed this problem in my firefox 3.5 i will publish it in othe web sites, you go ahead!

---

### Post by mac-duff on 2009-07-09
Hi VCoolio

thx for the quick answer, unfortunately I only find the firefox.sh file once, this is in the firefox.3.0.11 folder so I dont know real which I have to edit instead but I am sure that I am using 3.5 and u r right, the installation is in this folder /opt/firefox-3.5 but sadly without the file

cu

---

### Post by VCoolio on 2009-07-11
Well, you can try the script option. Also you can run "which firefox-3.5" to find out where it is located. Didn't think of that earlier.

---

### Post by EnlistedSquire on 2009-07-11
For those who've installed Firefox 3.5 using Ubutnuzilla, running ```
which firefox
``` just gives a symlink called Firefox in /usr/bin.

This is what I did to get this script to work:

First you need to edit VCoolio's script so it looks like this:

```
#!/bin/sh
LD_PRELOAD=/usr/lib/libGL.so.1 firefox
```

and give it whatever filename you like (need to make it executable as well).

You can now change the Firefox entry in the applications menu and the Preferred Applications applet to point to this script.

N.b. If you have multiple users you may need to put a copy of this script in each users' home directory. I orginally put it in /usr/bin and encountered some weird problems when setting it in Preferred Applications but this may be because my home directories are encrypted.

[EDIT]Also, what a mammoth bug to let slip into the final release. Someone was really sleeping on the job here.

---

### Post by lovinglinux on 2009-07-11
> **EnlistedSquire said:**
> For those who've installed Firefox 3.5 using Ubutnuzilla, running ```
which firefox
``` just gives a symlink called Firefox in /usr/bin.

This is what I did to get this script to work:

First you need to edit VCoolio's script so it looks like this:

```
#!/bin/sh
LD_PRELOAD=/usr/lib/libGL.so.1 firefox
```

and give it whatever filename you like (need to make it executable as well).

You can now change the Firefox entry in the applications menu and the Preferred Applications applet to point to this script.

N.b. If you have multiple users you may need to put a copy of this script in each users' home directory. I orginally put it in /usr/bin and encountered some weird problems when setting it in Preferred Applications but this may be because my home directories are encrypted.

[EDIT]Also, what a mammoth bug to let slip into the final release. Someone was really sleeping on the job here.

Too complicated. Ubuntuzilla users can simply edit the file /opt/firefox/firefox and adding the code below after the **moz_libdir** line (first uncommented line).

```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

---

### Post by EnlistedSquire on 2009-07-11
Thanks, I will try this later.

---

### Post by lovinglinux on 2009-07-11
> **EnlistedSquire said:**
> Thanks, I will try this later.

I have included this solution, with the proper credit to VCoolio, in the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). See **Solution** [**[COLOR="Red"]FOT008[/COLOR]**].

I also included the path to the file that should be edited for each of the 4 methods of Firefox 3.5 installation described in the "Install Other Versions" section, which are these:

[list][*] 
[*] **Method #1 (Psychocats):** /opt/firefox/firefox
[*] **Method #2 (Ubuntuzilla):** /opt/firefox/firefox
[*] **Method #3 (Repositories):** /usr/lib/firefox-3.5/firefox.sh
[*] **Method #4.1 (Shiretoko):** /usr/lib/firefox-3.5/firefox.sh
[*] **Compiled Firefox:** /usr/local/lib/firefox-3.5/firefox
[*] [/list]

---

### Post by SEBASTIANFFX on 2009-07-11
Thanks, ;) finally solved!

---

### Post by ourAri on 2009-07-12
> **sdowney717 said:**
> simply for 3.5 did this
gksudo gedit /usr/lib/firefox-3.5/firefox.sh

added line 

```
MOZDIR=$HOME/.mozilla
LIBDIR=/usr/lib/firefox-3.5
export LD_PRELOAD=/usr/lib/libGL.so.1
APPVER=3.5
META_NAME=
GDB=/usr/bin/gdb
DROPPED=abandoned
```

Didn't work for me :(
I edited this file:
 /usr/lib/firefox-3.5/firefox
and added the above lines before this line

> 
moz_libdir=/usr/local/lib/firefox-3.5

Previously, I would get a message about sending the crash report to mozilla, but after adding these lines, firefox just crashes and the window disappears with no message.

I also tried adding only this line
export LD_PRELOAD=/usr/lib/libGL.so.1
same results:mad:.

---

### Post by philinux on 2009-07-12
I'd love to know why this is happening to some people and not others.

All fine here. Maybe it's graphics card related.

---

### Post by EnlistedSquire on 2009-07-12
@OurAri - I think you need to add the lines *after* the ```
moz_libdir=/usr/local/lib/firefox-3.5
``` line.

---

### Post by mac-duff on 2009-07-12
Thx,
finally I found it. Its:
/opt/firefox/firefox

---

### Post by ourAri on 2009-07-12
> **philinux said:**
> I'd love to know why this is happening to some people and not others.

All fine here. Maybe it's graphics card related.

I think I finally got it. Apparently my GLX config for NVIDIA card was not right. I would get this error just before firefox crash:
Xlib:  extension "GLX" missing on display ":0.0".

Reinstalled NVIDIA driver and now full screen works well! :p

---

### Post by Danbo19 on 2009-07-14
Thanks VCoolio, adding !(name=firefox) to my compiz open animations fixed the conflict. I love when things work!

---

### Post by jv@indotreks.com on 2009-07-17
This works for all of my 32bit systems, but not for 64bit. Any suggestions?

---

### Post by Garyhans on 2009-07-17
Mine too. I just right clicked the video. Uchecked hardware acceleration to get it to work for now.

---

### Post by rccn on 2009-07-18
> **lovinglinux said:**
>  I have compiled Firefox and it was installed at /usr/local/lib/firefox-3.5 and there is no firefox.sh there.
Same here, but I added that line from VCoolio to **run-mozilla.sh** (the only script file in the installation folder) and it works quite well.

---

### Post by BoredOutOfMyMind on 2009-07-18
> **Danbo19 said:**
> Thanks VCoolio, adding !(name=firefox) to my compiz open animations fixed the conflict. I love when things work!

This worked for me to fix when I was unable to close the full screen. 

:D

From CCSM

Effects> Animation> Open Animation > Add

---

### Post by B-Con on 2009-07-26
Very nice, this solved my problem.

I primarily use Arch now. For Arch, since /usr/lib/firefox-3.5/firefox is a binary (and firefox has nothing in /opt) I just replaced the /usr/bin/firefox symlink with the script:

```
#!/bin/sh

export LD_PRELOAD=/usr/lib/libGL.so.1
/usr/lib/firefox-3.5/firefox
```

---

### Post by qva5 on 2009-08-02
> **VCoolio said:**
> 
```
#!/bin/sh
export LD_PRELOAD=/usr/lib/libGL.so.1
/path/to/firefox
```Now to run your browser make a launcher with as a command:
sh /path/to/script

Unfortunately, this has not helped with my **firefox 3.5.1**, installed from tarball.

I have modified my start script, by adding **export** line, but with that change I am completely unable to start my browser. 

I am just getting 

```
*** glibc detected *** /usr/local/share/firefox/firefox-bin: free(): invalid pointer: 0xb4e020a0 ***
```

each time i try to start it and that's it.

Any suggestions?

ps. Turning off hardware acceleration works, but this is just a workaround.

---

### Post by qva5 on 2009-08-05
This issue is present in firefox till 3.0.3. 

[https://bugzilla.mozilla.org/show_bug.cgi?id=460280](https://bugzilla.mozilla.org/show_bug.cgi?id=460280)

It looks like Mozilla has clean hands here, but unfortunately **nvidia** or **adobe**  don't try to fix it either.

---

### Post by xiphosurus on 2009-08-07
seems fixed in 3.5.2. i didn't have to add that line and i can still play youtube fullscreen. can anybody confirm?

---

### Post by EnlistedSquire on 2009-08-07
It's not fixed here.

---

### Post by qva5 on 2009-08-08
> **xiphosurus said:**
> seems fixed in 3.5.2. i didn't have to add that line and i can still play youtube fullscreen. can anybody confirm?
[B]
Sorry, but I cannot confirm this issue as being fixed. [/B]

I updated to 3.5.2, however the problem is still present. 
I've checked the Bugzilla and it looks like the problem is well known to Mozilla, but it has been defined as **nvidia/flash** issue. 
I am not sure if they doing something in the direction to fix the issue themselves right now.

ps. I was surprised by the time it is taking **nvidia/adobe/mozilla** to fix this very annoying issue(reported in 20080. Does it mean that linux community is not worth it?

---

### Post by redjedi on 2009-08-21
Hi

I'm still having this problem with Firefox.

I've added the line

> export LD_PRELOAD=/usr/lib/libGL.so.1

as instructed but still no luck.

I'm using Jaunty with Firefox 3.5.2

Any ideas?

Thanks

---

### Post by bzhao on 2009-08-30
> **redjedi said:**
> Hi

I'm still having this problem with Firefox.

I've added the line



as instructed but still no luck.

I'm using Jaunty with Firefox 3.5.2

Any ideas?

Thanks

export LD_PRELOAD=/usr/lib/libGL.so.1 
works for me
I am using Janunty with Firefox 3.5.2 as well
Please see if the flash plugin is there or not
the flash plugin should be inside  the folder plugins under the firefox installed folder.

in plugins folder:
flashplugin-alternative.so -> /etc/alternatives/xulrunner-addons-flashplugin
/etc/alternatives/xulrunner-addons-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so

libflashplayer.so is adobe flash plugin file.


Bill Z

---

### Post by Mulenmar on 2009-09-01
> **qva5 said:**
> **ps. I was surprised by the time it is taking [B]nvidia/adobe/mozilla** to fix this very annoying issue(reported in 20080. Does it mean that linux community is not worth it?

It took Adobe forever to release a 64-bit flash player for Linux. So as far as they're concerned, no, we're not. :frown:

I hate these Flash video bugs w/Firefox, so I decided to get around them, so far as YouTube is concerned anyway.

[LIST=1]
[*]Install Greasemonkey
[*]Install mozilla-mplayer or mozilla-plugin-vlc (I prefer mplayer)
[*]Go to userscripts.org and search for & install the YouTube Perfect scripts
[*]When you watch YouTube videos, you'll have the option to play as MP4, Flash, or to Download the video. 
[*]Play as MP4. 
[/LIST]

From personal experience, it works about 95% of the time, both fullscreen and normal-size. Sometimes Firefox decides to crash when you leave the video page, but everything opens back up when you restart Firefox and tell it to reopen old tabs.

Additional plus: Somewhat lower CPU usage than with Adobe Flash. :)

edit: Almost forgot: the VLC plugin seems to default to infinite loop and displaying no controls. The Greasemonkey YouTube script provides a "Stop" button, but that's it. Those are the reasons I prefer mplayer.

---

### Post by EnlistedSquire on 2009-09-10
Seems to be fixed with 3.5.3. Certainly I haven't had to re-add the line of code and I'm not getting any crashes. Can anyone else confirm? I couldn't see anything in the release notes.

---

### Post by qva5 on 2009-09-12
> **Mulenmar said:**
> It took Adobe forever to release a 64-bit flash player for Linux. So as far as they're concerned, no, we're not. :frown:

I hate these Flash video bugs w/Firefox, so I decided to get around them, so far as YouTube is concerned anyway..

Thanks for this neat hack. However I would appreciate if flash would work straight out of the box. 

<rant>
This looks like a general problem with FLOSS software. Everyone tell you that if necessary you could make a change, adding/removing/modifying, but if proprietary code ends up as part of it (take a look at flash in linux distributions), you really don't have that choice. 
</rant>

...

So, as long as 3.5 will crash with youtube, i will stay with **ubuntu's 3.0** (which also works more stable). 

Thank to that i have new hobby. Testing every new firefox release.

---

### Post by lovinglinux on 2009-09-12
> **EnlistedSquire said:**
> Seems to be fixed with 3.5.3. Certainly I haven't had to re-add the line of code and I'm not getting any crashes. Can anyone else confirm? I couldn't see anything in the release notes.

Yes. It has been fixed on 3.5.3 and also on 3.6.a1.

---

### Post by qva5 on 2009-09-12
Here you could find a link where you can **vote** for this issue to be resolved (and get more info about this problem, from mozilla guys).

[https://bugzilla.mozilla.org/show_bug.cgi?id=460176](https://bugzilla.mozilla.org/show_bug.cgi?id=460176)

---

### Post by qva5 on 2009-09-12
> **EnlistedSquire said:**
> Seems to be fixed with 3.5.3. Certainly I haven't had to re-add the line of code and I'm not getting any crashes. Can anyone else confirm? I couldn't see anything in the release notes.

[B]Confirm.
 [/B]
With firefox 3.5.3 youtube clips work quite good;)

---

### Post by qva5 on 2009-09-12
> **EnlistedSquire said:**
> Seems to be fixed with 3.5.3. Certainly I haven't had to re-add the line of code and I'm not getting any crashes. Can anyone else confirm? I couldn't see anything in the release notes.


Probably solution for issue **493541** included in 3.5.3, has fixed our problem.

[         > ]("https://bugzilla.mozilla.org/show_bug.cgi?id=493541")[**Bug 493541**]("https://bugzilla.mozilla.org/show_bug.cgi?id=493541") -               jemalloc integration cause crashes when libraries or plugins dlopen with RTLD_DEEPBIND      

You can find more details in release notes.

---

### Post by Marc van der Wijst on 2009-09-13
On Jaunty 64-bit right-clicked video and in settings unchecked "Enable hardware acceleration". Works like a charm for now. I will check it out again in FF 3.5.3.
Keep on the good work guys!\\:D/

---

### Post by stoian on 2009-09-24
Thanks a lot, VCoolio!!!! You rock, man!

I have Firefox 3.5.2 and it was always crashing when maximizing the flash video...


edited my /usr/lib/firefox-3.5/firefox script,
added the line you suggested, and it just works!!!

Thank you, this is a great day!

---

### Post by Marc van der Wijst on 2009-09-29
This problem seems to be fixed in Firefox 3.5.3. Sweet. :)

---

### Post by Mansteel on 2009-12-08
Hey this is first time writing here so i don't want to pretend to be too much of a smartass. 

But i have been following all of your advices in here. Nothing worked at all. 
Recently i found a much much simpler sollution. 

Go to a youtube video. Play it normaly. Right click in the window. And Disable the hardware acceleration!!!!! ;)

I thought that there would be some experts in this forum.. :???: Why bother writing all kinds of ununderstandable codes to a relativly simple sollution?

---

### Post by EnlistedSquire on 2009-12-08
> **Mansteel said:**
> Hey this is first time writing here so i don't want to pretend to be too much of a smartass. 

But i have been following all of your advices in here. Nothing worked at all. 
Recently i found a much much simpler sollution. 

Go to a youtube video. Play it normaly. Right click in the window. And Disable the hardware acceleration!!!!! ;)

I thought that there would be some experts in this forum.. :???: Why bother writing all kinds of ununderstandable codes to a relativly simple sollution?

What version of FF / Ubuntu are you using? This bug was fixed months ago.

---

### Post by Mansteel on 2009-12-12
> **EnlistedSquire said:**
> What version of FF / Ubuntu are you using? This bug was fixed months ago.
Ubuntu 9.10 (the latest one)
Firefox 3.5.5

---

### Post by Uachtarain on 2009-12-13
Yep boy do I know this. Install Google Chrome, Remove Firefox or leave it... watch your blood pressure go down...ha ha

Fergal

---

### Post by Uachtarain on 2009-12-13
Install Google Chrome.... Remove Firefox or leave it. The problem is with Firefox and has been for a couple of years now. Not worth the time to fix.

Fergal

---

### Post by macmaster on 2009-12-13
Firefox is glitchy for me, it randomly crashes every few hours.

---

### Post by Eskobar on 2010-02-18
> **Uachtarain said:**
> Yep boy do I know this. Install Google Chrome, Remove Firefox or leave it... watch your blood pressure go down...ha ha

Fergal


You have never lied brotha!!! Firefox has truly ran its course.  Not to mention the high cpu usage... makes my computer start humming lol.  Google Chrome is very nice, fast and low on resources. You dont even have to uninstall firefox, just try Chrome.

---

### Post by NoGroidWare on 2010-06-14
This is still a problem in Lucid Lynx, only in this release, the referenced library has been renamed.  Tried this with GLU, and /usr/lib/mesa's verion of GL, and neither worked.

Seems like the load code changed, which is a serious bug.  If this is as stated, it must affect almost every user.  Why am I still dealing with this so long after it was first reported, and in a new release of Ubuntu?

If we want that kind of logic, we could buy Windoze.

Also, it is a problem with the nvidia card, full stop.  I am not loading the nVidia drivers (which works much better, with better resolution options) at all.  That's another sore point.  A major share of Ubuntu users use the nvidia card, yet, since day 1 we have to act like it's some kind of exotic exception.  For 5 freakin' years, across 3 flavors of Linux, I simply copy my own version of XF86Config into the X11 directory, and I get highest resolution, no probs.  Not one- NOT ONE- released driver package, work around, etc. has ever worked.  THAT is what we expect from Microshaft, not Linux products.

---

### Post by stoian on 2010-06-14
> **NoGroidWare said:**
> This is still a problem in Lucid Lynx, only in this release, the referenced library has been renamed.  Tried this with GLU, and /usr/lib/mesa's verion of GL, and neither worked.

Seems like the load code changed, which is a serious bug.  If this is as stated, it must affect almost every user.  Why am I still dealing with this so long after it was first reported, and in a new release of Ubuntu?

If we want that kind of logic, we could buy Windoze.

Also, it is a problem with the nvidia card, full stop.  I am not loading the nVidia drivers (which works much better, with better resolution options) at all.  That's another sore point.  A major share of Ubuntu users use the nvidia card, yet, since day 1 we have to act like it's some kind of exotic exception.  For 5 freakin' years, across 3 flavors of Linux, I simply copy my own version of XF86Config into the X11 directory, and I get highest resolution, no probs.  Not one- NOT ONE- released driver package, work around, etc. has ever worked.  THAT is what we expect from Microshaft, not Linux products.

Dear NoGroidWare,

1. Did you try what people suggested in this thread? I know it is cumbersome to read through 8 pages of posts, but that is what it takes.
2. The nVidia card problem might be different from the one in this thread. On one of my boxes I am still running Karmic with nVidia and hardware acceleration / visual effects, and all is good (connected to a 46 inch SONY Bravia TV).
3. If Firefox doesn't cut it for you, then just use Google Chrome: it is faster, and could fix your problem.
4. If you really think Wind0ze will make you happier, then you are free to switch back...

I really hope you fix your problem and get back to your real, cool self :)

---

### Post by pvc kart on 2010-06-14
please check all new instatalion addon firefox browser

---

### Post by NoGroidWare on 2010-06-14
> **stoian said:**
> Dear NoGroidWare,

1. Did you try what people suggested in this thread? I know it is cumbersome to read through 8 pages of posts, but that is what it takes.
2. The nVidia card problem might be different from the one in this thread. On one of my boxes I am still running Karmic with nVidia and hardware acceleration / visual effects, and all is good (connected to a 46 inch SONY Bravia TV).
3. If Firefox doesn't cut it for you, then just use Google Chrome: it is faster, and could fix your problem.
4. If you really think Wind0ze will make you happier, then you are free to switch back...

I really hope you fix your problem and get back to your real, cool self :)

OK, for the "all I notice is presentation crowd"...

The library that you tell the script to load first isn't called that under Lucid Lynx.  So, the point is it is impossible to try what was recommended.  I posted what I tried.  Yes, I updated everything.  If it's my prob., fine, I'll deal with it.  The question was, "is everyone still having this problem"?  Either the answer is "yes", in which case the specifics to my case aren't very relevant, or it's "no" and you can ignore this.

I worked at Tandy in 1981 and wrote the first versions of Calculator, Notepad and Paintbrush for Windoze.  Their attitude never improved, and I'm not about to watch another OS get run into the ground to mollycoddle the politically correct.

---

### Post by EnlistedSquire on 2010-06-14
FYI, this problem was fixed for me a long time ago and hasn't raised its head even after a fresh install of Lucid. Using an Nvidia GeForce 7800 GTX with proprietary drivers installed.

---

### Post by akelsall on 2010-06-14
This was happening to me with 9.04 and the last version of FF. I recently upgraded to 10.04, plus the latest version of FF, and I no longer have this problem. I'm not sure which fixed it, but my guess would be the newer version of FF fixed it.

---

### Post by han681 on 2010-06-24
Thanks, worked perfect for me!

---

### Post by qva5 on 2010-06-26
Just want to add quick updated to my last messages.

First of all I am using 8.4 and 8.10 and  I've moved back to preinstalled version of firefox delivered with ubuntu, 3.0.19. With suggestions from this thread youtube does not crash firefox anymore and this is all what I wanted after all.

Of course maybe older version is less secure, but it's more stable. Every other firefox version I've downloaded and installed creashed at least once a day. It seems, to be ubuntu issue and as far nothing helped.

Chrome is good browser, I use it ocassionaly, but lack of some my favourite add-ons still conveince me to use mozilla's browser.

---

### Post by lovinglinux on 2010-06-27
Try these commands:

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

Restart the browser.

If that doesn't work, then right-click the flash video, select "Settings", then untick the option "Enable hardware acceleration".

For additional support see [Flash Troubleshooting and Optimization thread](http://ubuntuforums.org/showthread.php?t=1517564).

---

### Post by NoGroidWare on 2010-07-10
So, it turns out the answer is that it's an ugly bug.  The latest release addresses the prob by catching the crash gracefully, and displays (where the flash region is) "the flash plugin has crashed".  

Between the "we'll get to it eventually" attitude, the pompous groids  that can't answer a straight question- or bother to read one right, and  the idea that the release schedule is infinitely more important than end  user considerations, this is getting more like Microshaft everyday.  If  I get time it would be interesting to study the way this product  evolved and what is happening in the culture that produces it.

---

### Post by caffe_espresso on 2010-07-28
> **NoGroidWare said:**
> This is still a problem in Lucid Lynx, only in this release, the referenced library has been renamed.  Tried this with GLU, and /usr/lib/mesa's verion of GL, and neither worked.

Seems like the load code changed, which is a serious bug.  If this is as stated, it must affect almost every user.  Why am I still dealing with this so long after it was first reported, and in a new release of Ubuntu?

If we want that kind of logic, we could buy Windoze.

Also, it is a problem with the nvidia card, full stop.  I am not loading the nVidia drivers (which works much better, with better resolution options) at all.  That's another sore point.  A major share of Ubuntu users use the nvidia card, yet, since day 1 we have to act like it's some kind of exotic exception.  For 5 freakin' years, across 3 flavors of Linux, I simply copy my own version of XF86Config into the X11 directory, and I get highest resolution, no probs.  Not one- NOT ONE- released driver package, work around, etc. has ever worked.  THAT is what we expect from Microshaft, not Linux products.


I got the same problem, so I tried with:

sudo nvidia-xconf

after rebooting it seens working!

---

### Post by Ajay Ramaseshan on 2011-04-14
@VCoolio :
Hi 
I have Ubuntu 10.10 and am running Firefox 3.6-13. The youtube video upon fullscreening, crashes the plugin acrross all tabs. 
And there is no provision to send a crash report, which is usually present.
This problem occurs in other browsers too ie Chrome 9 and Opera 11.
I saw your post about the firefox.sh file and to add the line
```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

However, when I checked the /usr/lib directory, there is no file libGL.so.1.
The file with the most similar name is libGLU.so.1 . So I tried this :
```
 export LD_PRELOAD=/usr/lib/libGLU.so.1 
```

But the problem still persists.
Could you please help me out??

Ajay

---

### Post by VCoolio on 2011-04-14
@Ajay, man, I'd think this would've been fixed by now. But I can't help, tried with 10.10 64bit, firefox 3.6, flashplugin-installer 10.1.102 installed. Works. The libgl.so file belonged to a nvidia 173 driver package (nvidia-glx-173) I used back then on my old pc for my old video card. If I remember correctly this issue occurred especially with nvidia cards. Anyways, I think you'll get help sooner by starting a new thread. And get firefox 4, a lot faster!

---

