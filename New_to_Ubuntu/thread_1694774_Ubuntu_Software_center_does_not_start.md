---
title: "Ubuntu Software center does not start"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by rojen on 2011-02-24
I loaded Ubuntu Ylmf on an Acer e-machine laptop AMD64 athlon.

I used software center to add vlc.

I started update manager. It said updates available. I updated everything.

I restarted update mngr it sad 10.10 available. I installed it. (12 hrs)

It still says 10.10 available, but then when I click it it says nothing to update.

I wanted to add CreBS so I tried to start software center.  It spins the little wait wheel for a bit, then goes away.

How do I get access to software center back.

I am not that good at linux. I try it once a year to see if I can get rid of windows, eventually I've gone back to windows. But this year, it looks like there are software equivalents for everything I need. I hope I can stay, lol.

thanks, Rojen

---

### Post by rojen on 2011-02-25
I thought I would launch it from a terminal so maybe I could see the error?

So i did a quick search of the file system for *software center* and got lots of stuff, files, directories.

I never identified the executable tho.  I also have no idea what switches if any it is executed with.

I tried to find the properties from the menu launch button, but clicking does not have that as a choice and left clicking just gives another failed launch attempt without feedback.

Any ideas of how to launch it to get feedback?

Thanks

---

### Post by oldos2er on 2011-02-25
The command to run Software Center is **software-center**

---

### Post by corncob on 2011-02-25
I'd try reinstalling Software Center:
```
sudo apt-get install software-center
```
In the meanwhile, if its still working (as it is another part of the same thing), I'd use System > Administration > Synaptic Package Manager.

---

### Post by rojen on 2011-03-06
Thanks for the replies. I was gone traveling and was just got back.

I tried reinstalling it first. 
sudo apt-get install software-center

It told me I had the latest version:
software-center is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.

So I executed software-center. Here is what it printed out:
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 37, in <module>
    from softwarecenter.db.application import Application, DebFileApplication
  File "/usr/share/software-center/softwarecenter/db/application.py", line 31, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 127, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 116, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named Ylmf_OS


The first parts with lines 88, 37, 127, and 116 - are those normal>?

The last part is the derivative I am running. (This is my wifes old laptop and it gives her the familiar windows feel, which is why I chose Ylmf_OS.)

Any suggestions? Can I find the script and comment out that line?

Thanks, Ron

---

