---
title: "Dialogue windows seem to open as too small in Ubuntu"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Jerriy on 2009-05-06
Whenever some dialogue box or some pop-up appears the content falls out of place on the right edge of the box. Result: Dialogue text becomes (half)invisible. I really don't want to adjust boxes and po-pups every time they appear. I tried to see if there was some adjustment option available in "appearance configuration" but I couldn't fine one.

Why does it happen anyway? If there is a dialogue box, shouldn't the text wrap automatically? Why do Ubuntu popups behave as if I opened a notepad and disabled the "text wrap" option?

I never experienced something like this in 10+ years of Windows/Mac use. A (probably related) problem is also happening when I open a sidebar on the left side. Will the problem be solved if I upgrade to the new Ubuntu "Jaunty" or something? (from the currently installed 8.10)

Thanks in advance

---

### Post by Jerriy on 2009-05-06
Even buttons provided by the dialogue-boxes become (half-)invisible as a result of this problem.

---

### Post by nhasian on 2009-05-06
can you show us a screenshot of what your talking about?  simply press alt-print screen when the dialogue box is selected.

also did you change the font size/dpi?

---

### Post by Jerriy on 2009-05-06
Thanks for the reply - Yes I did do some changing of the size of fonts - is that what is causing the problem?

Here are some screenshots:

---

### Post by Zeedok on 2009-05-06
> **Jerriy said:**
> Thanks for the reply - Yes I did do some changing of the size of fonts - is that what is causing the problem?

Here are some screenshots:

I think the font size is your problem.  I have a media PC with Ubuntu on a very large screen and had similar issues, but it's pretty easily fixed by trying different font sizes in "System > Preferences > Appearance > Fonts"

---

### Post by Jerriy on 2009-05-06
Ok I try that - maybe it's an issue of precedence? (if i change one part of appearance, like "Theme" for example, then I have to keep going back to fonts again to let the fonts adapt to the new setting?)

---

### Post by Zeedok on 2009-05-06
No, you shouldn't have to. That setting is a global one (ie for all apps and themes)

---

### Post by Jerriy on 2009-05-06
Well I did that but no results :confused: The problem is still there...

---

### Post by freak42 on 2009-05-06
the add-ons window seems to need a minimum width , just make the window bigger or use the scrollbar below, you might have to test your new settings on another window (like the the 2nd screenshot above)

hth

---

### Post by spiderbatdad on 2009-05-06
If you manually make a window that size, firefox remembers the next time you open the window. So to fix the "problem" just drag the corner of the window to resize it, so it display correctly. The next time you open that type of window, it will be as you last left it.

---

### Post by El Zoido on 2009-05-06
I can second that, it happens a lot, with all kind of different applications.
Often an app opens a new window, e.g. to show the status of some action it is performing, and not everything is visible.
You have to adjust the size of the window manually.

---

### Post by Jerriy on 2009-05-06
> **freak42 said:**
> the add-ons window seems to need a minimum width , just make the window bigger or use the scrollbar below...The whole point of this thread is that it isn't right that I have to keep sideway-scrolling little windows (small w) every time they pop-up> you might have to test your new settings on another window (like the the 2nd screenshot above)That screen hasn't changed either.

---

### Post by spiderbatdad on 2009-05-06
Actually this thread is quite pointless. It is a troll thread. Firefox in windows behaves the same way. It remembers the sizes you set for it windows. So even the title of this thread is not true.
> Ubuntu has a problem Microsoft Windows never had

---

### Post by El Zoido on 2009-05-06
> **spiderbatdad said:**
> Actually this thread is quite pointless. It is a troll thread. Firefox in windows behaves the same way. It remembers the sizes you set for it windows. So even the title of this thread is not true.

While the title may be questionable ;) I wouldn't call this a troll thread.
It is a problem that occures not just with Firefox.
I don't think the origin of this behaviour is necessarily Firefox remembering the size of windows.
I had it happen in other apps, too.
So I guess it is propably a problem of the windows manager, or maybe Gtk.

Not necessarily Ubuntu specific.

---

