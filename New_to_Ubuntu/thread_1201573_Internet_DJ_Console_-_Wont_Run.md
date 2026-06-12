---
title: "Internet DJ Console - Wont Run"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by useLinux, on 2009-07-01
Internet Dj Console (idjc) wont run for some reason. Installed fine as far as I know and when I try to run it I get asked which profile I'd like to choose. Highlighted is default so I click okay and nothing. It's like the process was killed. I went into terminal and ran 

```
/usr/bin/idjc
```

I get this output:

```
mark@Marks-Computer:~$ idjc
Internet DJ Console Version 0.7.7
Copyright 2005-2008 Stephen Fairchild
Released under the GNU General Public License V3.0

Language translation: en_GB
/usr/lib/python2.5/site-packages/idjcgui.py:1565: DeprecationWarning: os.popen2is deprecated.  Use the subprocess module.
  self.mixer_ctrl, self.mixer_rply = os.popen2([ libexecdir + "idjcmixer" ], 4096)
no message buffer overruns
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 2360, in <module>
    run_instance = MainWindow()
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 1731, in __init__
    self.mic_select = nice_mic_togglebutton()
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 225, in __init__
    gtk.ToggleButton.__init__(self, label, use_underline)
RuntimeError: more argument specifiers than keyword list entries (remaining format:'):GtkToggleButton.__init__')
mark@Marks-Computer:~$ Mixer module has closed

```

I'm fairly new around linux to be honest so I have no clue as to what this really means. My guess would be some sort of error in the actual code. No idea why.

Running Kubuntu 9.04 btw.

Thanks in advance guys

-useLinux,

---

### Post by StephenF on 2009-07-03
The Ubuntu package for IDJC is a year out of date and will not run. Follow the 
link for instructions to compile a more recent version of IDJC from source:

[http://ubuntuforums.org/showpost.php?p=5200135&postcount=5](http://ubuntuforums.org/showpost.php?p=5200135&postcount=5)

---

