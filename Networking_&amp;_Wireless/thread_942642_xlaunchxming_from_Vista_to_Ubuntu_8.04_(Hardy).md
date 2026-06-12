---
title: "xlaunch/xming from Vista to Ubuntu 8.04 (Hardy)"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by kedmond on 2008-10-09
Thanks for reading my post.

I am on a LAN at work, and I have a laptop running Vista and a desktop machine running Ubuntu 8.04.  I would like to access the Ubuntu machine from my laptop, and see its desktop.  I guess this uses GDM or something...not sure.  Anyways, I installed Xming and Xlaunch on my computer.  I am using ssh, not putty, btw.  I activated X11 packet forwarding, and was able to run Xming and then login using SSH and launch an xterm on my laptop from the desktop machine.  So that was good.

But now, I am trying to use Xlaunch.exe (the wizard for Xming) to run an XDMCP session to remotely login to the ubuntu computer from the laptop.  This isn't working so well.

I've followed the instructions found here: [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Remote_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Remote_Desktop)

As of now, the Xserver window opens up and closes repeatedly, and I see Gnome's spinning wheel cursor when the window is open.  If I tell XLaunch to login indirectly, then I successfully get a "remote login" window to pop up under Ubuntu that lets me choose another XDMCP server, but that doesn't help.

I'm not sure how to post an error log since the Xming taskbar icon doesn't linger long enough for me to rightclick and selet "error log".  As I said above, the Xserver windows rapidly opening/closing, so I have to go to Task manager and end the process.

Any help would be appreciated, thanks.

-Kazem

---