### Post by Jerriy on 2009-05-06
> **spiderbatdad said:**
> If you manually make a window that size, firefox remembers the next time you open the window. So to fix the "problem" just drag the corner of the window to resize it, so it display correctly. The next time you open that type of window, it will be as you last left it.Yea - that's what I already did but unfortunately when you do a saved-temporary-data-clean- up or upgrade or reinstall or do something simillar then the default of that dialogue box/popup is the old bad one. 

I want the defaults to be "normal" and wrapped withing the visible space, just like Windows or Mac. Is this "mission impossible"? Surely that can be done (if it's not already done).

---

### Post by alphacrucis2 on 2009-05-06
> **spiderbatdad said:**
> Actually this thread is quite pointless. It is a troll thread. Firefox in windows behaves the same way. It remembers the sizes you set for it windows. So even the title of this thread is not true.

IIRC in the case of Firefox or any web browser it depends on the HTML/CSS of the page being displayed. If the div's etc are defined as being a percentage of the page width then text will automatically wrap as you shrink the page width until you hit anything requiring a minimum or fixed size. At that point a horizontal scroll bars will appear. That isn't really the same issue as a gnome or windows dialog box

---

### Post by Bradtek on 2009-05-06
Never ever seen this problem in Firefox ... Ubuntu 7.10, 8.04, 8.10, 9.04, or Windoze.

What do some people do to their computers that I never do :confused:

---

### Post by k3lt01 on 2009-05-06
Have you tried a different screen resolution. I have had a similar "problem" before and not in Ubuntu and all I did was change the screen resolution and it fixed it.

---

### Post by Aearenda on 2009-05-06
I think this is a real problem that can occur with some combinations of font sizes and monitor dpi settings unforeseen by the programmers. I often notice problems with tall dialogue boxes on my netbook (1024x600) for a similar reason. However, it definitely happens on Windows too if you change it to use large fonts, or a different dpi setting - it certainly isn't unique to Ubuntu, or even Linux distros.

At least in Ubuntu you can almost always resize the window - unlike on Windows.

---

### Post by Jerriy on 2009-05-06
> **El Zoido said:**
> While the title may be questionable ;) I wouldn't call this a troll thread.Ooh a bit touchy-feely today are we?
> It is a problem that occures not just with Firefox.You're right - I also think it might be an Ubuntu problem and not a Firefox problem (by the way I never even suggested that Firefox was the culprit) 
> I don't think the origin of this behaviour is necessarily Firefox remembering the size of windows.No one said it was :)
> ...I had it happen in other apps, too.Exactly! That's why I posted my problem right here in the _operating system_ forum and not at the _browser_ forum (Mozilla).
> So I guess it is propably a problem of the windows manager, or maybe Gtk.Windows manager? Gtk? :confused: > ...Not necessarily Ubuntu specific.Ubuntu operating system dialogue box isn't "ubuntu speciic"? :confused::confused::confused:

---

### Post by Jerriy on 2009-05-06
> **spiderbatdad said:**
> Actually this thread is quite pointless. It is a troll thread. Firefox in windows behaves the same way. It remembers the sizes you set for it windows. So even the title of this thread is not true.I beg to differ. Multiples of Ubuntu user reactions to this little thread has, by itself, confirmed that (1) there is a problem and that (2) it happens with a lot of Ubuntu users, and that (3) it's a recurring behaviour.

Examples have already been provided so if you dispute that then fess-up: show us a a similar Mac or Windows dialogue box/popup (preferably right now, as I don't want to give you enough time to photoshop one :))

---

### Post by El Zoido on 2009-05-06
> **Jerriy said:**
> Ooh a bit touchy-feely today are we?
Not at all, this was just my reply to #13

> **Jerriy said:**
> You're right - I also think it might be an Ubuntu problem and not a Firefox problem (by the way I never even suggested that Firefox was the culprit) 
No one said it was :)
I was under the impression that some people in this thread were starting to think so, also Spiderbatdad was pointing in that direction. ;)
> **Jerriy said:**
> Ubuntu operating system dialogue box isn't "ubuntu speciic"? :confused::confused::confused:
This is because the process responsible for drawing Windows/Controlls/etc. isn't Ubuntu but the Windows manager/Gtk engine, which isn't Ubuntu-specific but used by other distros as well.

