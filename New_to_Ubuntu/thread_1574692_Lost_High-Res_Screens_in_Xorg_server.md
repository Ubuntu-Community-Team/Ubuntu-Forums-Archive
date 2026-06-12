---
title: "Lost High-Res Screens in Xorg server"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by bsalem on 2010-09-14
I lost the high resolution screens from my desktop.

The resolutions I need still work under Windows Vista and Knoppix 5.1.1 Live CD.

As per the indications of a similar issue reported here I am attaching the nvidia-bug-report.log.gz which appears to do all of the troubleshooting mentioned in several bug reports. I already know that the driver for my card refuses to load and as per my earlier posting to this forum I'd like to know precisely which packages to install with that exact card and my kernel version.

I had the high resolution screens for a year and they became unavailable as I was working doing something else, unrelated to upgrading, last week.

Seems like lots of people have problems with Nvidia Cards and several Ubuntu releases. Might I suggest someone write a support matrix?

---

### Post by realzippy on 2010-09-14
According to your nvidia-bug-report
you not seem to have a xorg.conf file.
xorg.conf.failsafe is used instead,which is vesa not nvidia.
Open a terminal and run
```
sudo nvidia-xconfig
```
to get a new xorg.conf.Then restart X/reboot

---

### Post by bsalem on 2010-09-14
I have done 'sudo nvidia-xconfig' many times, even today, and it fails. If you look at the attachment it says that the driver itself isn't loading. The xorg.config file is in there too and it is just the most generic. I think that the problem is that there isn't a support matrix for my kernel and card so that I know what packages to install to fix this. The GUI tools from the Administrator Menu in Gnome all fail and I only have the low resolution screens to choose from.

---

### Post by realzippy on 2010-09-14
Did the NVIDIA driver ever work?Wonder why you can create a nvidia-bug-report...?
If so,which driver was it and how did you manage to install that driver?



*I think that the problem is that there isn't a support matrix for my kernel*

try:
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by bsalem on 2010-09-14
The system was installed about a year ago and the high resolution screens did work until about a week ago.
I will try to reinstall the kernel header files.

The answer to your question is that the driver for the card did work, and I assume that it had to use hooks for that hardware to get 1440x900 resolution, the monitor is an  Emachines E19T6W, 19 inch wide and every
time it comes up with the low-res setting it tells me that it will do more and to have the OS I'm running do that. This OS won't do that, as it has become configured.

---

### Post by bsalem on 2010-09-14
I did the install linux-headers and things got worse. I lost the 800x640 screen and are left with the two lowest resolution screens. The graphics on this system are almost entirely useless. The only thing I am able to do is to use small fonts in a browser to use this editor to post this reply.

What is the CLI command to activate the Nvidia driver. I can't use the GUI now since it fills the screen add
will not let me activate it?
.

---

### Post by bsalem on 2010-09-14
The install-headers did finally result in my getting my high-res screens back.

Thank You

The only gotcha was that it too me to install the latest version of the driver to get it to
work, not the one picked up by the apt-get. It worked with 180 and not with 173 version.

Of course save the /etc/X11/xorg.conf, but how do I protect the driver from another failure?

I still don't know why this all happened, and I came this close to installing a different distro.

I regard this matter as resolved.

---

### Post by bsalem on 2010-09-14
I wanted to say that I wil come and hang out on some of these forums and try to give back. I have some
experience with this stuff.

Thanks again.
:D

---

### Post by realzippy on 2010-09-15
Fine you made it.Sorry for absence,but [CET]("http://www.timeanddate.com/library/abbreviations/timezones/eu/cet.html") here...

---

