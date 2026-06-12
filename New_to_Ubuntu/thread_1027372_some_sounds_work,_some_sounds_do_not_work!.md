---
title: "some sounds work, some sounds do not work!"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-01-01
Hi Ubuntu Community:

I decided to keep up with the Jones and upgraded to 8.10. I started from scratch using an iso.

SOUND STOPPED WORKING. :-\"

I fumbled around for 2 days and studied the following forum discussions, fooling around - not really knowing what I was doing using advice from those pages.

Here are the forum discussions that I studied:

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
[http://ubuntuforums.org/showthread.php?t=997506]("http://ubuntuforums.org/showthread.php?t=997506")
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
[http://ubuntuforums.org/showthread.php?t=843012&highlight=sound]("http://ubuntuforums.org/showthread.php?t=843012&highlight=sound")


This morning I booted my computer and *some* sound started to work. I was shocked! Don't ask me why it works! :shock:

Here is what started working:
[LIST]
[*]Stuff on firefox like youtube and flash, and
[*]gxine
[/LIST]

Here is what still does not work:
[LIST]
[*]amarok,
[*]exaile,
[*]minirok.
[/LIST]

I don't know why they don't work! Maybe I need to put 2 more days of sweat into trying to get sound to work.

Can anybody provide advice on how to get amarok to work? Or to get sound to work in general?

:-k


Thanks,
Phil Smith
Duluth, GA

AMD 64

---

### Post by jboy012000 on 2009-01-01
* amarok,
    * exaile,
    * minirok.

Hi,

Are the above programs like SKYPE by any chance.

John

---

### Post by Old Jimma on 2009-01-01
Hi:

I do not know. I think that Skype is phone software. The programs I listed are music software. Perhaps both share some similarites, but I wouldn't know.

Phil

---

### Post by chrisod on 2009-01-01
Is it a matter of the first thing you try with sound working, and then no sound from any other app after that? Pulse Audio has some problems when multiple apps want to produce sound. I uninstalled Pulse and went back to ALSA in 8.04 and haven't had any more sound sound issues.

---

### Post by kansasnoob on 2009-01-01
I know you listed this as a source already, but I'd repeat the steps for Intrepid here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

And then follow the Troubleshooting (Appendix A and C) in the same guide.

---

### Post by Old Jimma on 2009-01-01
Hi Kansasnoob:

I followed your recommendation.

None of my sound software (eg, gxine, flash in firefox) work now.

I am sad.

Anything else you could offer?

Thanks.

Phil

---

### Post by Old Jimma on 2009-01-01
Chrisrod:

Can you guide me on how to uninstall pulse and swith over to alsa?

Thanks,
Phil

---

### Post by linux_tech on 2009-01-01
When multiple apps need to use sound at same time you should use alsa-oss

```
sudo apt-get install alsa-oss
```

If you are using intrepid, it is good to also have libasound2
```

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```

---

### Post by sadaruwan12 on 2009-01-01
> Can you guide me on how to uninstall pulse and switch over to alsa?

Hi,

I think I might be able to help you. Try these steps

click on System -> Administration -> Synaptic Package Manager

after getting the GUI click on a name of a package name and start type "Pulse" and the package manager will automatically take you to the pulse audio driver package. Now you'll see an green color box in front of the package name that means the package is installed on to your system. OK, click on that and a pop up will come and click mark for complete removal do the same for "pulseaudio-esound-compat" and now click on apply. You'll get a dialog box click apply on that too. This will remove pulse audio from your system completely.

To install ALSA do the same to search the name and click the check box from the pop up click mark for installation and click on apply now ALSA will get installed on to your system.

---

### Post by linux_tech on 2009-01-01
To un-install pulse and switch over to alsa, there is a good guide here-

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

---

### Post by ibuclaw on 2009-01-01
Installing asoundconf-gtk
```
sudo apt-get install asoundconf-gtk
```
running the app
**System->Preferences->Default Sound Card**
and selecting the **default** soundcard and quitting usually gets the sound working on pulseaudio/alsa/other if it isn't working to start with for me.

But, things that work for one person will not necessarily work for another...

Regards
Iain

---

### Post by Old Jimma on 2009-01-01
Dear Ubuntu Community:

[COLOR="Navy"]**Chrisrod suggested a solution that works when there is no sound!!**[/COLOR]

\\:D/


[COLOR="Black"][COLOR="Navy"]**Crisrod suggested just removing pulsaudio and reinstalling ALSA. So, that is what I did... and it works GREAT!**[/COLOR][/COLOR]

Here are the threads that show how to do these things:

[LIST=1]
[*][COLOR="Red"]**Remove pulse audio:** [http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)[/COLOR]
[*]1.[COLOR="Green"]**Install ALSA drivers:** [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)[/COLOR]
[/LIST]

I am grateful for the suggestions you provided, even the ones that seemed to make things worse temporarily. I am truely grateful for those, also. It gift to have people who will throw in their 2 cents, no matter what.

Have a great New Year! Continue being your selves as independent thinkers. 

Case closed.

:-\"

Sincerely,
Phil Smith
Duluth, GA

---

### Post by ibuclaw on 2009-01-01
That's great.

Since you are happy with the outcome, could you mark this thread as 'Solved'?
Just click on the 'Thread Tools' button in this thread and you should see it.

Regards
Iain

---

