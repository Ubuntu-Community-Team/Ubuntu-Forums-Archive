---
title: "D-Bus Error"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by Zeophlite on 2010-06-17
Hi,

When I try System->Administration->Hardware Drivers from the Ubuntu desktop (via wubi), I get this error:

Cannot connect to D-BUS
org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket  /var/run/dbus/system_bus_socket: No such file or directory

then the Hardware Drivers dialogue doesn't open

How do I correct this?

Cheers

---

### Post by jtarin on 2010-06-18
From a terminal enter  ```
ps -ejH
```to see if the DBUS daemon is running.

Why are you attempting to open the drivers dialogue in WUBI, if you don't mind me asking?

---

### Post by Zeophlite on 2010-06-18
dbus-launch and dbus-daemon are in that list, but I still have that error.

Well my computer doesn't work with my old monitor, so I'm trying to update the nvidia drivers.  (See [here]("http://ubuntuforums.org/showthread.php?t=1491018") for more info)

Also I can't get my wireless to work either.  It doesn't appear under network tools, and I have to manually add the ethernet one like [so]("http://ubuntuforums.org/showpost.php?p=9472317&postcount=23").

---

### Post by jtarin on 2010-06-18
> **Zeophlite said:**
> dbus-launch and dbus-daemon are in that list, but I still have that error.

Well my computer doesn't work with my old monitor, so I'm trying to update the nvidia drivers.  (See [here]("http://ubuntuforums.org/showthread.php?t=1491018") for more info)

Also I can't get my wireless to work either.  It doesn't appear under network tools, and I have to manually add the ethernet one like [so]("http://ubuntuforums.org/showpost.php?p=9472317&postcount=23").
The monitor is more than likely causing the problem....I don't think updated drivers for your vid card will help that.
Are you running WUBI or do you have Ubuntu installed? Reading your other post it seems you have hardware problems...not Linux problems.Pull the cover off that thing and clean out the inside for starters especially around the cpu.Make sure your fans are working. You'd be surprised what that can do.Your problems are also symptomatic of a failing or dirty power supply.
As to the Nvidia drivers.....I've never installed one from a GUI. It's always been from a terminal. I didn't know you could do it from a GUI in Linux.

---

### Post by Zeophlite on 2010-06-18
> **jtarin said:**
> The monitor is more than likely causing the problem....I don't think updated drivers for your vid card will help that.Unlikely - now that I've updated my drivers, my Fujitsu monitor (as well as my Logix one) both work fine.

> **jtarin said:**
> Are you running WUBI or do you have Ubuntu installedWubi

> **jtarin said:**
> 
Pull the cover off that thing and clean out the inside for starters especially around the cpu.  Make sure your fans are working.  You'd be surprised what that can do.  Your problems are also symptomatic of a failing or dirty power supply.I'll give her a clean

> **jtarin said:**
> As to the Nvidia drivers.....I've never installed one from a GUI.  It's always been from a terminal.  I didn't know you could do it from a GUI in LinuxI don't know either.  How do I update nvidia drivers from terminal?


> When I try System->Administration->Hardware Drivers from the  Ubuntu desktop (via wubi), I get this error:

Cannot connect to D-BUS
org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket   /var/run/dbus/system_bus_socket: No such file or directory

then the Hardware Drivers dialogue doesn't open
Getting back on thread, I still have this problem.  How do I fix it?

---

### Post by jtarin on 2010-06-18
That's only a front end for obsolete Nvidia drivers....that's what Nvidia and Google are for. It's not hurting anything...just remove it with the Synaptic package manager. Search for nvidia-common and do a complete removal.

---

### Post by Zeophlite on 2010-06-18
I sorry, I don't quite understand what you mean.

---

### Post by jtarin on 2010-06-18
> **Zeophlite said:**
> I sorry, I don't quite understand what you mean.
You don't need the System->Administration->Hardware Drivers menu item.
To remove it from your system go to System->Administration->Synaptic Package Manager and with the Synaptic Package Manager there will be a search function at the top. Enter the phrase "nvidia-common". Left-click the little square to the left of the "nvidia-common" entry and select "mark for complete removal". Then from the tool menu above you will see a green arrow that is marked "apply"...click on it.Wait for it to be uninstalled.Now your problem is solved. As you have said your nvidia driver is working fine and this package that you are removing is for installing "obsolete" nvidia drivers.

---

