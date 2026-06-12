---
title: "Overwriting Wireless Driver"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by egret on 2008-06-11
I've just followed [this](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WG311%29%7C%28netgear%29) guide, installed ndiswrapper, and installed the driver, only I forgot to copy the full driver into the folder so when I got ndiswrapper to install the driver it failed to completely install the driver.  I can't work out how to uninstall the driver and can't overwrite the driver.

I should say that this is my first install of any Linux so am on a very steep learning curve (so basically I know nothing)

Thanks for any help

---

### Post by molotov00 on 2008-06-11
This is a post that I came across the other day. I've saved it because there was lots of useful info/commands in it. Plus, you can see the "helper's" thinking process.

[http://ubuntuforums.org/showthread.php?t=822931](http://ubuntuforums.org/showthread.php?t=822931)

One thing that stands out there -- that might help you -- is the ndisgtk command.

Edit: I just looked at the tutorial you used. It looks dated because they talk about using dpkg to install and downloading from FTPs. The post I linked to uses an easier method of: sudo apt-get install ndiswrapper ndisgtk (both ndiswrapper and ndisgtk are automatically downloaded and installed), and then ndisgtk to configure. For the record, dpkg -i and apt-get install do the same thing but people say that apt-get is smarter with respect to dependencies etc.

Type 'man apt-get' to learn a bit more about it. I might uninstall ndiswrapper and install it again with apt-get (because that's what I'm comfortable with), although that probably isn't necessary.

---

### Post by egret on 2008-06-12
Thanks, that post talks of blacklisting a driver, which I assume I could do to allow me to reinstall the driver again.
How do I ding the location of the driver so I can blacklist it?

---

### Post by Ayuthia on 2008-06-12
If you are trying to remove a driver from ndiswrapper, you need to do:
```
sudo ndiswrapper -e <driver>
```
Replace <driver> with the driver you are trying to remove.  Make sure that you do not include the .inf portion.

---

### Post by chili555 on 2008-06-12
> **egret said:**
> Thanks, that post talks of blacklisting a driver, which I assume I could do to allow me to reinstall the driver again.
How do I ding the location of the driver so I can blacklist it?You don't need to know the location of a driver you want to blacklist. For instance, let's say the native driver that's not working for you and needs to be blacklisted is called *b43.* You would then *sudo gedit /etc/modprobe.d/blacklist.* A text editor will pop up with the file in it ready to be edited. Add a new line:```
blacklist b43
```Check your work carefully, save and close gedit. Make sure the module is not loaded with:```
sudo rmmod -f b43
```Substitute your driver module here, if it's not b43. The purpose of blacklisting a driver is so a native, built-in driver that doesn't work well or at all, doesn't get loaded and so you can then use ndiswrapper.

---