Anyway, whatever the reason, it sure is annoying sometimes.
Especially as your changes aren't remembered.

---

### Post by Jerriy on 2009-05-06
> **Aearenda said:**
> I think this is a real problem that can occur with some combinations of font sizes and monitor dpi settings unforeseen by the programmers. I often notice problems with tall dialogue boxes on my netbook (1024x600) for a similar reason. However, it definitely happens on Windows too if you change it to use large fonts, or a different dpi setting - it certainly isn't unique to Ubuntu, or even Linux distros.

At least in Ubuntu you can almost always resize the window - unlike on Windows.Well the problem isn't that it is merely happening but rather that it happening by default. That's why it is an issue. If it was only happening if I do something exaggerated like, make the font too big or make the box too narrow, then I wouldn't have minded. 

But I want the default to be what defaults are supposed to be: normal.

Besides, I really don't want to readjust my screen resolution settings that I have finally settled on (as that would lead us to a whole another set of open-source software hiccups as you may know :>)

---

### Post by Aearenda on 2009-05-06
Jerriy, I really think there's something about your system metrics that is confusing the X subsystem. I have installed Ubuntu on many different systems and I haven't seen the word-wrap-missing-like-notepad problem myself. I just opened the Firefox toolbar customize box for the first time ever, and it was fine - no cut-off parts, as in your screenshot.

Can you tell me the dpi and font size settings you are using in system->preferences->appearance->fonts, and post the output from ```
xdpyinfo | grep dimension
xdpyinfo | grep resolution 
```
(and any other relevant changes in xorg.conf)? I'd like to try to recreate your problem on my system.

---

### Post by mick8985 on 2009-05-06
The comparison between operating systems and antagonistic nature of the title and replies you are giving are not necessary, people are here to solve your problem not defend the operating system. 
You're entitled to your opinion of ubuntu, but this is a support forum for ubuntu, whether you experience this on other operating systems is irrelevant.

---

### Post by Jerriy on 2009-05-06
Mick, believe it or not the title was not meant to be antagonistic at all - ok maybe a wee bit cheeky, I'll admit that much, but not antagonistic since after all it *is* a matter of fact that, of all the problems Microsoft Windows ever had (and also still have) sideway overstreaching boxes and popup windows hasn't been one of them, as far as I recall. 

