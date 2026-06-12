---
title: "High CPU activity - why?"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by zcacogp on 2009-05-27
Chaps, 

I've installed 9.04 on my Thinkpad X61s lappie, on a dual-boot with XP. 

It runs fine. Doesn't feel slow or tardy at all. But the CPU logs are showing that the processors are working very hard, even at idle. I have the System Monitor showing in the top panel, and it rarely shows a usage of less than 50% (as in, not at all). I also have a screenlet running on the desktop which shows CPU activity which is equally high. 

It's a dual-core 1.6ghz thing, with 4Mb RAM, so shouldn't be struggling. 

I also have the frequency scaling monitor showing on the top panel, and even with the CPU speed dialled down to 800Hz it doesn't feel any slower to use, but the CPU use graph is still very high. 

What's happening? I'm not running anything unusual - at the moment I have a couple of firefox windows open. Nothing more. And the two cores are showing 51.5% and 58.5% respectively. At idle. 

Are the graphs not accurate? 

Do ask questions - I can give more information. And thanks in advance for any help. 


Oli.

---

### Post by mcduck on 2009-05-27
Run "top" in a terminal and check what process is using the CPU.

---

### Post by Celauran on 2009-05-27
Run top to see what's eating up your CPU cycles.

---

### Post by pro003 on 2009-05-27
is your monitor screenlet designed for dual core cpu's?

---

### Post by zcacogp on 2009-05-27
mcduck, 

Good idea. 

The list is not stable (it changes with time), but the results are something like this: 

Xorg - 15%
dbus-daemon - 4%
gconfd-2 - 4%
firefox - 3%
x-session-manag - 3%
compiz.real - 2%
python - 1%

.. and then various other ones, at about 1% each. Maybe 7 or 8 of them. 

I know that adds up to around 40%, and the graphs show 50% or more, which is one of the reasons I am a bit confused. 


Oli.

---

### Post by zcacogp on 2009-05-27
pro003 - the monitor shows two lines for the CPU activity, one slightly higher than the other. I am assuming that one is for each CPU core. 


Oli.

ETA: I'm wrong - one trace is for "User", one for "System". 

But the screenlet shows both cores seperatly, so I am guessing it is correct.

---

### Post by Sir Jasper on 2009-05-27
Hi,

Someone suggested using htop rather than top. Unfortunately, I can't recall why?

However, I reckon someone will advise you - if not you could just try it.

My regards

---

### Post by mcduck on 2009-05-27
> **zcacogp said:**
> mcduck, 

Good idea. 

The list is not stable (it changes with time), but the results are something like this: 

Xorg - 15%
dbus-daemon - 4%
gconfd-2 - 4%
firefox - 3%
x-session-manag - 3%
compiz.real - 2%
python - 1%

.. and then various other ones, at about 1% each. Maybe 7 or 8 of them. 

I know that adds up to around 40%, and the graphs show 50% or more, which is one of the reasons I am a bit confused. 


Oli.
The last percent simply adds up from processes that use less than 0,5% CPU (so their CPU usage is rounded to 0)

15% is quite high for Xorg, but that's most likely related to all the screenlets and other stuff you have running on your desktop. Still, you might want to make sure you have correct graphics drivers installed.

