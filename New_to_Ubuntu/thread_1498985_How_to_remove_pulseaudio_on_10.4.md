---
title: "How to remove pulseaudio on 10.4?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by shuqi on 2010-06-01
Hi,

I am running ubuntu 10.4 as a vmware guest and everything is running fine except for pulseaudio starting to hog all available resources every few minutes.
I actually don't need sound at all for this guest, so that I tried uninstalling pulseaudio. However, that comes up with the warning that it will also remove ubuntu-desktop, which I assume will render gnome unusable?

Even disabling all sound devices and muting any remaining sound settings still causes pulseaudio to take up all the resources.

Is there a way to remove pulseaudio or at least disable it so that it will no longer restart automatically?

I tried 
chmod -x /usr/bin/pulseaudio
but then indicator-sound and indicator-apple processes appear and they also start taking up a lot of cpu resources.

Any help getting rid of pulseaudio or to remove sound completely would be appreciated.

---

### Post by marty1011 on 2010-06-01
try to follow the instructions on this site and see if they work

[http://www.jeffsplace.net/node/12]("http://www.jeffsplace.net/node/12")

---

### Post by shuqi on 2010-06-01
Thank you.

I just made a copy of the VM and gave

sudo apt-get purge pulseaudio

a try, which actually worked out.
Gnome is still running without a problem and sound has been globally disabled.
So far the system is finally running smooth without any spikes in the resource usage.

---

