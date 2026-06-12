---
title: "having trouble with skype"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by L Campbell on 2011-05-28
I'm using 11.04 on a PC and I'm having trouble with Skype, in that I can't complete a 'testcall' and if I call a person they can't hear me.

I've been to the Skype 'HELP' page and deleted a 'hidden' file, as per their suggestion, but still cannot get it to work.

Is going back to 10.04 a likely option?

TIA

---

### Post by Lateralis on 2011-05-28
Can you provide some more information?  

Do you just have sound issues, or is this video as well? Have you tested your sound/video in other programs such as Cheese and the sound recorder?  How have you installed Skype: with the .deb, the dynamic binary or static binary off of the [Skype website]("http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/")?

---

### Post by L Campbell on 2011-05-28
> **Lateralis said:**
> Can you provide some more information?  

Do you just have sound issues, or is this video as well? Have you tested your sound/video in other programs such as Cheese and the sound recorder?  How have you installed Skype: with the .deb, the dynamic binary or static binary off of the [Skype website]("http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/")?

It is just a sound issue, not video.

When I do the 'Test call' I can hear the young Lady perfectly but my message doesn't replay.

My sound seems to function properly, as in booting up.

I installed Skype from Ubuntu Software Center.

---

### Post by ajgreeny on 2011-05-28
Can you record with sound-recorder?  Perhaps your microphone is muted.

Try runing ```
alsamixer
```  in terminal and check that the levels are set where you want them.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by L Campbell on 2011-05-28
> **ajgreeny said:**
> Can you record with sound-recorder?  Perhaps your microphone is muted.

Try runing ```
alsamixer
```  in terminal and check that the levels are set where you want them.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

Thanks but this went way over my head.

The thing is that I have been using Skype for many years and my issue here is that I'm having this problem on 3 different machines that are about 5 miles apart.

---

### Post by beew on 2011-05-28
Install gnome-alsamixer from Synaptic, it has a gui.Just push capture way up, see the screen shot.

---

### Post by L Campbell on 2011-05-29
> **beew said:**
> Install gnome-alsamixer from Synaptic, it has a gui.Just push capture way up, see the screen shot.

Thanks for the suggestion. I installed it from Synaptic but it doesn't appear anywhere under Applications.

---

### Post by beew on 2011-05-29
It should be in Applications > Sound & Video if you use the Classic Desktop.

In Unity, move your mouse to the buttun "Applications" on the Unity bar, right click and choose "Multimedia", the dash will open up. If you don't see GnomeALSA Mixer,  click "see xx more results" next to "installed". Alternatively, just type GnomeALSA Mixer in the search bar.

EDITED: If you still can't find it open the Main Menu, choose Sound & Video on the left panel and see that the box GnomeALSA Mixer on the right panel is checked.
The Main Menu is in Places > Preference for the Classic Desktop. In Unity, you can either open the Dash (click Applications on the Unity bar) and search for it, or right click the "shut down" button on the upper right corner and choose System Settings on the drop down menu, a window will open up and you will find the Main Menu there.

---

### Post by beew on 2011-05-29
Oh btw your Skype problem may have to do with a bug which has disabled Skype for many people in the last few days. It is cross platform. :)
[URL="http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/"]
http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/[/URL]

Opps, sorry, it seems that Skype doesn't crash on you, you just have no sound.

---

### Post by L Campbell on 2011-06-04
Original post:-

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10876975](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10876975)

I realized that my troubles with Skype had begun after I had done an UPGRADE, as opposed to installing 11.04 from a disk, so I then installed 11.04 from a disk but still was not able to use Skype. Maybe there is a little 'hiccup' in 11.04?

Next, I installed 10.04.2 from a disk and that appears to have solved my problem.

I'm a happy camper.

---

