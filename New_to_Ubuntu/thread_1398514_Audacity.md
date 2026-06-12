---
title: "Audacity"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by squrl on 2010-02-04
I have installed audacity in Hardy. There is no sound out. It says to check 'output device settings' Where will I find output device settings. I have tried every button I can find and no such animal.

Thanks

---

### Post by Hendronicus on 2010-02-05
You need to edit the menu entry for it and add "aoss" w/o quotes to the beginning of the command line. This will create a dsp device for it before it runs. I have only tested this in Gutsy, but it should still be the same.

---

