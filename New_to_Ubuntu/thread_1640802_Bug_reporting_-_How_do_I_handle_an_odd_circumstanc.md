---
title: "Bug reporting - How do I handle an odd circumstance"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by getut on 2010-12-08
Hello,

I need help filing a bug report and I have some special circumstances because it will involve some proprietary software. I don't know whether the bug is because of the proprietary software a specific package I have installed from the Ubuntu repos. Let me first explain the bug...

I have 2 64 bit Ubuntu Maverick desktops that have VMWare Workstation 7.1.3 installed. Because these are corporate machine, we also run the x11vnc package (as opposed to the Ubuntu native VNC) so that we can connect to our Ubuntu linux desktops even if no one is in front of them or if they are sitting at the gdm sign on.

The problem is that as of Maverick Meerkat, this combination of software crashes gdm when a virtual machine is started. If x11vnc is disabled, then a VM can be started with no problem.

I have no idea whether this needs to be reported as an Ubuntu x11vnc bug or a VMWare Workstation bug or even how to narrow it down.

We have been using this combination of software since all the way back at Edgy Eft and have used every release since.

---

### Post by philinux on 2010-12-08
> **getut said:**
> Hello,

I need help filing a bug report and I have some special circumstances because it will involve some proprietary software. I don't know whether the bug is because of the proprietary software a specific package I have installed from the Ubuntu repos. Let me first explain the bug...

I have 2 64 bit Ubuntu Maverick desktops that have VMWare Workstation 7.1.3 installed. Because these are corporate machine, we also run the x11vnc package (as opposed to the Ubuntu native VNC) so that we can connect to our Ubuntu linux desktops even if no one is in front of them or if they are sitting at the gdm sign on.

The problem is that as of Maverick Meerkat, this combination of software crashes gdm when a virtual machine is started. If x11vnc is disabled, then a VM can be started with no problem.

I have no idea whether this needs to be reported as an Ubuntu x11vnc bug or a VMWare Workstation bug or even how to narrow it down.

We have been using this combination of software since all the way back at Edgy Eft and have used every release since.

Open a terminal.

```
ubuntu-bug x11vnc
```

If the package is incorrect the launchpad folks will change it. At least the bug gets reported.

---

### Post by krunge on 2010-12-08
There are a lot of Xorg X server bugs that are released in Ubuntu.

The most recent one is worked around by supplying the "-noxrecord" option to x11vnc.

And older one, still not fixed I think, requires the "-noxfixes" x11vnc option to work around it.

Try them in that order (and finally both if needed) and see if it solves your problem.

---

