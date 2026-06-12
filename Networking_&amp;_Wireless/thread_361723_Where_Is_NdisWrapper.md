---
title: "Where Is NdisWrapper?"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by SHIFTY101EASY on 2007-02-14
once ndiswrapper is installed, is it a program u can access from the applications/places/system tab things at the top of the screen? or do i need to do it from somewhere else...

i honestly have been trying to install it for a few days now and dont really know what im doing....people tell me stuff assuming i know even a little bit and i really dont. ive never really used a command line before.

i tried follow the directions for the installer in the .zip (or whatever its called in linux) but when i try to do the extract command it says something about an error or something, i cant really copy and paste it cuz the linux comp isn't on the internet yet, which is my ultimate goal by doing all this ndiswrapper stuff......

i think i may have updated the kernel last night? but im not sure if that was successful....it was a really long process and i followed a guide...who knows if it worked though.....

anyways, can anyone help me get this thing installed?

---

### Post by Floppyjoe on 2007-02-14
The following UrL may be of some help to you:

[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

Ndiswrapper is usually accessed from the terminal(command line interface)
It can be installed from the Ubuntu install CD by clicking on System/Administration/Synaptic Package Manager.
Then clicking Edit/Add CDROM . Then click reload. Then search for ndiswrapper.
This ndiswrapper install method won't work with a custom kernel though.

Some common ndiswrapper commands are:
```
ndiswrapper -l
```
Which will list the installed ndiswrapper drivers.

```
ndiswrapper -i driver.inf
```
Which will install a .inf driver file.

```
ndiswrapper -e driver
```
Which will delete the invalid or valid driver called "driver"

Floppyjoe

---

