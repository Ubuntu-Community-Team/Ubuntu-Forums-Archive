---
title: "NetworkManager Missing"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by yun.a.k on 2011-08-08
A few days ago my Network Manager Symbol and the battery status symbol went missing from the toolbar. the internet connection still worked so i delayed the the solution for this problem. now i had a problem with my connection that had nothing to do with the missing network manager unfortunately i played around with the networkmanager in the start programms and even deleted it from the list. my question is how can i reinstall the network manager and maybe even delete the fragments that might stayed somwhere. just make it work again because i have no clue how i can connect otherwise to the net. the battery status would be nice tocomeback as well. sorry for my unprofessional description but i am really no pro at all. a step by step guide wouldbe helpfull. thanks yunus

---

### Post by dwasifar on 2011-08-08
It sounds like you lost the indicator, not Network Manager itself.

Right-click the panel, choose "Add to Panel," scroll down until you find "Indicator Applet Complete," and drag it from the list onto the panel.  This should give you your network and battery indicators back.

If you really did remove Network-Manager from your system, go to Synaptic, search for network-manager, right-click the box next to it, and choose "Mark for Reinstallation."  Then click the Apply button on Synaptic to execute the reinstall.

---

### Post by amjjawad on 2011-08-08
> **yun.a.k said:**
> sorry for my unprofessional description but i am really no pro at all. 

Understood but you need to mention what release of Ubuntu are you using? :)

---

### Post by zanaz on 2011-09-08
I am having the same issue with the network indicator gone missing from the top panel on my Natty installation. The problem started after attempting to install an ndis-wrapper for the netgear wna3100. After I installed that wrapper and the driver, my network indicator icon disappeared and I could also no longer successfully run lsusb in a terminal. I also noticed any other system process (like the system test) would fail to continue past the lsusb command.  I did manage to repair the ndis-wrapper problem by removing it and the wlan driver, but my network indicator is still missing.

I don't see any "click" options in the panel in Natty that will allow changes to the panel itself.  I tried running the commands in the instructions here: [http://ubuntuforums.org/showthread.php?t=1838431&highlight=how+to+add+items+to+panel+in+natty](http://ubuntuforums.org/showthread.php?t=1838431&highlight=how+to+add+items+to+panel+in+natty) but they did not work.

Thanks

---

