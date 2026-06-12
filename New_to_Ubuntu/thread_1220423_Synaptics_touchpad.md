---
title: "Synaptics touchpad"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by BobJam on 2009-07-22
My pointer is very erratic.

Thinking that maybe if I can adjust the Synaptics touchpad settings, this might improve the performance.

However, in System>Preferences>Mouse, the display does not reflect Synaptics touchpad settings as I knew them in Windows:

[IMG]http://i510.photobucket.com/albums/s346/rbjamie/Ubuntu/Pointers/1MouseProperties.png[/IMG]

[IMG]http://i510.photobucket.com/albums/s346/rbjamie/Ubuntu/Pointers/2Synapticsproperties.png[/IMG]

I've installed the Synaptics driver package:

[IMG]http://i510.photobucket.com/albums/s346/rbjamie/Ubuntu/Pointers/PackageInstallershowingthatxserver-.png[/IMG]

but I have no idea how to run an executable, or for that matter **WHERE** the executable even is located.

If I could get to a display like the one I was used to in Windows (shown above in the first two screenshots), I could make the settings.

I have mostly been pointing and clicking in the GNOME desktop, but I think here maybe I'm going to have to use the command line.

In any case, can anybody tell me what to do and where to find the executable (and how to run it . . . in Windows I just double clicked on an .exe file, but I know it's different in Ubuntu).

TIA

---

### Post by Durden on 2009-07-22
sudo apt-get install gsynaptic

Might help. Its a gui for configuring the touchpad.

---

### Post by BobJam on 2009-07-22
Here's what I got when I ran that command:[INDENT][FONT=Arial][COLOR=Blue][B][I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gsynaptic is a virtual package provided by:
  synaptic 0.62.5ubuntu3
You should explicitly select one to install.
E: Package gsynaptic has no installation candidate[/I][/B][/COLOR][/FONT]
[/INDENT]Seems like this in on the right track, but now what?

BTW, this is really getting annoying . . . the thing is skipping all over the place and I barely have control over it.  Posting in this window is a chore, and selecting text with the pointer is almost impossible (I resort to the Shift-Page/Arrow down mechanism).

I've adjusted the sensitivity in the pointer speed in System>Preferences>Mouse and am messing with the Accessibility options, but so far no joy.

---

### Post by lakshyt on 2009-12-29
Hello...
I am trying to configure and tweak my synaptics touch pad for ease of use and comfort.

First, I love the fact that I am now able to use two fingers to scroll. Thats great.

What I would love to do now, is configure the four corners of the touch pad to do certain tasks.

This could be, back (bottom right corner), and forward (top right) in the browser, minimize (bottom right).

I would also like to be able to do the middle click. Either by clicking with two fingers, or setting the top right corner of the mousepad to do that.

I have found previous posts that explain how one is able to use the two finger tap for the 3rd click. However, the code for that also includes a setting for the two-fingered scrolling which I didn't want to play around with because it's already working fine by using the default mouse application.

I appreciate the help you are providing us.

Laith

---

### Post by lakshyt on 2009-12-29
ok, so to reply to my own question... I was lucky enough to find this:
> **GreatMan(TM) said:**
> I always had the top right corner act as the middle mouse button for opening tabs. It was like that by default, so I was in trouble when I upgraded and it no longer behaved the same.

Anyway, this is how I fixed it: You need the gsynaptics package. From the command line you can use ```
synclient -l
``` to list the possible setting, most of which aren't in the GUI tool.

For corner buttons you want to edit the CornerButton lines. So all I had to do was enter ```
synclient RTCornerButton=2
```and I was able to tap the right-top corner button to emulate pressing the middle-mouse button.

Hope this helps

So I was able to configure that, and now I'm trying to find a way to configure the other buttons.

I tried setting LTCornerButton=5.. but it did work as to set it as button 5 of the mouse. So it seems like thats not the way it works. I'm going to send a msg to the original poster, and hope I'll get a reply.

Take Care.

---

