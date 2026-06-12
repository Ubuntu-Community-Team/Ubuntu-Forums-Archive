---
title: "Help with setting up a trust tb-6300 on karmic... ..."
date: 2009-11-26
forum: New to Ubuntu
---

### Post by techno-mole on 2009-11-26
Hello.

I have been trying to get my graphics tablet to work on karmic (32 bit, i switched from 64bit)

I did try to get it running on 64bit, but I failed, badly, so now Im on 32 bit, but doing a little better, I can get the pen to move the cursor, sort of, even after running the wizard pen calibration the dimensions seem odd, and moving the stylus is very odd as well, it will shoot from the top to the bottom of the screen, and is generally very erratic.

I have tried various things, and I think that may be the reason Im having issues, the original how to is from here - ```
https://help.ubuntu.com/community/TabletSetupWizardpen
```

but this didnt seem to work very well, and after reading various posts and articles I came to the conclusion that I needed and fdi file as well, and the how to mentioned doesnt seem to mention one ?
if I run " xinput --list " I get ```
"UC-LOGIC Tablet WP8060U"	id=9	[XExtensionPointer]
	Type is WizardPen Tablet
	Num_buttons is 6
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1440
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 900
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1000

```
and running this " cat /sys/bus/usb/devices/*/product " gives me this ```
Tablet WP8060U

```
I have installed the wizard pen driver as the how to mentions, and as far as I can tell everything went okay, running this command - ```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
```

gives me - ```
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so
```

but now I am stuck, I have used the wizard pen calibrate function, but this has yielded some odd stuff as well, even after following the instructions to the letter, the cursor moves in an odd way, I even tried the configuration file from the how to for my tablet (last ditch attempt) 

any help would be appreciated, I bought the tablet to help me with my image editing (into digital photography) and I like gimp, but dont want to have to revert to using xp, especially when the tablet is in the list of working tablets.

thanks in advanced for any help.

PS - update, I have been messing around with the fdi file (again) I am making progress, but I am still not sure if what I have is right, here is my fdi file ```
<?xml version="1.0" encoding="ISO-8859-1" ?>

<deviceinfo version="0.2">
  <device>
        <!-- This MUST match with the name of your tablet -->
    <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.topZ" type="string">5</merge>
      <merge key="input.x11_options.bottomZ" type="string">1024</merge>
      <merge key="input.x11_options.maxZ" type="string">1024</merge>
      <merge key="input.x11_options.TopX" type="string">826</merge>
      <merge key="input.x11_options.TopY" type="string">2626</merge>
      <merge key="input.x11_options.BottomX" type="string">32747</merge>
      <merge key="input.x11_options.BottomY" type="string">32762</merge>
      <merge key="input.x11_options.MaxX" type="string">32747</merge>
      <merge key="input.x11_options.MaxY" type="string">32762</merge>
    </match>
  </device>
</deviceinfo>
``` 

I have tried to add lines for pressure sensitivity, and it has sort of worked, but if anyone knows what they are doing (I dont, Im winging this) maybe you could take a look at the fdi file to see if it is at least halfway right.

cheers

---

### Post by techno-mole on 2009-11-27
Bump*  no one fancy a crack at this ?

I'm still messing and making some progress, although I am guessing at most of it.

---

### Post by drpjkurian on 2009-12-06
Hi
Why do not try my thread
[http://ubuntuforums.org/showthread.php?t=1337260](http://ubuntuforums.org/showthread.php?t=1337260)

With regards
Dr Kurian

---

### Post by techno-mole on 2009-12-09
i did have a look at your thread, it was helpful, more helpful than the wiki entry i was working off, that doesnt seem to mention the creation of an fdi file (if it does i must have missed it)

i am using the fdi file i posted previously and it seems to be working, i did try and use the calibrate tool, but for some odd reason it doesnt seem to give the right set up, in the end i used a combination of the settings from the wiki entry this one - ```
https://help.ubuntu.com/community/TabletSetupWizardpen
``` in case you were wondering.

i did some of the steps from that and some from your guide in the end, i installed etc using the wiki and then found your thread after doing some research and finding out that i would need an fdi file (i should have guessed really as i had to create one for my trackball mouse) 

i have it running, with pressure sensitivity as well, and it works great, i had to use the configuration file from the wiki, well bits of it anyway because of the calibration issue, i guess that if its working as it should then the fdi file is okay.

funny because i got it all set up to work (even on my virtual machine and on adobe elements running through wine) and it turns out that gimp isnt in the application stack for the next ubuntu release (lucid lynx) i assume it will be in the repos' ? but if not i (along with other people) will have to install from source if i/we upgrade to lucid, although to be honest i have upgraded every new release since i started to use ubuntu, im going to stay with karmic for a while, unless i have major issues.

cheers

---

### Post by Favux on 2009-12-09
Hi techno-mole,

> it turns out that gimp isnt in the application stack for the next ubuntu release (lucid lynx)
Yes it will be in the repos'.  They decided Gimp is too complicated for newbies and want to substitute something simpler (and smaller).  Plus Gimp is fairly "large" and they'd like to free up space on the install CD.

---

### Post by techno-mole on 2009-12-10
i can relate to that, up until a few months ago i didnt really use gimp, it wasnt until i did an open university course in digital photography that i actually used it to even a fraction of what it can do.

since then i have added various scripts and plugins and brushes etc etc, i prefer gimp to other editors (i also have photoshop and elements)

cheers

---

### Post by drpjkurian on 2009-12-10
Hi Technomole

Plaese share your Installation steps which you have 'invented' to your forum friends.

Thanks 
Dr Kurian

---

