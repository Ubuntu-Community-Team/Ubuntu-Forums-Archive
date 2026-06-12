---
title: "Display too big for screen."
date: 2011-05-05
forum: New to Ubuntu
---

### Post by Demothe7 on 2011-05-05
Hey guys,

I installed Ubuntu 11.04 today and all was well, but then when I installed the drivers for my video card, [NVIDIA GeForce GTS 450] the edges of the display got shoved into nothingness. Now, the top and bottom panels are gone and the bar at the side with the big buttons on [sorry I'm a total Linux newbie] is half-gone too, the sound isn't working either, but I read in another post that uninstalling PulseAudio might do the trick, I tried adjusting the resolution to no avail, any help would be greatly appreciated =]

---

### Post by kherring7383 on 2011-05-05
Here's an idea. First restart the system (Reset) and at the Login, choose Gnome Classic from the pull-down menu at the bottom of the screen and login. Hopefully you should now have the familiar Gnome Desktop. From there change your display resolution using the Monitors app under Preferences. Once you've changed it, log out then back in using the Gnome Classic Desktop to make sure the change took effect. If it did, log out again the choose Unity and hopefully it will be OK.

---

### Post by Demothe7 on 2011-05-05
> **kherring7383 said:**
> Here's an idea. First restart the system (Reset) and at the Login, choose Gnome Classic from the pull-down menu at the bottom of the screen and login. Hopefully you should now have the familiar Gnome Desktop. From there change your display resolution using the Monitors app under Preferences. Once you've changed it, log out then back in using the Gnome Classic Desktop to make sure the change took effect. If it did, log out again the choose Unity and hopefully it will be OK.
Thanks, I'll go try that now =D[URL="http://ubuntuforums.org/member.php?u=1216071"]
[/URL]

---

### Post by lukeanders70 on 2011-05-05
try the display options it should offer resizing options

---

### Post by Hedgehog1 on 2011-05-05
More likely you can solve this with adjusting the Overscan Compensation setting for your Nvidia card:

[IMG]http://img18.imageshack.us/img18/4561/screenshotnvidiaxserver.png[/IMG]

***The Hedge***

:KS

---

### Post by Demothe7 on 2011-05-05
I tried stretched, centered and aspect ratio scaled but nothing changed, and i forgot to mention that i read in another post that changing some values in 'section monitor', in xorg i think, would help, so i did, and now i'm stuck on tty command line and cant get back to the gui desktop =[ i'm really getting tangled up with linux, but i've seen what people can do with it so i cant give up.

---

### Post by Hedgehog1 on 2011-05-05
Try: **startx**


Then, please adjust the **Overscan Compensation** setting

---

### Post by Demothe7 on 2011-05-05
OK I tried 'startx' but i got 'fatal server error: no screens found' and sorry hedgehog, i was thinking of 'GPU scaling method' for some reason XD. Sorry my brain isn't working properly because my tonsils are attempting to break out of my neck. I will of course, try adjusting the overscan compensation setting, if I can get back onto the desktop.

---

### Post by 3rdalbum on 2011-05-06
Wow, I had no idea there were such problems with the newer Nvidia graphics cards. I've never encountered that before, although my cards are a little older.

As for the sound not working, you might need to install some updated Alsa packages. Don't bother trying to remove Pulseaudio - it doesn't cause loss-of-sound problems these days, but removing it will probably prevent you from ever getting any sound.

For some odd reason, a new installation of Ubuntu will often default to putting the sound on Mute; you probably want to check the sound applet towards the right of your top panel, and try playing one of the sound files in the "Examples" folder on your desktop.

---

### Post by roccity1 on 2011-05-06
Ok how did you install the drivers for your card? Did just install from the apt-get or did you use the Additional Hardware option in the menu?

As for the sound you can open a terminal and type alsamixer. it should give you a display of your sound options. make sure that at least master,pcm and speaker all have a green box at the bottom of the bars. If not use the left and right arrows and to activate it just use your arrow keys and highlight the bar that is not green and hit the spacebar. You can use the up and down arrows to adjust the volume as well for each option.

