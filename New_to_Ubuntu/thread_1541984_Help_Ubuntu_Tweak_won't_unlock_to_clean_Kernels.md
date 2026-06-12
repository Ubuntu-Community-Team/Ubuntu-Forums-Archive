---
title: "Help: Ubuntu Tweak won't unlock to clean Kernels"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by steve228 on 2010-07-29
I have been using Ubuntu Tweak for a while now.  Recently I haven't used it and have installed various programs.  Today, I was going to clean my kernel listing and cache and such, but it won't let me unlock with my root password, it just gives me an error... 

Here's the details

I opened the application today and it popped up with a message saying
> The daemon of Ubuntu Tweak doesn't start correctly, that means some advanced features may not work.
If you want to help developer to debug, try to run "sudo ubuntu-tweak-daemon" under terminal.

So I navigate to the "Clean Kernels" option, and click "Unlock" and here is what popped up:
> Could not authenticate
An unexpected error has occured

I also ran it in the terminal and here is the standard output from the terminal 
> [DbusProxy][ERROR] 'NoneType' object has no attribute 'get_dbus_method' (dbusproxy.py:56)
/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py:130: DeprecationWarning: Accessed deprecated property Package.summary, please see the Version class for alternatives.
  return self.cache[pkg].summary
[DbusProxy][ERROR] 'NoneType' object has no attribute 'get_dbus_method' (dbusproxy.py:56)



I have also been having trouble with my dbus-daemon using high cpu usage when adding the "Indicator Applet Session" to my top panel.  If I add that applet to any panel the dbus-daemon starts using almost all my cpu...

Any Ideas?...

---

### Post by clhsharky on 2010-07-29
steve228

Have you tried to reinstall or upgrade Ubuntu Tweak?


Sharky

---

### Post by k3lt01 on 2010-07-29
I know I will probably get a flame or something for this but have you considered [doing it the old fashioned way]("http://ubuntuforums.org/showthread.php?t=140920")? UT is a great tool but at times like this it [pays to know how to do it without tools such as UT]("http://ubuntuforums.org/showthread.php?t=140920").

---

### Post by steve228 on 2010-07-29
Sharky, Yes I have re-installed the version I had on there previously and then I downloaded and installed the newest version...

As far as UT goes... I like having all the various options and tweaks in one app, but I will definitely take a look at the link!

---

### Post by soldier1st on 2010-08-03
did you go here [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) and download the .deb and see if that will fix it?also did you remove any of the default Ubuntu programs?

---

### Post by Keen101 on 2010-08-03
I'm pretty sure "sudo apt-get autoclean" will do the same thing.

---

### Post by akila87 on 2010-08-04
Check whether you are having PolicyKit on startup programs.

This might help
[http://ubuntuforums.org/showpost.php?p=9482066&postcount=18](http://ubuntuforums.org/showpost.php?p=9482066&postcount=18)

---

