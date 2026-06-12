---
title: "2 Ubuntu versions after security updates"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by DGINSD on 2011-02-27
I loaded Ubuntu 10.10 about a week ago, and after some redirecting from this forum I found the right instructions to get my wifi card up and running and in turn a internet connection to do updates. After the updates completed I rebooted the system only to find now in the boot menu there are now 2 versions of Ubuntu to chose from; [COLOR="Purple"]Ubuntu with Linux 2.6.35.**25**[/COLOR] generic, a recovery of the same name, then there's[COLOR="Purple"] Ubuntu with Linux 2.6.35.**22** generic[/COLOR] and its recovery mode.

My question is do I need this seemingly older or different version? Did Ubuntu create another partition for this second version that taking up extra space? If so how do I get rid of it and make sure my computer doesn't add things like this in the future, or is it necessary?

Off topic but a few other buggie issues that might likely be resolved by one with more experience. Some windows for certain apps are too big causing some content to not be on the desk top one specifically the settings window for Evolution Mail the last tab is cut off. 

Second problem, DVD play is choppie, some of the player programs I've tried don't work at all, some crash when I open a disc, others have no sound. Whats the best program to both play and backup encrypted DVDs (has to do DVD9 to DVD5), I'd like to use my new Ubuntu install to do this with but my windows programs work flawlessly and these issues so far have me concerned about weather or not Ubuntu is capable?

---

### Post by Perfect Storm on 2011-02-27
You can safely uninstall the previous kernel. The reason it's still there is if the new kernel fail you can login in the previous one.

> Second problem, DVD play is choppie, some of the player programs I've tried don't work at all, some crash when I open a disc, others have no sound. Whats the best program to both play and backup encrypted DVDs (has to do DVD9 to DVD5), I'd like to use my new Ubuntu install to do this with but my windows programs work flawlessly and these issues so far have me concerned about weather or not Ubuntu is capable?

Make sure to install the codecs and a lib to play DVDs.

Install **ubuntu-restricted-extras**

