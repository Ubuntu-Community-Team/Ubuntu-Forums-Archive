---
title: "Ubuntu Tweak Windows Management Problems."
date: 2010-05-14
forum: New to Ubuntu
---

### Post by metici on 2010-05-14
Hello all,

I am currently running Ubuntu 10.04 and after updating I've been having a problem with my windows management. I usually go to Ubuntu Tweak to deal with my windows but, when I clicked on the panel it gave me this error message:

Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/ubuntutweak/mainwindow.py", line 393, in setup_notebook
    page = module()
  File "/usr/lib/pymodules/python2.6/ubuntutweak/modules/metacity.py", line 127, in __init__
    buttonview1 = ButtonView()
  File "/usr/lib/pymodules/python2.6/ubuntutweak/modules/metacity.py", line 51, in __init__
    self.update_model()
  File "/usr/lib/pymodules/python2.6/ubuntutweak/modules/metacity.py", line 74, in update_model
    self.COLUMN_LABEL, self.values[k])
KeyError: ''

---

### Post by nhasian on 2010-05-14
why do you need Ubuntu Tweak?  I've never used it.  I just install any codecs or flash etc manually myself.

---

### Post by metici on 2010-05-14
well, I find that Ubuntu Tweak generally makes my life easier. However, in this case, it hasn't.

---

### Post by nhasian on 2010-05-14
you could report a bug of Ubuntu Tweak [here]("https://bugs.launchpad.net/ubuntu-tweak/+filebug") or you can ask a question directly to them [here]("https://answers.launchpad.net/ubuntu-tweak/+addquestion")

I hope this helps

---

