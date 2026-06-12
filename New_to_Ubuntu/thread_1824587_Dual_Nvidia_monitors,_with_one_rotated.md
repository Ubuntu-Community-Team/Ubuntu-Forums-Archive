---
title: "Dual Nvidia monitors, with one rotated"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by rufwork on 2011-08-14
Okay, I'm not 3 hours old as an Ubuntu user, so Absolute Beginner Talk it is.

I've installed Ubuntu 11.04 64 bit and everything seems happy.  I've been using a second monitor that's rotated with this machine in Windows, and want to do the same in Linux.  I've removed the Windows drive and installed another internal hard drive for Ubuntu.  All I've got plugged in is a keyboard and mouse.

I've used the Nvidia configuration deal (Nvidia X Server Settings) to make the second monitor active, but it wants me to restart X.  I haven't had any luck getting that to work.  I've found a recent post trying to do pretty much exactly what I want to do here:

[http://viktorstanchev.com/blog/ubuntu-11.04-rotate-only-one-of-two-monitors](http://viktorstanchev.com/blog/ubuntu-11.04-rotate-only-one-of-two-monitors)

Following those instructions, I get jammed when I log out and try to log back in.  Initially, the box stopped while (I think) shutting down on "Stopping System V Run Level Compatibility".  There's a thread on that here: [http://ubuntuforums.org/showthread.php?t=1823970](http://ubuntuforums.org/showthread.php?t=1823970)  ... but I really don't think it's the disk.  I haven't really done anything but install and change xorg.conf.

I do get the "failed to parse existing X config file" when I try to save from the Nvidia configurator that's described here: [http://www.wetware.co.nz/blog/2009/10/failed-to-parse-existing-x-config-file-etcx11xorg-conf/](http://www.wetware.co.nz/blog/2009/10/failed-to-parse-existing-x-config-file-etcx11xorg-conf/)

Doing exactly what that page says -- running sudo nvidia-config -- does fix that issue, or at least make the file parseable.

I rebooted the machine after it hung, and now I'm stuck on Checking Battery State...  I had that happen the first time before I found that vikorstanchev.com blog and ended up reinstalling.  I had it happen when I tried not using Absolute positioning for the second monitor when I otherwise followed Viktor's instructions too.  Using my backup conf file fixes the issue when I ctrl-alt-F2 out, login, cp it over, and then sudo reboot.

Any luck?  Seems like this should be easier, which makes me think I'm doing it wrong.  I'm using an Nvidia 8500 GT (specifically [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127295")).

TIA.

UPDATE: If I reboot (rather than logging out and back in) after enabling the second monitor in Nvidia X Server Settings with Xinerama on, I get a log in screen and once I log in I get both monitors active (not rotated, of course).  But it never displays anything else but the mouse pointer and the background.  Right clicking does nothing.  Jumping to Ctrl-Alt F2 and back to Ctrl-Alt F7 [sic] gives me a black display with a moveable pointer, but that's it.

Twinview works fine, except that I want the second monitor to be rotated, so, um... ;^)


UPDATE 2: I have no idea what I did "right", but I first did Twinview, rebooted instead of logging out, and Twinview worked.  I then did Separate X Screen with the Nvidia X Server Settings applet or whatever with absolute positioning as Viktor suggested, and again rebooted instead of logging out.  I did NOT click "Enable Xinerama", however.  Logged back in, everything's happy.  Then I edited xorg.conf by hand to add the Option "Rotate" "left" to the second display.  Rebooted.  Voila.

Who knows.  I've got copies of the xorg.confs that didn't work, so I guess I'll diff them and report back at some far future date. I'm suspicious I may have told Nvidia X Server Settings to merge the xconf's initially.  I'm pretty sure you want to leave that unchecked.

So I can move the mouse from one to another, but I can't actually move windows between them.  If I create a new file in the rotated monitor on the left, I can double click and have it open a gedit window in the rotated monitor (and have it oriented correctly), but I can't type in it or otherwise interact.  When the mouse is in the second monitor, PrintScreen doesn't take a picture; it does nothing.

UPDATE3:  This unresponsive window issue is apparently a known bug:
[http://ubuntuforums.org/showthread.php?t=1779863](http://ubuntuforums.org/showthread.php?t=1779863)

It's also been reported:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/764051](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/764051)

In that second URL, you get [a fix too]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/764051/comments/4"):
> Because keyboard doesn't work on second screen I run this command on first screen: DISPLAY=:0.1 compizThat worked for me, at least.  You can also downgrade compiz, whatever that is, but that apparently also involves uninstalling Unity for Gnome.  I'm well outside of my comfort zone there, and will just stick with the kludge for now, I guess.

I also tried changing the Window Manager to something I can't remember now.  I'll try to dig it up.  It didn't fix the issue, but I can't say it wasn't a contributor later without figuring out what I did do (it was late; I forget).

So I have two monitors, one rotated, and windows that work on both.  Unfortunately I can't move windows between monitors, but that's apparently expected.  I also have to get creative to have anything appear on the second monitor.  

Tricks to get jive on the second window: 
1.) Right click the second monitor's desktop, create a folder, double click it, and you've got a directory explorer.  Double-click an app from there.  
2.) Open a term on the second monitor with a script: 

gnome-terminal --screen 1&

Now open stuff from the term with commands like "google-chrome" or whatever.

Then I have to open apps from the term or move their icon (or create a link) to get them on that second monitor.  Not being able to move windows between monitors and having to open in the monitor I want to use an app in is annoying, but I can stomach that.

Hopefully this post will be useful for someone.

---