Also add medibuntu: [http://medibuntu.org/](http://medibuntu.org/)
and install libdvdcss2 and non-free-codecs

---

### Post by fabricator4 on 2011-02-27
> **DGINSD said:**
> I rebooted the system only to find now in the boot menu there are now 2 versions of Ubuntu to chose from; [COLOR="Purple"]Ubuntu with Linux 2.6.35.**25**[/COLOR] generic, a recovery of the same name, then there's[COLOR="Purple"] Ubuntu with Linux 2.6.35.**22** generic[/COLOR] and its recovery mode.

That's a feature, not a bug.  It's a good idea to keep the last known working kernal on the computer in case there's a problem with the new one.  This make reverting to the last known good one a simple matter.

If you want to get rid of old kernels use synaptic package manager and delete them.  Search for linux-headers-2.6.35 and delete the ones you don't need.


> Off topic but a few other buggie issues that might likely be resolved by one with more experience. Some windows for certain apps are too big causing some content to not be on the desk top one specifically the settings window for Evolution Mail the last tab is cut off. 

Sounds like you're running in a low resolution mode.  Have a look in display settings and see if there's a higher res mode that you can use.

If you're using an old laptop or netbook that just doesn't have the screen resolution there is a workaround.  You can grab the window and move it so that you can get access to the other buttons and controls.  Hold down the <alt> key while clicking and dragging in the window area.  I believe visual effects must be set to "none" for this to work.

> Second problem, DVD play is choppie, some of the player programs I've tried don't work at all, some crash when I open a disc, others have no sound. Whats the best program to both play and backup encrypted DVDs (has to do DVD9 to DVD5), I'd like to use my new Ubuntu install to do this with but my windows programs work flawlessly and these issues so far have me concerned about weather or not Ubuntu is capable?

Playing videos works well on most computers I've tried, though it's not something I do much of, usually.  You do need to load the restricted codecs which cannot be shipped with Ubuntu because of the licensing issues.  To load the restricted extras package with the codecs see [here]("https://help.ubuntu.com/community/RestrictedFormats"). I've always found it to be a simple and easy one click solution to the problem.

I have had problems with totem movie player not playing some DVD's.  In this case I've always found Gnome mplayer to work well enough to fill the gap.  Some of the controls in Gnome mplayer don't work.  Someone else might be able to suggest some better packages.


Chris

---

### Post by DGINSD on 2011-02-27
Thank you for the explanation of the other kernel sounds best to just let well enough alone, my only question about it would be is it taking up a lot of disc space?

I already had installed the Ubuntu-restricted-extras package when I did was when it went from no play at all to the issues described in my first post.
I added Medibuntu and installed libdvdcss2 and non-free-codecs and so far I tried the Gnome Mplayer I'm getting good playback butI get error messages on startup of the program;"[COLOR="Red"] Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory[/COLOR]".whats this mean and how can I remedy it?

> Sounds like you're running in a low resolution mode. Have a look in display settings and see if there's a higher res mode that you can use.

If you're using an old laptop or netbook that just doesn't have the screen resolution there is a workaround. You can grab the window and move it so that you can get access to the other buttons and controls. Hold down the <alt> key while clicking and dragging in the window area. I believe visual effects must be set to "none" for this to work.


My computer is an older Dell Inspiron 1150 laptop, when I click into Monitor Preferences it says; 

Monitor: unknown 
Resolution: 1024X768 (4:3) 
Refresh: 0hz 
Rotation: normal

which is the right resolution but the "monitor unknown" kinda concerns me the 0hz refresh should be 60hz, which can't be changed, just for being complete in some of the previous talked about video programs I don't have control of some of the included video settings; contrast brightness color etc. I'm guessing I'm using a generic monitor/graphics driver,is there a fix for that?

With the <alt> key thing to move the window where would I go to set visual effects to "none", sorry if this seems a remedial question I'm a very new newb, but being as green as I am all the help I can get is very much appreciated.

---

### Post by Perfect Storm on 2011-02-27
> Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

Install libvdpau1 and vdpau-va-driver should fix the problem. It's used for running movies via the video card (better performance and quality). But if you don't have a nvidia card you can change the settings in Gnome mplayer and change the video output to xv

---

### Post by DGINSD on 2011-02-27
So if I don't have a Nvidia card do I still need to install "libvdpau1 and vdpau-va-driver", or just change the video output settings to XV? What should the audio output settings be set to? what about other players rippers and burner programs?

EDIT

I just change the video output XV but now I get no playback it tries (flickers and changes chapters)but no picture eventually I do get audio though.

---

### Post by Perfect Storm on 2011-02-27
> **DGINSD said:**
> So if I don't have a Nvidia card do I still need to install "libvdpau1 and vdpau-va-driver", or just change the video output settings to XV? What should the audio output settings be set to? what about other players rippers and burner programs?

Just change it to xv and you'll be fine :)

---

### Post by DGINSD on 2011-02-27
> **Artificial Intelligence said:**
> Just change it to xv and you'll be fine :)

No dice, I edited my previous post. I just thought of something maybe totally wrong but the DVD is NTSC, I just noticed your in Europe different video standards no?

---

### Post by Perfect Storm on 2011-02-27
Have you tried the other video output in Gnome Mplayer?

By the way which version of Gnome Mplayer are you using?

---

### Post by DGINSD on 2011-02-27
OK X11 and XVMC both seem to work OK, X11 seems to process anamorphic movies.

Not sure which version how do I tell?

Also to back up my DVD movies on single layer DVD's are there any other things I'm gonna meed to get?

---

### Post by Paqman on 2011-02-27
> **DGINSD said:**
> Thank you for the explanation of the other kernel sounds best to just let well enough alone, my only question about it would be is it taking up a lot of disc space?


About 100MB.

---

### Post by DGINSD on 2011-02-27
> **Paqman said:**
> About 100MB.

So not too much, though with my tiny dual booted 80G HDD, space is at a premium.

On the video player issue I downloaded the dragon player and it almost works a little jerky now and then but not totally un-useable. The "Movie Player" that came with my Ubuntu install is still very jerky to the point of being worthless. Whats the consensus on which is the best free player (I'm cheap)

---

### Post by fabricator4 on 2011-02-27
> **DGINSD said:**
> With the <alt> key thing to move the window where would I go to set visual effects to "none", sorry if this seems a remedial question I'm a very new newb, but being as green as I am all the help I can get is very much appreciated.


Did you try it?  Possibly it's already set to none.  However:

```

->System
    ->Preferences
        ->Appearance

```

and then select the "Visual Effects" tab.  Select "None" - Simple desktop environment.

Chris

---

### Post by Perfect Storm on 2011-02-27
> **DGINSD said:**
> So not too much, though with my tiny dual booted 80G HDD, space is at a premium.

On the video player issue I downloaded the dragon player and it almost works a little jerky now and then but not totally un-useable. The "Movie Player" that came with my Ubuntu install is still very jerky to the point of being worthless. Whats the consensus on which is the best free player (I'm cheap)

As fabricator4 said, do try disable the eyecandy stuff. It would help if you're using a low end computer.

Another player you could try is VLC. As the same with Gnome Mplayer you can with VLC experiments with Video output to see which one give the best performance for you.

---

