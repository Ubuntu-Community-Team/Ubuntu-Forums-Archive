---
title: "Firefox Freeze and Voices at Startup"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by XubuRoxMySox on 2009-04-11
[FONT="Comic Sans MS"]Hi y'all,

I'm new to Linux (and Ubuntu 8.10 is my first distro - installed a few days ago). And even though I'm having two little issues, I doubt I'll go back to Windows. I really don't think my computer should be *telling me what to do*, LOL! It's a tool! It's s'posed to do what *I* want, not tell me what *it* wants... so far in Ubuntu my computer is compliant and a whole lot faster! Now it says, "Yes, your majesty, right away!" instead of "I can't and I won't until and unless you do so-and-so first." Rawr.

Okay so I'm having two little problems:

**1st** and most important: Firefox freezes whenever I click on a YouTube link. The screen gradually (but quickly - just not suddenly) goes gray (like it does when I have to enter my password for a software installation or something), then Firefox just freezes and I have to "force" it to close. I have the "ubuntu restricted" package installed from "Multiverse" which was supposed to fix that, but it hasn't so far.

My **2nd** little glitch is on startup. The Terminal window opens and abuncha stuff referencing other languages scrolls across the pane while a computer voice starts babbling. It stops when I close the Terminal window.

I guess I configured some stuff wrong? Seems likely, I'm a total newbie and it took a long time to work up the courage to even *try* changing from Windows. 

I don't think this a true "bug" though. Prob'ly just something I messed up on when trying to install packages... I just dunno how to fix it yet.

Thanks!
-Robin, scared but excited n00b

[/FONT]

---

### Post by Michael.Godawski on 2009-04-11
hi dixiedancer,

do not be scared. Feel free to ask everything you want, there are no stupid questions.

Now are you perhaps running Compiz Visual Effects? That might cause sometimes trouble.
Check in System > Preferences > Appearance > Visual Effects.

Also what version of flash are you using? Type into the url input section if Firefox ;) ```
about:plugins
```

What is your graphic card? To check open up the terminal - Applications > Accessories > Terminal and run this command:
```
sudo lshw -C display
```You will be asked for the login/sudo password. Type it in, it won't be displayed. 

Have you tried to run firefox via the terminal to see if some errors are reported?
```
firefox
```> [FONT=Comic Sans MS]My **2nd** little glitch is on startup. The Terminal window opens and abuncha stuff referencing other languages scrolls across the pane while a computer voice starts babbling. It stops when I close the Terminal window.[/FONT]Could you post the output here?

---

### Post by XubuRoxMySox on 2009-04-11
Thanks, Michael.

I have the "standard" visual effects - the choice in the middle, not the fancy stuff. I was unable to get the "lshw -c display" command to show me anything. It just sits there with a "???" look on it's face, LOL. So I can't tell you what graphics card I'm using. It didn't even ask for a password.

