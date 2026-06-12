---
title: "New user on brand new comp, couple setup questions"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Aarold on 2011-03-05
Hello!

I've just bought a new PC yesterday and it's served as a great opportunity to start using Ubuntu, something I had considered for a while.  Now, I've got a dual-boot going with Windows 7 (that'll be used only for my gaming) and the rest of my computing is going to take place in Ubuntu.

Now most of this is running fine, but I've got a couple issues I was hoping someone with more experience could help me out with.

My new system is working with a Radeon 6850 and I just used the additional drivers option to load up the ATI/AMD proprietary FGLRX graphics driver, and now that I've rebooted I'm seeing in the bottom right of my display a little box reading "AMD Unsupported Hardware" message.  Now, with the driver loaded my resolution is actually turned up properly, but I'm wondering how to get both the resolution and lose the message.  A couple quick clicks around the net was saying that I should be using the FGLRX driver, and thus the confusion.

Second question is really simple, while I'm browsing in Firefox I was trying to use the wheel-click to get that scrolling up/down arrow set but that wasn't loading... any suggestions around that one?

Thanks very much for your time an patience, if you need any more info please just let me know.

Cheers!
Aarold

---

### Post by sikander3786 on 2011-03-05
Welcome to the forums :-)

For the Firefox scroll issue, go to Edit > Preferences > Advanced > General and under Browsing, enable autoscrolling.

For the ATI graphics card, wait for some other mate to jump in.

---

### Post by seawolf167 on 2011-03-05
I've seen a couple other people that have had the "AMD Unsupported Hardware" message and they were able to fix it by installing the newest versions of the drivers directly from AMD

[x86 & x86_64 driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

If you want to leave it the way it is, you should be able to simply copy over the control file from the drivers to your system.

To do that, download the driver from the above link, cd to that directory (say a "temp" folder in the downloads folder)

```
mkdir ~/Downloads/temp
cd ~/Downloads
mv ati-driver* temp/
cd temp/
```extract the driver instead of installing it

```
ati-driver* --extract
```backup your current control set

```
cp /etc/ati/control /etc/ati/control.backup
```copy over the new control set

```
cp ~/Downloads/temp/fglrx*/common/etc/ati/control /etc/ati/control
```

---

