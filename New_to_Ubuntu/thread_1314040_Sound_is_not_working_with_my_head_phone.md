---
title: "Sound is not working with my head phone"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by mi6crazyheart on 2009-11-04
Hello.....
I'm totally a new user of Ubuntu. This is the first time I'm using Ubuntu. From a couple of days I'm exploring it. Yet every things are going fine except one thing. That is my head phone is not working with it. But, my that is working fine . 

First when i got this problem i checked in that "**Sound Preference** (System>Preferences>Sound)" Control Panel. At there i got 2 type of connector are available. One for **Analog Output** & another one for **Analog head phone**.When i'm selecting the **Analog Output** connector my external sound system is working fine but when i'm selecting **Analog head phone**(which i suppose to think used for Haed phone) connector my Head Phone is not working with that. 

By d way, I'm also using a Windows XP OS too for my development work. At there every things are working absolutely fine (Both external sound system & Head Phone).The Mother Board model of my System is - Intel 915GLVG

Please, any one can help me a bit to solve this problem.

---

### Post by laidback on 2009-11-04
Try this as it's the only solution I can think of.
Top right of the Taskbar is an icon for a loudspeaker, press it and you get a volume control slider. But there is also a button called "Volume Control..", press it and you will see a new window called "Volume Control". At the top of this window you will find a drop down that let's you choose which device you want to adjust, select the one you want, if you're not sure you'll have to use trial and error. In the space below will appear slider(s) for the various options associated with the selected device. Make sure the red cross on the loudspeaker icon at the bottom of any slider is removed (click it) so that you activate that output (or input depending on which slider it is), now move the slider upwards to increase the volume. If you cannot see a slider for what you need press "Preferences" and the associated options will appear, tick to activate that option within the slider display window.

It's worth a try.

Good luck and welcome to Ubuntu.

---

### Post by Bunnybugs on 2009-11-04
Maybe your headphones are muted in Alsa(you can't get there without terminal in 9.10 Karmic)

Go to Terminal (Applications>Accessories>Terminal),

Typ:
```
alsamixer
```

move to the right with your cursor-keys to Headphone, and press 'M' if it says '[COLOR=Blue]MM[COLOR=Black]'

Press 'Esc' and try again with your headphone.

If this doesn't solve the problem, I can't help you... Then you have to ask someone else.
[/COLOR][/COLOR]

---

### Post by mi6crazyheart on 2009-11-05
Hey , Thx for u'r suggestion. As u'd told that, there might be a button called "Volume Control" on the top right task bar. But, i didn't get any such button. 
Here is my Desktop image I'm giving ([http://img94.imageshack.us/i/screenshotpp.png/](http://img94.imageshack.us/i/screenshotpp.png/)).
Have a look , there is not such Volume Control Button except those Loud Speaker icon, Wired Network connection icon.

Hey, can u say one thing, that..... Is that possible to use both the Head phone  & External sound system simultaneously by connecting all the jack(Jack of external sound system + jack of Head Phone)  to the available input points. Because, i've notice that..... I've 3 input points in my Mother board for inserting 3 jack. What i generally do in my XP is..... i connect all my jack(3=2 from my Head phone+ 1 of my external sound system) to the available inputs points & set them properly by going to the audio driver Control Panel. So, i never need to Plug in & Plug out Jacks any time whatever device(Head Phone/Sound system) i want use.

But, thing what here is happening in Ubuntu that, from out of 3 jack input available points only 1 is working. So, whenever i'm Plug in any 1 of my audio device jack(Head phone/External Sound system) that is working. Due to this i can't able to use both of my audio device simultaneously. Every time I've to plug in & plug out my Jacks according to the device i want to use.

So [laidback]("http://ubuntuforums.org/member.php?u=187456") , is this the default way in which it works in Ubuntu or their are some short of setting problem which i can't find out properly.

---

