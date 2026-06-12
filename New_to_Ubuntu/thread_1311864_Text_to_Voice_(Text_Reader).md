---
title: "Text to Voice (Text Reader)"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by rDwyP44y on 2009-11-02
Is there such a program on Ubuntu that can read text (english text)

and out put Audio?



I got this 300 page e-book from a friend, but reading this on the LCD screen really hurts my eyes!


I would actually prefer to copy n paste this text into some program that would READ the text to me!


I'm not sure if this fall's under this forum, but thanks for your help.

---

### Post by nwadams on 2009-11-02
I personally have no idea how to do this...however the guy who made post 5 in that thread seems to know what he is doing.
[http://ubuntuforums.org/showthread.php?t=918099](http://ubuntuforums.org/showthread.php?t=918099)

good luck. If that doesn't work try doing ubuntu forums or google searches wiht things like text to speach or text reader (add linux or ubuntu if doing google searches)

---

### Post by johnaaronrose on 2009-11-12
I installed text reader on a netbook using UNR karmic and a laptop using ubuntu karmic. It works fine on the netbook but fails on the laptop. Running it from terminal on the laptop gives:
administrator@JohnLaptop:~$ python /usr/share/textreader/textreader
Traceback (most recent call last):
  File "/usr/share/textreader/textreader", line 7, in <module>
    import wx.richtext as rt
ImportError: No module named richtext

Python version is 2.6.4 (found by running python in terminal).

richtext.py is in /usr/lib/python2.6/dist-
packages/wx-2.8-gtk2-unicode/wx but not /usr/lib/python2.6/dist-
packages/wx-2.6-gtk2-unicode/wx. Is this significant? BTW on the
netbook, richtext.py is in /usr/lib/python2.6/dist-
packages/wx-2.6-gtk2-unicode/wx but there is no /usr/lib/python2.6/dist-
packages/wx-2.8-gtk2-unicode/wx directory.

I have no knowledge of python. So any help needs to be clearly explained. Thank you.

PS  /usr/share/textreader/textreader's first few lines are:
#!/usr/bin/python

#Text Reader
import wx
import os
import tl
import wx.richtext as rt
[COLOR=#888888]
[/COLOR]

---

### Post by philinux on 2009-11-12
> **rDwyP44y said:**
> Is there such a program on Ubuntu that can read text (english text)

and out put Audio?



I got this 300 page e-book from a friend, but reading this on the LCD screen really hurts my eyes!


I would actually prefer to copy n paste this text into some program that would READ the text to me!


I'm not sure if this fall's under this forum, but thanks for your help.

espeak is already installed. It command line text to voice.

```
man espeak
```

Also search speech synth in synaptic.

---

