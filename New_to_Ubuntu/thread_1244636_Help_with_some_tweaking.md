---
title: "Help with some tweaking"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by libertypilot on 2009-08-19
So I just recently installed xubuntu 9.04 on my 11.6" Acer Aspire One Ao751h. I swapped the 160GB HDD out for a 32GB SSD.

After some forum searching and trolling, I was able to get a lot of my questions answered, and have fixed my main problems. However, there's still some tweaking left over for me to do, and I'm not very experienced with linux.

What I've done so far:

Turned laptop mode on via[FONT=monospace] 
[/FONT]echo 5 > /proc/sys/vm/laptop_mode

Installed powertop, did what it suggested (this definitely gave me about another hour of juice)

Installed graphics driver following directions from [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)


Anyway, I'd like to get as much battery power out of this netbook as possible. When running XP Home on the HDD, I get about 7 1/2 to 8 hours of battery life running wifi and Firefox. With xubuntu I get about 5 to 5 1/2 hours (powertop says I'm using between 8.5W and 11W). If I can get closer to the original battery life, that'd be great. I've read quite a bit from lesswatts.org, but I'm unsure of how to tweak my power settings further. One of the big consumers of power is something entitled "psb@pci:0000:00:02.0" I have no idea what that is.

A few other gripes: 

I'm not sure whats doing it (maybe hitting the touchpad?) but every now and then windows randomly switch around or if I'm typing it pastes from my clipboard.

Sluggish performance in firefox - I assume this is associated with the graphics driver. I've read that there isn't great Linux support for the GMA 500 on my netbook, so I guess its not being used to its full potential. The most annoying thing is scrolling: firefox essentially locks up while I'm scrolling up or down and I have to wait for it to catch up with my touchpad scrolling.


Anyway, any help/suggestions/further reading would be greatly appreciated! Thanks!

---

### Post by rajeev1204 on 2009-08-20
Scrolling is a problem with firefox on linux.Try the new firefox 3.5 if it fixes your problem.

---

### Post by Penguin Guy on 2009-08-20
> **libertypilot said:**
> if I'm typing it pastes from my clipboard.
When you press down the middle button (scroll wheel) in Linux it pastes the last text you had highlighted. Perhaps you are doing this accidentally?

---

### Post by libertypilot on 2009-08-20
> **Penguin Guy said:**
> When you press down the middle button (scroll wheel) in Linux it pastes the last text you had highlighted. Perhaps you are doing this accidentally?

My touchpad doesn't have a middle click button. I also went into my mouse settings and disabled the middle click function just in case. However I think I found a fix for this while looking for audio/video codecs. I came across this HOWTO:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

And followed these instructions:
> **[COLOR=darkred]LAPTOP TOUCHPAD[/COLOR]**

Using a laptop? If your cursor shoots off all over the place when you type and seemingly clicks on things without your consent, have no fear, you can disable it's click function while typing in a few simple steps. First of all, execute the following command in the terminal:

**gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi**

Next, copy and paste the following text into the empty document:

[B]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>[/B]

**[COLOR=DarkRed]Ubuntu/Xubuntu Users:[/COLOR]** Navigate to "System > Preferences > Sessions" ("Applications > Settings > Autostart Applications" in Xubuntu) and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot.

Its more of a workaround. It didn't stop my touchpad from randomly pasting things or rolling up windows, but it only ever does this when I'm typing, so disabling the touchpad while I'm typing is a good-enough solution for me. Still, it'd be nice if my toucpad wasn't crazy.

@rajeev Thanks for the suggestion. I'll update and see if it fixes the problem. If that doesn't work I guess I'll check out other browsers.

---

### Post by LewRockwell on 2009-08-20
we've got one similar to that and it does "wierd" "performances" with the arrow/pointer/cursor also

we've come to the conclusion that, since the touchpad is actually integral to the case, static electricity plays a part in this phenomenon

you will also note that this does not happen with everyone equally due to each bodies individual and somewhat unique electrical field

Wheeeee, look at those electrons go!

.

---

### Post by SuaSwe on 2009-08-20
For the Firefox scrolling thing, you can also edit this document*:

~/.mozilla/firefox/<ID#>.default/chrome/userContent.css

I believe it's this setting that does it:

```

body {
background-attachment: scroll !important;
}

```

... and there's also loads of other things that can be tweaked exactly to your liking! There are templates of this particular file in the chrome folder that explain it all. :)


*Note that this document doesn't exist until you create it so take the example from the same folder and edit it as you want it, then save as userContent.css

---

### Post by libertypilot on 2009-08-20
It would seem that I don't have an <ID#>.default folder nor a Chrome folder. Would this be for Firefox 3.5? I'm sticking with Firefox 3.0 for now, as 3.5 didn't fix my problem.

---

### Post by SuaSwe on 2009-08-20
Hmm, maybe it differs in xubuntu? Not sure as I've never used it. Have a look for it though if you like:

Open Terminal and do

```

cd ~/.mozilla/firefox

```

You should now be in that folder. Do

```

ls -l

```

... to show all unhidden files. Our directory should be unhidden and called something like 123a45b6.default. Do

```

cd 123a45b6.default/chrome    [replace these numbers and letters with those on your machine, obviously!]

```

Is the folder there? It may be hiding elsewhere in xubuntu; Google isn't being of much help on the matter!

---

### Post by libertypilot on 2009-08-20
So I was able to find the folder the example .css files. I made the change as you suggested, but no good. Firefox still stutters and is sluggish. 

I recently installed the poulsbo 2d/3d driver using synaptic package manager (poulsbo-driver-3d; poulsbo-driver-2d), but no real change in my computer's or firefox's performance...

---

### Post by binbash on 2009-08-21
play with laptop-mode configuration files. For example enable usb auto suspend etc. Tweak that laptop-mode settings (they are under /etc/laptop-mode/conf.d/ ) if you want more battery life and performance.

---

### Post by libertypilot on 2009-08-21
I think I may have squeezed a couple more minutes out of my laptop by configuring those files, but thats about it. It would seem according to powertop that the biggest consumer of power is something called "psb@pci:0000:00:02.0" (Anywhere from 35% to 60% of power at idle). I have no idea what it is and unfortunately a google search actually leads me back to this thread.


Hmmm, I just realized that psb probably stands for "Poulsbo" (my GMA500 integrated video), so this is probably my graphics. I guess there wouldn't really be a way of meaningfully reducing its power consumption.

---

