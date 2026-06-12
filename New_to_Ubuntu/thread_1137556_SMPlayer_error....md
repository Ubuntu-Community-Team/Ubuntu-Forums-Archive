---
title: "SMPlayer error..."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-25
I'm trying to play back a DVD in SMPlayer but I get the error:

```
mplayer -noquiet -nofs -afm hwac3 -sub-fuzziness 4 -identify -slave -vo xv -ao oss -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 41943052 -monitorpixelaspect 1 -fontconfig -font Comic Sans MS -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -dvd-device /media/cdrom0 -chapter 1 -dvdangle 1 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af scaletempo dvd://1

The sub-fuzziness option must be <= 2: 4
Error parsing option on the command line: -sub-fuzziness
MPlayer SVN-r29220-4.3.2 (C) 2000-2009 MPlayer Team
```

---

### Post by rvm4000 on 2009-04-25
Something strange happened, smplayer is passing to mplayer *-sub-fuzziness 4* which is completely wrong.

Go to Preferences -> Subtitles and change the autoload option.

---

### Post by kamitsukai on 2009-04-26
> **rvm4000 said:**
> Something strange happened, smplayer is passing to mplayer *-sub-fuzziness 4* which is completely wrong.

Go to Preferences -> Subtitles and change the autoload option.

Using any of the settings in the drop down box for autoload gives the same error:confused:

---

### Post by rvm4000 on 2009-04-26
What version of smplayer are you using?

I can't reproduce the problem...

Edit the file ~/.config/smplayer/smplayer.ini and delete the "subfuzziness=" line.

---

### Post by kamitsukai on 2009-04-26
> **rvm4000 said:**
> What version of smplayer are you using?

I can't reproduce the problem...

Edit the file ~/.config/smplayer/smplayer.ini and delete the "subfuzziness=" line.

now I get:

```
mplayer -noquiet -nofs -afm hwac3 -sub-fuzziness 4 -identify -slave -vo xv -ao oss -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 44040204 -monitorpixelaspect 1 -*** -embeddedfonts -***-color ffffff00 -***-border-color 00000000 -fontconfig -font Comic Sans MS -subfont-autoscale 1 -***-font-scale 1 -subcp ISO-8859-1 -aid 1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af scaletempo /home/carl/shameless.S6 e14.ws.pdtv.xvid.avi

The sub-fuzziness option must be <= 2: 4
Error parsing option on the command line: -sub-fuzziness
MPlayer SVN-r29220-4.3.2 (C) 2000-2009 MPlayer Team

```

same isn't it? and I'm usi9ng the smplayer which you get from the ubuntu repositorys in ubuntu

---

### Post by kamitsukai on 2009-04-26
Sorted the problem! just deleted my .SMPlayer folder should of done that in the bggining...

---