Hope this helps.

---

### Post by Demothe7 on 2011-05-06
OK, I tried muting and unmuting the sound and it had no effect, and I ran the sound tests, still nothing. Roccity I THINK I used additional hardware, not too sure though, and the main problem right now guys, is I'm stuck on tty line command and can't get onto the GUI desktop =[

---

### Post by Demothe7 on 2011-05-06
OK I'm back on the Desktop but it looks like this:



sorry if the image is huge, i cant really tell because of the messed up sizes =[, if someone could just tell me how to get into Dash from that, I can change the overscan compensation settings and if that fixes the screen sizing i can work on getting the sound working THEN i might be able to DO something with Linux other than solving problems =[

EDIT: ok the image isn't there, i'll post it when i get time

---

### Post by Demothe7 on 2011-05-21
ok (sorry for the wait, loads of stuff on my plate lol) i managed to get into the nvidia control panel through the terminal and i adjusted the overscan compensation and in doing so, discovered that the top, bottom and dash panels aren't just not being displayed, they're actually ***not there*** anymore, so if you guys know of anything i can do to get them back, i'd be extremely grateful, and i'd like to say thank you for all your help thus far :)

---

### Post by Hedgehog1 on 2011-05-22
Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

There will be some error messages - ignore them please.

Logout **<ctrl> + <alt> + <Delete>** and reboot...


***The Hedge***

:KS

---

### Post by Demothe7 on 2011-05-22
I was just about to write to say that I managed to fix the problem with help from a page that i cant find again lol but the top bar disappeared when i tried out the different effects in CCSM but when i use the workspace switcher i can see it but then when i go into a workspace it goes again lol, still havent found a fix for the sound tho :(

---

### Post by Hedgehog1 on 2011-05-22
If the sound is 'Audio over HDMI', I have the fix for that, too:

[**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294")

***The Hedge***

:KS

*p.s. How are your tonsils?  Did they have to come out?*

---

### Post by tpprynn on 2011-05-22
When I used Xubuntu 11.04 recently the sound was set to the wrong type of output in the applet you get by clicking the volume icon and choosing Sound Preferences in one of the tabs. I've gone back to Gnome so I can't describe this better.

Another time I got no sound because my pc's BIOS was set wrong - if you have two audio options there maybe try the other. Oddly with my ASUS motherboard I have to set it to the 'wrong' setting for my audio chip to get any sound...

Are you saying that the screen resolution is wrong or just that panels are missing? Does the text look too big and blurred? Do you know what resolution your monitor has? I remember a solved thread for the FX5200 started by 'frankwakeman', which as old as that card is might show you better the form for a xorg.conf file that would put your display right. Post number #15 here in particular:

[http://ubuntuforums.org/showthread.php?t=1031885&highlight=frankwakeman+fx5200&page=2](http://ubuntuforums.org/showthread.php?t=1031885&highlight=frankwakeman+fx5200&page=2)

A bit more googling pertaining to your actual monitor/card would tell you what to put in place of certain lines, like for HorizSync and VertRefresh.

Sorry if I've missed the point or this is no use, but it sounds like a lead to me.

---

### Post by Demothe7 on 2011-05-22
I think I've fixed the display problem so far, now I'm just trying to get the sound to work and I have two ouputs, NVIDIA GeForce GTS 450 and the normal hda intel chipset, I'll have a nose around the BIOS now, see what's going on, and get back to you, thanks :)

---

### Post by Demothe7 on 2011-05-22
Yaaay it's fixed! I switched the sound output device to ***Digital Stereo (HDMI) nr2 Output*** and now I can finally hear her majesty, the nerd-queen Nixie Pixel's dulcet tones :D thanks for all the help guys, couldn't have done it without ya!:p

---

### Post by Hedgehog1 on 2011-05-22
***[SIZE="3"]HURRAY!!![/SIZE]***

Hedgie Happy Dance going on over here!


***The Hedge***

:KS

---

