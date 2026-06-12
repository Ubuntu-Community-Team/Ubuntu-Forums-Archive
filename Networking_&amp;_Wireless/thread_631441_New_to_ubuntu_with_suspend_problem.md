---
title: "New to ubuntu with suspend problem"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Nu7a on 2007-12-04
Hey, Just recently made the switch from windows to ubuntu, and I must say, im liking it very much. However, I use a laptop and like to suspend, but when I come back from suspend, when i click on the network icon in the taskbar, ubuntu doesn't seem to see my wireless card, Im on a asus c90s w/ intel 4965agn card. Ive done some search and tried different things but I have not been able to get it to work.

Thanks in advance...

---

### Post by Junglizer on 2007-12-04
Recompile your kernel and make sure you've got correct settings for APM/ACPI and your wireless drivers.


Oh wait... this is the Ubuntu forum.

---

### Post by Junglizer on 2007-12-04
> **Junglizer said:**
> Recompile your kernel and make sure you've got correct settings for APM/ACPI and your wireless drivers.


Oh wait... this is the Ubuntu forum.

Thats just me being an ***, but it does bring up another valid question. Does Ubuntu come with kernel sources by default or do you have to do that whole system-update crap? A lot of the problems on here, compatibility wise could be fixed simply with a kernel recompile. Its nice to have a distro where you don't have to update all of this stuff that you aren't using just to get the kernel sources so that you can remove all of it anyways.

---

### Post by NateMan on 2007-12-15
there is a problem with the 3945agn laptops. As I write this on my c90s at the moment mine is unable to run without being plugged up (the wifi that is). There are new batches coming out that shouldn't have that issue.

---

### Post by Silentheero on 2007-12-16
I also have a C90s. The wireless works out-of-the-box and I haven't had a problem, but as soon as I suspend or hibernate, the wireless dies. It is not in the network settings list. Its like it was taken out of the computer while suspended. I tried the init.d/networking restart thing and the following from [this post:]("http://ubuntuforums.org/showthread.php?t=633303")

```
sudo gedit /etc/default/acpi-support
```
```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"
```

but those have not helped. I tried Ctl+Alt+Bksp to reset X, but of course that did nothing. I know many people have this problem from the searches, but most of them have had no success in solving it (at least from what I found)

A simple command entry is probably all it takes, but I don't know it and can't find it.

TIA

---

### Post by NateMan on 2007-12-20
The issue that the c90s has with the wifi on the 4965 not working will unplugged or after a suspend or  hibernate is not an issue with the wifi card as was originally thought. it turns out that it is a bios issue with the c90s motherboard. Asus is working on a new bios right now that should be out after the holidays at the earliest. the only temporary solution to this is to buy a intel 3945 wifi card which can be found cheaply online. this card has no issues, however it doesn't support the n network. also early c90s laptops need to have the motherboard replaced, which they will do for free any time in the life of the laptop. This is so the laptop can support more power hungry processors and video cards. I write this on my plugged in c90s. I can't wait to get my 3945 in so I can suspend and hibernate my machine with impunity.

---

