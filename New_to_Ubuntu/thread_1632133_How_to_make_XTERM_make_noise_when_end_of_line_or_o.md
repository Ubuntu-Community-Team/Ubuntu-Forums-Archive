---
title: "How to make XTERM make noise when end of line or other?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-27
Hello 

I would like to run a wav when some actions under xterm, i.e. to make XTERM make noise when end of line or other?.

I saw that 
>  xset -b 
  can be used, but how to set a wav file for that ? 
xterm has ringing bell and visual bell

Best regards

---

### Post by honeybear on 2010-11-27
content of .xkb/xkbevd.cf
```
soundDirectory  = ""
soundCmd        = "mplayer"

Bell()                  "~/sounds.wav"
Bell(ImAlive)           "~/sound.wav"
```


then do:
xkbevd -bg 


> Disable the Automatic Sound
#
1

Navigate to Firefox's address bar, type "about:config" and press "Enter."
#
2

Type "typeahead" in the Filter field.
#
3

Double-click on the "accessibility.typeaheadfind.enablesound" option. Verify that the line turns bold and the value has changed to "false," as this signifies that the sound has been disabled.
#
4

Close all windows and restart the browser to enjoy a sound-free "Find in Page" function.


---

