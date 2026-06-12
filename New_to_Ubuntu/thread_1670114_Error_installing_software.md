---
title: "Error installing software"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by D-Train on 2011-01-18
Hi guys,
I tried to install a program using Ailurus and got the following error message. Can anyone interpret for me what happened and tell me how I can fix it?

('Ubuntu', '10.10', 'maverick')
('Linux', 'Toshiba Laptop', '2.6.35-24-generic', '#42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010', 'i686')
Ailurus version:  10.10.5
Youtube-dl: Download videos from Youtube
Traceback (most recent call last):
  File "/usr/share/pyshared/ailurus/install_remove_pane.py", line 406, in __apply_change_thread
    obj.install()
  File "/usr/share/pyshared/ailurus/libapp.py", line 351, in install
    BACKEND.install(*self.pkgs.split())
  File "/usr/share/pyshared/ailurus/lib.py", line 931, in install
    run_as_root_in_terminal('apt-get install %s' % ' '.join(packages))
  File "/usr/share/pyshared/ailurus/lib.py", line 770, in run_as_root_in_terminal
    else: raise CommandFailError(command)
CommandFailError: apt-get install youtube-dl

I haven't tried to install this program using the Ubuntu Software Center or Synaptic Package Manager. Should I try using one of those instead?

---

### Post by erudite on 2011-01-18
Yes try and install it using the software centre or synaptic.

---