I did start firefox from the Terminal line and it started right up, didn't show any problems. I have every plugin (lots of them!) enabled according to ```
about:plugins
``` But I'm having display issues in Firefox besides the YouTube freeze-ups:

I couldn't even log in here 'til I hit the "quote" button on your post, because on the front page of this forum in the User Name box it says "user name" and won't even let me put the cursor there. So my user name *has* to be "user name," unless I try to reply to a post, then I get a login screen I can actually use on this site. I've discovered I'm not the only one having that problem, too. Someone else described it [here]("http://ubuntuforums.org/showthread.php?t=1121519").

As for the other little problem, here's what I get in the Terminal window at startup:

> Welcome to Orca setup.
Select desired voice:
1. default (en)
2. en-scottish (en-sc)
3. english (en-uk)
4. lancashire (en-uk-north)
5. english_rp (en-uk-rp)
6. english_wmids (en-uk-wmids)
7. english-us (en-us)
8. en-westindies (en-wi)
9. esperanto (eo)
10. spanish (es)
11. spanish-latin-american (es-la)
12. finnish (fi)
13. french (fr)
14. french (Belgium) (fr-be)
15. greek-ancient (grc)
16. hindi-test (hi)
17. croatian (hr)
18. hungarian (hu)
19. indonesian-test (id)
20. icelandic-test (is)
21. italian (it)
22. lojban (jbo)
23. kurdish (ku)
24. latin (la)
25. macedonian-test (mk)
26. dutch-test (nl)
27. norwegian-test (no)
28. polish (pl)
29. brazil (pt)
30. portugal (pt-pt)
31. romanian (ro)
32. russian_test (ru)
33. slovak (sk)
34. serbian (sr)
35. swedish (sv)
36. swahihi-test (sw)
37. tamil (ta)
38. turkish (tr)
39. vietnam-test (vi)
40. Mandarin (zh)
41. cantonese-test (zh-yue)
42. afrikaans (af)
43. bosnian (bs)
44. czech (cs)
45. welsh-test (cy)
46. german (de)
47. greek (el)
Enter choice: 


So I guess Orca starts up by default? I wonder if I have some conflicting flash players or something in Firefox. I dunno which ones to use and which ones to disable. Here's what ```
about:plugins
``` shows me:

> 
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Totem Web Browser Plugin 2.24.3

    File name: libtotem-basic-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	application/annodex type 	anx 	Yes
audio/annodex 	audio/annodex type 	axa 	Yes
video/annodex 	video/annodex type 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes
Java(TM) Plug-in 1.6.0_10-b33

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_10

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_10 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_10 	Java 		Yes


Hope I'm not being a pain... thanks again,
Robin

---

### Post by XubuRoxMySox on 2009-04-12
Well I fixed the Orca problem by uninstalling it. I have no idea what to do about the Firefox problem other than just reload ubuntu and start over from scratch. I hate to do that, especially because it took me all day just to get the network connection to work and set up my e-mail and all that. I dunno what else to do. Should I try another browser first?

-Robin

---

### Post by crf on 2009-04-12
The firefox problem is likely a flash plugin problem.

What to do? Start firefox, go to Tools Menu --> Add-Ons --> Plugins and disable the flash plugin.

Then you won't see flash videos though.

--

You can try other flash plugins (there are several to choose from).

To try a different one, In Ubuntu, go to the System Menu --> Administration --> Synaptic package manager, and search for "flash".
You can try "flashplugin non-free" or "swf-dec mozilla" or "mozilla-plugin-gnash". You can have all of them installed at the same time, but if you do, in firefox's Add-ons section, I would try having only one enabled at a time.

---

### Post by XubuRoxMySox on 2009-04-12
> **crf said:**
> The firefox problem is likely a flash plugin problem.

What to do? Start firefox, go to Tools Menu --> Add-Ons --> Plugins and disable the flash plugin.

Then you won't see flash videos though.

--

You can try other flash plugins (there are several to choose from).

To try a different one, In Ubuntu, go to the System Menu --> Administration --> Synaptic package manager, and search for "flash".
You can try "flashplugin non-free" or "swf-dec mozilla" or "mozilla-plugin-gnash". You can have all of them installed at the same time, but if you do, in firefox's Add-ons section, I would try having only one enabled at a time.

Is one better than another? I'm down to one (Shockwave) but the same thing happens. It acts like it wants to load, but then the screen goes gray and I have to "force quit."

I guess if I want to see videos I have to go back to Windows??

I even tried another browser. Nothing helps. Do I re-install Ubuntu and start over? I'll lose another day getting everything set up again, but that would still be better than having my computer held hostage by Microsoft, LOL.

Thanks, though, y'all have been very kind.

Oh - maybe I should just use Xubuntu (for simplicity's sake?), not that my 'puter won't handle Ubuntu. But I'm starting to get display issues now and I'm not sure if I messed something up or not... or how to fix it. Is there some kinda "Restore all defaults" setting that might undo whatever I messed up?

Thanks so much,
Robin

---

### Post by crf on 2009-04-16
Reinstalling shouldn't have any effect. I'd say the one that works would be the best ;) ... if neither swfdec nor gnash nor flash-plugin non-free work, then it's just too bad :( ... often firefox crashes for me when I have flash enabled.

----

There is one more thing you could try: there are more modern versions of the swfdec programs you can download here --> [http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/) , called "unstable releases".

---

### Post by XubuRoxMySox on 2009-04-16
> **crf said:**
> Reinstalling shouldn't have any effect. I'd say the one that works would be the best ;) ... if neither swfdec nor gnash nor flash-plugin non-free work, then it's just too bad :( ... often firefox crashes for me when I have flash enabled.

Actually, re-installing did help! Perhaps some of the flash plug-ins don't play nice with each other *even when only one at a time is enabled*. Or perhaps I inadvertently set up some conflict myself with the graphics settings I was trying to use - some set up in *System ---> Preferences ---> Appearance* and some set up within applications like Firefox separately. I'm not sure what caused it, but "starting over from scratched" certainly fixed it.

I'm just using the "recommended" Adobe flash plugin and no others, and it's working just fine.

Thanks, y'all,
Robin

---

### Post by sanofi on 2010-01-27
I had the problem of firefox freezing on startup (using ubunti 9.10) and found that the cause was a firefox addon, bindwood. Disabled it and restarted and viola! Back to normal startup time.

I got the idea from a post which pointed me to plugins and worked through them one by one, to locate the problem plugin.

---