Ubuntu is a special kind of Linux, namely one that deliberately strives (as one of it's core aims) to make linux a *competetive* alternative to the big non-linux world that is out there. Therefore one has to be careful not to allow this operating system to be (if I may say so) too "spartan" like many other alternatives.

---

### Post by Jerriy on 2009-05-06
> **Aearenda said:**
> Jerriy, I really think there's something about your system metrics that is confusing the X subsystem. I have installed Ubuntu on many different systems and I haven't seen the word-wrap-missing-like-notepad problem myself. I just opened the Firefox toolbar customize box for the first time ever, and it was fine - no cut-off parts, as in your screenshot.

Can you tell me the dpi and font size settings you are using in system->preferences->appearance->fonts, and post the output from ```
xdpyinfo | grep dimension
xdpyinfo | grep resolution 
```
(and any other relevant changes in xorg.conf)? I'd like to try to recreate your problem on my system.Well here they are:```
 dimensions:    1440x900 pixels (369x233 millimeters)
 resolution:    99x98 dots per inch

```

---

### Post by Jerriy on 2009-05-06
> **Aearenda said:**
> (and any other relevant changes in xorg.conf)? I'd like to try to recreate your problem on my system.That file has not been modified recently (3 months according to "properties")

---

### Post by Jerriy on 2009-05-06
I have a question regarding resolution since resolution is (from what I know of computers) a very influential thing in this matter. Is there such a thing as "default" resolution for a particular screen size? By default I mean a resolution that is "most fitting/sharpest/most optimum number of pixels or whatever for that particular screensize-videodriver combination. 

Or is it another possibility: just a matter of user preference (the best is whichever one the user selects, so long as the choice remains within a "minimum and maximmum" acceptability range.

My suspicion is that is is mostly a third possibility: well designed software and websites are correctly displayed no matter what, while others are "optimised" for marely one or the other size/resolution/font-setup/OP/browser... etc etc

---

### Post by stchman on 2009-05-06
Are you using a netbook?  If yes then decrease your font size.  My Aspire One did the same thing when the fonts were too big.  Unfortunately netbook screen size can be limiting.

---

### Post by Jerriy on 2009-05-06
No it's just a desktop.

As for decreasing my font size, stchman, please I'm almost ready to beg you to give me an alternative that wouldn't require that particular option (I really really like the font size, since when it becomes smaller it also suddenly becomes radically too thin/slender)

---

### Post by roachk71 on 2009-05-06
One of my gripes related to this thread is that the GIMP's main tools window keeps shrinking itself, but this has been the case for the last few revisions. In this instance, the problem should be referred to the GIMP developers (and has), but it appears unlikely to be fixed soon...

And I have to agree when it comes to dialogs: the settings in this case shouldn't be fixed to a given window size, but made more dynamic to accomodate different font and widget sizes. It's a bit aggravating, since some of these dialogs can't be resized at all (and in some cases, entire buttons get cropped out.)

---

### Post by Jerriy on 2009-05-06
The font-resolution issue is important since if it the case that one particular resolution "belongs" to a particular font-size (as a result of optimization or something else)

---

### Post by El Zoido on 2009-05-06
Now that I'm home, I can provide some screenshots, too.
This is using Avidemux. It's not the only app where I've seen it, but the only one I remembered right now. Also it happens every time, no matter if I resize it.

Just in case:
```
dimensions:    1680x1050 pixels (490x321 millimeters)
resolution:    87x83 dots per inch
```

---

### Post by Jerriy on 2009-05-06
> **roachk71 said:**
> It's a bit aggravating, since some of these dialogs can't be resized at all (and in some cases, entire buttons get cropped out.)Wow that's a bummer (I haven't yet encountered a dialogue getting cropped out while at the same time being one of those "un-resizables"

---

### Post by stchman on 2009-05-06
> **Jerriy said:**
> No it's just a desktop.

As for decreasing my font size, stchman, please I'm almost ready to beg you to give me an alternative that wouldn't require that particular option (I really really like the font size, since when it becomes smaller it also suddenly becomes radically too thin/slender)

What resolution are you running on your monitor?

---

### Post by Jerriy on 2009-05-06
Haha Zoido - that's quite a significant portion chopped-off. Das ist keine kleine :)

---

### Post by El Zoido on 2009-05-06
> **Jerriy said:**
> Haha Zoido - that's quite a significant portion chopped-off. Das ist keine kleine :)

Allerdings! ;)

However, maybe this is as much a problem with Avidemux.

---

### Post by Jerriy on 2009-05-06
> **roachk71 said:**
> One of my gripes related to this thread is that the GIMP's main tools window keeps shrinking itselfToo funny - I happen to be familliar with that Gimp "quirk" as well. But at least in that case there is no "chopping off" of the window-content as far as I gno

---

### Post by Jerriy on 2009-05-06
@stchman: 99x98dpi

---

### Post by Aearenda on 2009-05-06
Jerriy, you didn't say what your font settings are in system->preferences->appearance->fonts - I'm interested in what your dpi and font size settings are there, as well as the xdpyinfo stuff (which looks normal).

EDIT: [This blog post]("http://www.advogato.org/person/robertc/diary.html?start=98") looks useful!

---

### Post by Jerriy on 2009-05-07
Thanks for that link Aearenda - as for the font settings, I'm not at home now so I'll tell you that later (+/- 2 hrs from now)

---

### Post by Snyper450 on 2009-05-07
Thats weird Jerriy has this happen to anyone else coz ive got nothing wrong with my GUI when i was on 8.10 that was fine so it 9.04?

---

### Post by BDNiner on 2009-05-07
I have not encountered any problems with text wrapping that you are facing. My only issue is the 'save as' dialogue box will always be small. I have to manually resize it so that i can see anything.

---

### Post by El Zoido on 2009-05-07
At home I'm using 9.04, but it definitely happened before.
At work I'm still using 8.04, should I encounter it I could post it I suppose.

I'm pretty sure it would happen with Avidemux on 8.04, too.

---

### Post by Snyper450 on 2009-05-07
See im not having problems with that maybe a graphics card problem? incorrect Driver? what graphics cards you lot got Jerriy what do you have??

---

### Post by Jerriy on 2009-05-07
I've got Nvidia

---

### Post by Jerriy on 2009-05-07
> **El Zoido said:**
> ...At work I'm still using 8.04...You have Ubuntu at work? You lucky sonofagun. I guess you belong to the "happy few" who spend their days without ever going through the gate of Bill Gates.

---

### Post by Snyper450 on 2009-05-07
Workign without Big Brother on your back what a life :P well Jerriy you got the best card for the job xD

---

### Post by El Zoido on 2009-05-07
Unfortunately not completely.
On my PC in my office I'm pretty free to install whatever OS my faculty has a license for, or alternatively any free OS that suits me.
BUT there is some software I need that is Windows only - for that I still keep Windows in a virtual machine.
And in the lab there's practically no way around Windows yet, due to the same reason.

Still, better than nothing I guess ;)

---

### Post by lavinog on 2009-05-07
Jerriy: can you post a screenshot or list what your fonts and font details settings are in system>preferences>appearance>fonts

It looks like a bug report should be filed on this issue.  The bug report should have steps to recreate the issue.

The question is if this is a gtk/window manager issue, or if these are issues with individual programs.

In the future you should refrain from making comparisons to windows, especially since the problem can exist in windows.

---

### Post by Snyper450 on 2009-05-07
Aww dam so they still got a leash on you xD:P

---

### Post by El Zoido on 2009-05-07
Hm, I just remembered one more.
Quite ironically...
See the pic.
Again, this is Firefox, but unfortunately it doesn't seem to remember the setting when I resize and close it.

---

### Post by Jerriy on 2009-05-07
Well then, here are my font settings now:

Application font: Sans | 10
Document font: Sans | 10
Desktop font: Sans | 10
Window title font: ***Sans Bold Italic***
Fixed width font: Monospace | 10

Details:

Rendering: Subpixel smoothing
Resolution: 94 dpi
Smoothing: Subpixel
Hinting: Slight
Subpixel Order: RGB

---

### Post by Jerriy on 2009-05-07
> **lavinog said:**
> It looks like a bug report should be filed on this issue.  The bug report should have steps to recreate the issue.I've tinkered with the font and other settings a bit (since yesterday) so, to what extent this matter can be "recreated" I have no idea (i.e. I'm planning to see if the little changes I made have a good effect or not..

> The question is if this is a gtk/window manager issue, or if these are issues with individual programs.If a bug report is made one could do what I did: First try change a theme (or better yet: customize a theme) and at the same time make no other change in any other part of the appearance-settings and then enable that new feature (restart) and see what happenes - go from there.

---

### Post by Aearenda on 2009-05-07
Jerriy, are the fonts on your login screen unusually large (or small)? I'm wondering if X is detecting a different dpi setting, then getting overridden by the settings in Appearance->Fonts, and some apps are still using the old values.

Also, in /etc/X11/xorg.conf, do you have a 'DisplaySize' entry?

---

### Post by Jerriy on 2009-05-08
Nope, not unusually large or small at all, maybe slightly larger than the default but quite normal (as seen in the provided screen-shots). By the way this sideway-cropping issue is something I noticed right at the beginning when I started Ubuntu. But at first I just ignored it until I finally started using the OP intensively and then the recurrence of the phenomenon started bothering me.> Also, in /etc/X11/xorg.conf, do you have a 'DisplaySize' entry? Nope. Is it supposed to be there by default?

---

### Post by Aearenda on 2009-05-08
DisplaySize isn't supposed to be there by default - it allows you to override the metrics the monitor is providing, in case it is lying. In this case, I suspect it IS lying. EDID is the acronym for the mechanism used to report monitor metrics.

Are there any clues in your /var/log/Xorg.0.log, such as lines like these:
> (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.


EDIT: Actually, it might help if you attach your complete /var/log/Xorg.0.log (give it a .txt extension when uploading).

---

