---
title: "Having to manually type in &quot;modprobe ndiswrapper&quot;"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by t0ksik on 2007-12-03
Every time my computer starts, I have to type in "sudo modprobe ndiswrapper" to get my wireless to work.

The problem started when one of two things happened.  I was playing around with the services and I unchecked the dbus service.  Obviously I started having all kinds of problems with my network until I started the services again.  I rechecked the dbus services but then I had trouble with HAL (the popup box that says "Failed to initialize HAL".  I finally figured out that my rc2.d folder had things a little bit backwards.  Apparently when I rechecked the dbus services it had setup the script and named it S50dbus while HAL was started via S12hal.  Once I renamed S50dbus to S12dbus that error box went away.

The other thing I did was use ndiswrapper to wrap my Dell 1501 Broadcom driver because I was having a lot of trouble with the "default" driver dropping the signal and not connecting well at my university.  I got my driver to work well, but every time my computer starts, I have to type in "sudo modprobe ndiswrapper"

I tried "ndiswrapper -m" but that didn't work, and if I type it now it says
```

ben@ben-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

```

I am fairly new at linux but fairly good at reading forums (that's how I figured out how to fix the HAL problem) but I can't get this one.  Any help would be appreciated.  I am not sure if I broke it when I unchecked the dbus service or if I missed a step when following the NDIS tutorial.

---

### Post by elctb on 2007-12-03
Add this line to the /etc/modules file (must be on a line by itself):

```
ndiswrapper
```

---

### Post by Can+~ on 2007-12-03
I don't know how to solve your problem (since I use a wired connection), but if it's of any help, instead of having to type a command each time you could open System>Prfereences>Sessions and add the command so it's executed on loading.

Hope you find a solution :KS

---

### Post by t0ksik on 2007-12-03
Thanks to both of you for the quick reply.

elctb I did what you said and that fixed it.

---

