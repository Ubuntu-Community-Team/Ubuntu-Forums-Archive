---
title: "WICD prevented me from being able to log in"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Death_Sargent on 2007-09-20
I can't log in if wicd is installed. 

I had to use recovery mode to remove it from command line just so i could get to a 32bit browser to make this post

---

### Post by imdano on 2007-09-20
Could you provide more details?  How far into the login process to you get?  Was wicd set to try to autoconnect to any networks?  What version of Ubuntu are you using?  How did you install/uninstall it (apt-get, a .deb file, etc)?

---

### Post by Death_Sargent on 2007-09-21
I am running ubuntu fiesty 7.04

i would never get further than the log on screen disappearing after i entered my password. 

I installed via apt-get

I set wicd to auto connect to my home network

it was using the ndisrapper driver.

its a built in atheros wireless card.

---

### Post by Death_Sargent on 2007-09-23
any-one?

---

### Post by kevdog on 2007-09-23
Dont install wicd from repository.  You need the beta/experimental/unstable (whatever they call it but not the stable) version from the wicd website.

Is ndiswrapper setup correctly??
lshw -C network
ndiswrapper -v
ndiswrapper -l

---

### Post by imdano on 2007-09-23
a new testing version is being released in a day or two, you should probably use that when it comes out.  In the meantime you could try reinstalling it, but make sure no networks are set to autoconnect.  Then see if you can log in after rebooting.

---

### Post by kevdog on 2007-09-23
Testing version -- do you have a summary of the new features???

Any idea when VPN is going to be incorporated?

---

### Post by imdano on 2007-09-23
It's mostly a bug fix release, but ralink support has hopefully been improved a little, and you can now choose do use signal strength in dBm instead of as a percentage (for people who either don't have link quality listed or for whom it's broken).  We're in the process of completely reorganizing and rewriting some of the code, as well as completely changing the file structure (no more /opt/wicd) for a future release, so most of our energy has been going into that stuff and bug fixes.  Hopefully you'll see more new features once that's finished.

The VPN plugin (at least the pptp one, not sure on vpnc) is coming as soon as I have time to sit down and write it.  With school and another project I'm working on I don't have a ton of time to work on wicd, and right now a lot of that is going into bug fixes and troubleshooting/support.  I've got some preliminary work done on it though.

---

