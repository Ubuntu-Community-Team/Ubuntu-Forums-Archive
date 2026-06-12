---
title: "Broken Packages?"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2010-07-01
I was updating my sister's desktop when it reported that:
"You have 2 broken packages in your system!

Use the "Broken" filter to locate them.
[Close]"

Then, came:
"(-) An error occured
The following details are provided:
```
E: /var/cache/apt/archives/firefox_3.6.6
+nobinonly-0ubuntu0.10.04.1_i386.deb: trying to overwrite 'usr/bin/firefox', which is also in the package firefox-mozilla-build 0
```
[Close]"

Followed by:
"Changes applied
Update complete
(-) Not all changes and updates succeeded. For further details
of the failure, please ex[and the 'Details' panel below.
[-] Details
```
(Reading database ... 225015 files and directories currently installed.)
preparing to replace firefox 3.5.3+nobinonly-0ubuntu4 (using .../firefox_3.6.6+n
obinonly-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu0.10.04.1_386.deb (--unpack):
trying to overwrite 'usr/bin/firefox', which is also in package firefox-mozilla-build 0:3.6.6-0ubuntu1
Please restart all running instances of firefox, or you will experience problems.
Errors were experienced while processing:
 /var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu010.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
dpkg: dependency problems prevent configuration of firefox-branding:
firefox-branding depends on firefox (= 3.6.6+nobinonly-0ubuntu0.10.04.1); however:
 Version of firefox on system is 3.6.3+nobinonly-0ubuntu4.
dpkg: error processing firefox-branding (--configure):
 dependncy problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (3.6.6+nobinsonly-0ubuntu0.10.04.1); however:
 Version of firefox on system is 3.6.3+nobinonly-0ubuntu4.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-gnome-support; however:
 Package firefox-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--congigure):
 dependency problems - leaving unconfigured
Errors were encountered processing:
 firefox-branding
 firefox-gnome-support
 firefox-3.0-gnome-support
```
[Close]"
Note: This was typed from the original box, so there could be typing errors.

Then, on the upper bar appeared a red circle with a white minus-sign. When I put the mouse to it, a window appeared saying:
"An error occured, please run Package Manager from teh right-click menu or apt-get in terminal to see what is wrong. The error message was 'Error: BrokenCount > 0'This usually means that your installed packages have unmet dependenies"

So, I went to Synaptic Package Manager and went under the 'Broken' Filter. From there, I searched for and highlighted the yellow entry (which predictably was 'firefox') and went to 'Edit'>'Fix Broken Packages'. Then, I tried again, but to no avail.

Is there another way of fixing this broken package?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by k3lt01 on 2010-07-01
In a terminal try
```
dpkg --configure -a
```
that should re-configure any package that didn't install properly

---

### Post by Miljet on 2010-07-01
Sometimes a .deb file will get corrupted during download. When that happens, dpkg keeps trying to install the corrupted package without success. The only reliable solution I have found is to delete the offending package and reinstall it, which will cause the system to download a fresh copy.

In your case try this:
```
sudo rm /var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu010.04.1_i386.deb
```

Then run
```
sudo apt-get update
```

Then try to install Firefox by whatever means you prefer.

---