My laptop has 1,66GHz Core Duo CPU, and with desktop effects enabled it idles at 0-3% CPU use (with Xorg's usage varying between 0% and 1%)

---

### Post by zcacogp on 2009-05-27
> **mcduck said:**
> ... you might want to make sure you have correct graphics drivers installed.How would I do this? 

> **mcduck said:**
> My laptop has 1,66GHz Core Duo CPU, and with desktop effects enabled it idles at 0-3% CPU use (with Xorg's usage varying between 0% and 1%)

That is more what I would expect. My 9.04 build on a desktop machine at home does pretty much the same (idle at around 0-2%.) I'd like the lappie to do the same (it should make the battery last a fair bit longer, amongst other things.) 


Oli.

---

### Post by sanderj on 2009-05-27
> **zcacogp said:**
> 
<snip>
I have the System Monitor showing in the top panel, and it rarely shows a usage of less than 50% (as in, not at all).


Use the Processes tab in System Monitor, and sort on CPU to see which processes are causing the 50% usage.


> **zcacogp said:**
> 

It's a dual-core 1.6ghz thing, with 4Mb RAM, so shouldn't be struggling.


Well, 4Mb is not that much ... ;-)

---

### Post by zcacogp on 2009-05-27
sanderj, 

Sorted by "CPU" under processes, I get a load of things that add up to nowhere near 50%.

gnome-system-monitor - 2%
dbus-daemon - 2%
gconfd-2 - 1%
firefox - 1%

... and not a fat lot more. Which is one of the reasons why I am wondering whether the graphs are not to be trusted. 

No, 4Gb is not a LOAD of memory, and it runs just fine, but I am confused by the graphs! :D

Sirjasper - thanks. I tried htop, and it claims not to be installed. 


Oli.

---

### Post by zcacogp on 2009-05-27
Sanderj, 

Just seen what you did there. I always confused the two of them - Megs and Gigs! :(

(Although, in my defence, I think you knew what I meant! ;) ) 


Oli.

---

### Post by Sir Jasper on 2009-05-27
Hi,

I installed htop using Synaptic Package Manager.

My usage seems a bit high but nothing like as high as yours and as I have a desk top I'm luckier.

Good luck.

My regards

---

### Post by mcduck on 2009-05-27
> **zcacogp said:**
> How would I do this? 



That is more what I would expect. My 9.04 build on a desktop machine at home does pretty much the same (idle at around 0-2%.) I'd like the lappie to do the same (it should make the battery last a fair bit longer, amongst other things.) 


Oli.

Do you know what graphics chip your laptop has? If you don't, you'll probably find the model if you run "lspci", although simple google search with the laptop's model might be easier way to get the same information.

You can also check what driver is currently being used by running "lsmod | grep drm" in a terminal.

Also I recommend disabling Screenlets for a while, just to see how big difference that makes. Some of them can be real resource hogs...

---

### Post by lovinglinux on 2009-05-27
> **mcduck said:**
> Do you know what graphics chip your laptop has? If you don't, you'll probably find the model if you run "lspci", although simple google search with the laptop's model might be easier way to get the same information.

You can also check what driver is currently being used by running "lsmod | grep drm" in a terminal.

Also I recommend disabling Screenlets for a while, just to see how big difference that makes. Some of them can be real resource hogs...

The sensors screenlets, including it's derivatives (ring sensors, circle sensors etc) are resource hogs by themselves. I would love to use them, but I don't think they worth the extra CPU usage.

---

### Post by b@sh_n3rd on 2009-05-27
I had about the same prob on my PC with an Intel i845 chip. It was running with the "vesa" driver at the time but as soon as I changed it to "intel" it began to work normally...after that I discovered the fix mentioned in the "Multimedia & Video" section. Anyways, this problem reeks of video driver fault...find your card and try to set the correct the driver. Hope this helped...

---

### Post by zcacogp on 2009-05-27
lspci gave this (first couple of lines): 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

lsmod | grep drm gave this: 

```
drm                    96296  3 i915
agpgart                42696  3 drm,intel_agp
```

To my eyes, this says that I have an Intel graphics chip and am running an intel driver. Is this so? 

If I am correct then it means that the driver is correct, so not much mileage to be gained there (alas!)

I have tried turning off the screenlets and it has made no difference to the (reported) cpu use. Although the machine remains as responsive as ever. 

b@sh_n3rd - what is the fix you mentioned in the "Multimedia and Video" section? I'll see if I can find it ... 

Thanks again for your help chaps. It's appreciated. 


Oli.

---

### Post by zcacogp on 2009-05-27
... to add, I have turned off the screenlets and rebooted the system, ensuring that they didn't startup at the reboot, and it has made no difference. 


Oli.

---

### Post by mbsullivan on 2009-05-27
I've found the built-in system monitor to give fairly anomalous results, as well. Are your readings highly variable, or is it steady at ~40-50% usage?

> To my eyes, this says that I have an Intel graphics chip and am running an intel driver. Is this so? 

Look at the output of:

```
glxinfo | grep direct
```

This should tell you whether you are using the Intel drivers properly.

Are you using CPU frequency scaling, and if so, are you getting these readings when you're on your lowest frequency step? Anecdotally, I've found the readings to be less accurate when the CPU is in a throttled state.

You can find the current CPU frequency with the following command (among other ways):

```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
```

To be clear... You're thinking that the problem is with the system monitor and not with a process hogging lots of CPU time, no?

Mike

---

### Post by zcacogp on 2009-05-27
Mike, 

The results aren't that variable. They move up and down frequently, but stay within the 50-60% range almost all the time. 

glxinfo | grep direct gave me this: 
```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```
I don't know whether this means I am using the drovers correctly or not. 

The command you gave me (sudo cat /sys/devices/system/cpu/cpu0/cpufreq) claimed to be a directory, not a command, but yes I am using frequency scaling. The current setting is "ondemand", and it flickers between 800mhz and 1.6ghz fairly often. However, if I move the setting up to "Performance", it makes no difference to either the behaviour of the machine or the cpu activity graph. 


Oli.

---

### Post by zcacogp on 2009-05-27
> **mbsullivan said:**
> To be clear... You're thinking that the problem is with the system monitor and not with a process hogging lots of CPU time, no?That is a suspicion, although based on nothing more than the idle musings of a non-techie mind. The reason for it is that the machine runs just fine - no sluggishness anywhere, and a delight to use. The only issue is that the graph shows a consistently high figure. (One may point out that a solution would be to stop the graph from displaying! ;) )


Oli.

---

### Post by mcduck on 2009-05-27
> **zcacogp said:**
> lspci gave this (first couple of lines): 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

lsmod | grep drm gave this: 

```
drm                    96296  3 i915
agpgart                42696  3 drm,intel_agp
```

To my eyes, this says that I have an Intel graphics chip and am running an intel driver. Is this so? 

If I am correct then it means that the driver is correct, so not much mileage to be gained there (alas!)

I have tried turning off the screenlets and it has made no difference to the (reported) cpu use. Although the machine remains as responsive as ever. 

b@sh_n3rd - what is the fix you mentioned in the "Multimedia and Video" section? I'll see if I can find it ... 

Thanks again for your help chaps. It's appreciated. 


Oli.

Yes, you have Intel graphics card. While I don't personally have one of those, I've understood that the Intel driver's included with 9.04 are not exactly spectacular when it comes to running desktop effects and other GPU-intensive stuff. You might want to try updating the driver, there's a PPA repository with new driver versions here: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/")

---

### Post by mbsullivan on 2009-05-27
> The command you gave me (sudo cat /sys/devices/system/cpu/cpu0/cpufreq) claimed to be a directory, not a command

Whoops... fixed. You answered my question, anyway.

> I don't know whether this means I am using the drovers correctly or not. 

That means that you are not using your graphics card for 3D acceleration. At least, this is what it meant with the old (pre-Jaunty) xorg setup. 

I think that still holds, even now that we've moved to GEM/UXA in lieu of DRI/DRI2/EXA.

> While I don't personally have one of those, I've understood that the Intel driver's included with 9.04 are not exactly spectacular when it comes to running desktop effects and other GPU-intensive stuff.

That's true. I have an Intel card.

> You might want to try updating the driver, there's a PPA repository with new driver versions here: [https://edge.launchpad.net/~ubuntu-x...ive/x-updates/](https://edge.launchpad.net/~ubuntu-x...ive/x-updates/)

I've seen people do this, with mixed results. It might work for you... but I'd probably shy away from it unless you're really into 3D effects and gaming. Be patient, I'm sure everything will work itself out with the Intel drivers eventually.

If I were you, I'd try and enable acceleration through a non-UXA method. It'll be an improvement, and hopefully shouldn't make your system unstable. One way to do this is to add the following to your xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "EXA"
        Option         "EXAOptimizeMigration"          "true"
        Option         "MigrationHeuristic"            "greedy"
        Option         "Tiling"                        "true"
EndSection

```

Then restart X and check glxinfo again.

Mike

---

### Post by zcacogp on 2009-05-27
Chaps, 

Thanks for your answers. 

I have a grasp of what you are suggesting, but only a vague one, and I'm afraid I will need to ask for more help. 

mcduck, you are suggesting I tell the computer about a new location to download software (or is it updates?) from, but I have no idea how to 'give' that new location to the computer. I seem to recall having seen instructions about this sort of thing, and I need to add that location to a configuration file, but I don't know what file or where. Some more direction would be most welcome - thanks! 

mbsullivan, EXA/UXA and DRi/DRi2 mean nothing to me, but I suspect that is not critical to this question. I'm not into 3d graphics or gaming, although I am happy to play, HOWEVER my complete-numpty status means I probably ought to be careful about anything too difficult. Where is xorg.conf, and can I edit it using gedit? And how do I restart X (is this another way of saying 'reboot'?) and how do I check gixinfo? 

In short chaps, I suspect you have over-estimated my knowledge and ability. Thanks - I'm flattered! :D - but instructions need to be clear and simple ... :(

Thanks very much for your input, both of you. 


Oli.

---

### Post by sodainmay on 2009-05-27
i got the same problem as well. often one is very high ,and the other one is not so much.

---

### Post by mbsullivan on 2009-05-27
> mbsullivan, EXA/UXA and DRi/DRi2 mean nothing to me, but I suspect that is not critical to this question. I'm not into 3d graphics or gaming, although I am happy to play, HOWEVER my complete-numpty status means I probably ought to be careful about anything too difficult. Where is xorg.conf, and can I edit it using gedit? And how do I restart X (is this another way of saying 'reboot'?) and how do I check gixinfo?


To be perfectly honest, I'm not so sure what exactly they are, either. Long story short, EXA is the old way to do 2D acceleration, DRI is the old way to do 3D acceleration.

The "new" way is to use UXA/GEM for 2D, DRI2 for 3D. However, as of Jaunty, there are some bugs and issues with this combo, especially for Intel drivers.

> Where is xorg.conf, and can I edit it using gedit? 

xorg.conf is located at /etc/X11/xorg.conf. You can edit it with gedit, but you need administrative permission to do so:

```
gksu gedit /etc/X11/xorg.conf
```

> And how do I restart X (is this another way of saying 'reboot'?) 

It's another way to say "logout". Essentially, you want the screen to go blank and to get back to the login screen.

The old key combo to restart X was CTRL+ALT+Backspace. By default, that's now disabled by default (which IMO was a horrible call). To re-enable it, you could also add the following to xorg.conf (while you're in there):

```
Section "ServerFlags"
        Option "DontZap"        "false"
EndSection

``` 

> and how do I check gixinfo? 

Same way as before:

```
glxinfo | grep rendering
```

Hopefully it'll turn into a "yes".

Mike

---

### Post by zcacogp on 2009-05-28
Mike, 

Thanks. I've now amended the xorg.conf file but the glxinfo command still returns "No". 

Having read the page on xorg.conf (man xorg.conf), would adding the following line make any difference: 
```

Option         "Accel"         "True"
```

Or am I asking a stupid question? 


Oli.

---

### Post by zcacogp on 2009-05-28
OK, well, taking my courage in both hands I made the amendment I suggested above, and it still made no difference. 

It says that ```
(LIBGL_ALWAYS_INDIRECT set)
```

Where is LIBGL_ALWAYS_INDIRECT set? Is that in xorg.conf as well? 


Oli.

---

### Post by zcacogp on 2009-05-28
**[COLOR="Red"]New Symptoms! [/COLOR]**

Moving on from the xorg.conf issue ... I have discovered that if I click 'Log Out', but have something which has unsaved data (an office document, for instance), I am prompted with what to do with the unsaved data. 

If I click "Cancel" (i.e. cancel logout), the CPU activity drops to around 1% (pretty much as I would expect), but I am not logged out. 

I can then use the computer as normal, with the CPU activity very low. 

This would suggest, to me (and I may be wrong), that there is some process happening which is using the processor. When I start the logout, this process is stopped, and no re-started when I abort the logout. 

Does this sound logical? 

If so, what could this process be? How can I find it? There is nothing immediately apparent when I run 'top', either way. 

Are there processes which don't show in 'top'? 


Oli.

---

### Post by b@sh_n3rd on 2009-05-28
[COLOR=Black]OK, just a troubleshoot. The bug fix I mentioned is [here]("http://ubuntuforums.org/showthread.php?t=1130582"). When I had trouble, with some research, I eventually found out that it was to do with my Intel card. So with what I gained with my research I edited my xorg.conf like this. (This was *before* the bug fix mentioned).
[/COLOR][COLOR=Black]```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "AccelMethod" "uxa"
EndSection
```[/COLOR][COLOR=Black]
I posted a thread at the time [here]("http://ubuntuforums.org/showthread.php?t=1153171"). There's no real fix there. I found the thread above later on and was able to get my video working to the max. Just try adding the above. Then see if there is improvement, coz what you tried now, may or may not work on your card. For example, [COLOR=Navy]Option     "Tiling"    "true"[/COLOR] is,  [COLOR=Navy]"false"[/COLOR] for my i845. Depends on your specs. UXA oughta bring your cpu usage down to an amount, but might also cause some instability on your PC.

In reply to post [/COLOR][COLOR=Black][COLOR=Red]**[#29]("http://ubuntuforums.org/showthread.php?p=7360146#post7360146")**[/COLOR], that sounds like a rogue process or something? OR, maybe just a minor bug in jaunty, like a heavy video applet/process closing for logout and not restarting?...it just adds confusion...just try the above fix...if that doesn't help we'll have to consider some other problem. On the other hand, If it *does*, try the thread I've linked above. Good luck! :D
[/COLOR]

---

### Post by zcacogp on 2009-05-28
b@sh_n3rd, 

Thanks. 

I've now tried as you suggested, and my xorg.conf file looks like this: 

```
Section "Device"
        Identifier      "Configured Video Device"
	Driver          "intel"
        Option          "AccelMethod"                   "UXA"
EndSection
```

It didn't make any difference tho'! The plot is as it was before, pretty steadily above the 50% mark. 

I'm going with the rogue process idea. The difference is so marked - the graph drops, like a stone, to around 1%, when the shut-down is aborted. I don't know what process it is that it stopped at this point, and I don't know how to go about finding out. I'm wondering about playing with boot manager, although this is shooting in the dark a little. 

Thanks for your help. 


Oli.

---

### Post by b@sh_n3rd on 2009-05-28
you're welcome...just a note, is "UXA" really upper-case or lower-case? it oughta be lower-case...anyways, I'm not sure about the boot manager idea...the settings to load processes at login can be configured at, System > Preferences > Startup Applications, though...

---

### Post by zcacogp on 2009-05-28
UXA is upper case ... I'll try changing it. 

Yes, I know about the Startup Applications list. I've taken out a number of things from there, but there are some things that remain that I just don't understand! It could be one of them, I just don't know. 


Oli.

---

### Post by zcacogp on 2009-05-31
OK, bit of an update. 

Due to stupidity on my behalf, I ruined the install I had on my laptop, about which I started this thread. I have reinstalled, and all is well - CPU load is down at 1% or thereabouts. With the same set-up (same screenlets, same machine, same drivers, same live disk, etc etc etc.) Which suggests that it wasn't hardware related.  

BUT my desktop machine (at home) has started to do exactly the same thing. That had a low CPU trace (around 1%), but I was playing around with screenlets on that and the trace has jumped up to 50% or more - exactly the same as with the laptop machine. 

I have removed all the screenlets, and uninstalled them, but to no avail - same problem. I have tried playing around with the "Automatically remember running applications when logging out" setting in System > Preferences > Startup Applications, but with no happy result. 

It shows the same behaviour on logout as well - if I have unsaved data in an application, and try to logout, I am prompted to save the data. If I say "No, don't logout" then the system doesn't logout but the CPU activity trace drops back to around 1%. 

Anyone any ideas? I can confirm that this machine was working fine 2 hours ago (and has been for a month or so) and this problem is NOT graphics related as far as I am aware. 


Oli.

---

