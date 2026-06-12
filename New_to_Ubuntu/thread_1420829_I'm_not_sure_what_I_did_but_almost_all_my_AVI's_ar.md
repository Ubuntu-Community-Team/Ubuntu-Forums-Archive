---
title: "I'm not sure what I did but almost all my AVI's are missing their thumbnails."
date: 2010-03-03
forum: New to Ubuntu
---

### Post by diablo75 on 2010-03-03
I recently pulled Pulse Audio off my system which seemed to break the audio aspect of Totem but not VLC so I use VLC for all my media playback now and decided to remove totem.  Then a lot of my AVI files started to just have the same generic icon on them instead of a thumbnail image from the video.  I've since reinstalled Totem but this didn't seem to fix the problem so I'm not sure what else I'm missing.

---

### Post by Ghost|BTFH on 2010-03-03
> **diablo75 said:**
> I recently pulled Pulse Audio off my system which seemed to break the audio aspect of Totem but not VLC so I use VLC for all my media playback now and decided to remove totem.  Then a lot of my AVI files started to just have the same generic icon on them instead of a thumbnail image from the video.  I've since reinstalled Totem but this didn't seem to fix the problem so I'm not sure what else I'm missing.

Sounds more like an issue with Nautilus being Naughty...

Open up a folder in your system and go to Edit -> Preferences

Check through the tab Preview and make sure you have Other Previewable Files set up appropriately.  If you use a server, make sure it's set to Always, if you only use local files, make sure it's set for Local Only.

If that's the case, problem solved.  If not, let us know. :)

Cheers,
Ghost|BTFH

---

### Post by diablo75 on 2010-03-03
I actually already tried that but forgot to mention it.  I have it set to "Always" right now, but it didn't make a difference...

---

### Post by mcduck on 2010-03-03
Nope.That sure is related to removing Totem. Nautilus itself doesn't generate the thumbnails, it uses other programs to do that, and Totem being the default video player in Gnome is also the program that Nautilus uses as thumbnailer for video files.

To get the thumbnails back you'll probably have to set the relevant Gconf keys again. Start gconf-editor, browse to desktop/gnome/thumbnailers, and find all the video-related keys that don't have a thumbnailer set and set it to "/usr/bin/totem-video-thumbnailer -s %s %u %o" and then mark the checkbox to enable the thumnails.

Perhaps there's a simpler way to do this by just resetting all video-related gconf keys in this section to their defaults but you'll have to wait for somebody better in handling gconf keys from CLI comes up with a command to do that..

---

### Post by Ghost|BTFH on 2010-03-03
> **diablo75 said:**
> I actually already tried that but forgot to mention it.  I have it set to "Always" right now, but it didn't make a difference...

Okay, now that *is* odd.  I have a feeling it's still something going on with Nautilus...because I run pure ALSA on my system - Pulse-Free and happy with it, but I can view thumbs on all my avi's without issue...

The extreme solution would be to wipe your currently thumbs and force Nautilus to rebuild them.

[I]killall -9 nautilus
rm -r $HOME/.thumbnails/fail
rm -r $HOME/.thumbnails/normal
rm -r $HOME/.thumbnails/large[/I]

Then open up a folder, thus restarting Nautilus.  If that doesn't work, I am truly stumped.

Cheers,
Ghost|BTFH

---

### Post by diablo75 on 2010-03-03
> **mcduck said:**
> To get the thumbnails back you'll probably have to set the relevant Gconf keys again. Start gconf-editor, browse to desktop/gnome/thumbnailers, and find all the video-related keys that don't have a thumbnailer set and set it to "/usr/bin/totem-video-thumbnailer -s %s %u %o" and then mark the checkbox to enable the thumnails

Welp I took a look at that registry (is that what it's called?) and it appears every video@ entry DOES in fact already have the correct command in place and they are all enabled with the check box.  I also confirmed that the binary it points to (/usr/bin/totem-video-thumbnailer) is present on the system and not missing.

I will try the method in the post that came after yours to see if I can force a rebuild.

---

### Post by diablo75 on 2010-03-03
> **Ghost|BTFH said:**
> Okay, now that *is* odd.  I have a feeling it's still something going on with Nautilus...because I run pure ALSA on my system - Pulse-Free and happy with it, but I can view thumbs on all my avi's without issue...

The extreme solution would be to wipe your currently thumbs and force Nautilus to rebuild them.

[I]killall -9 nautilus
rm -r $HOME/.thumbnails/fail
rm -r $HOME/.thumbnails/normal
rm -r $HOME/.thumbnails/large[/I]

Then open up a folder, thus restarting Nautilus.  If that doesn't work, I am truly stumped.

Cheers,
Ghost|BTFH

THAT DID IT!

Thanks for the help!  Looks like all my thumbs are rebuilding correctly.

---

### Post by Ghost|BTFH on 2010-03-04
Rock on! :D :D :D

Very glad I could offer assistance.

Cheers,
Ghost|BTFH

---

