---
title: "cannot get wireless working"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by khronix on 2008-07-26
hey guys, first post and first day using ubuntu and linux in general seriously. been lingering on the idea of installing for a long time and decided that i finally would start to learn about linux. looking awesome so far, but i can't get on wireless internet. read a lot of stuff on my ipod touch while in linux (can't look anything up online with no wireless in linux) and still am getting nowhere. basically, i found that theres that program called ndisgtk and that would hopefully make it easy to get wireless going but i cant install because it says "root or sudo required" or whatever. i read like 10 sites on this but i still cant figure it out. i dont really know to much about terminal to use sudo through there so in the end i cant run the program. btw, my wireless card is the Linksys WUSB54GS w/ speedbooster. only things in the networks thing are wired and modem or w/e so clearly it isnt supported. loving what i see so far in linux but w/o internet, theres no way i could start using over windows for anything. thanks in advance to anyone able to help, i really hope i can figure this out so i can start using linux for everything.

---

### Post by terry slaughter on 2008-07-27
"sudo" is to call for your password for access to ADMIN programs.eg: yourcomp@yourtermprmt$ Type>" sudo + what you want to do"+ hit enter will return a prompt for your password and permission to execute.Maybe read the Absolute Beginners Talk area before you go any further. Have Fun:guitar:

---

### Post by hajk on 2008-07-27
You need to supply some info on your wireless adapter. Open a terminal and type```

sudo lsusb -v |grep Linksys
```and then report the output of that command. This will tell us a bit about the wireless chip used.

Since you're new: the "lsusb -v" command results in a flood of output for all your USB devices. This output is "piped" (the vertical bar) to the "grep" command, which filters the output for any line containing some word, in this case the word Linksys. Remember this trick, it can save a lot of time.

---

### Post by khronix on 2008-07-27
> **hajk said:**
> You need to supply some info on your wireless adapter. Open a terminal and type```

sudo lsusb -v |grep Linksys
```and then report the output of that command. This will tell us a bit about the wireless chip used.

Since you're new: the "lsusb -v" command results in a flood of output for all your USB devices. This output is "piped" (the vertical bar) to the "grep" command, which filters the output for any line containing some word, in this case the word Linksys. Remember this trick, it can save a lot of time.

typed it and it said:

> 
Bus 005 Device 005: ID 13b1:0014 Linksys 
  idVendor           0x13b1 Linksys
  iProduct                2 Linksys Wireless-G USB Network Adapter with SpeedBooster
can't get debug descriptor: Connection timed out


---

### Post by hajk on 2008-07-27
Hmm, it appears to be a version 2 with a Broadcom chipset. Since this adapter has been around for a while, chances are that the b43 kernel module will work. Note that Broadcom firmware must also be installed, which is done with the b43-fwcutter package during installation. The b43 module is installed in a terminal with```

sudo modprobe b43
```
You might add it to /etc/modules for automatic loading at boot time.

---

### Post by khronix on 2008-07-27
> **hajk said:**
> Hmm, it appears to be a version 2 with a Broadcom chipset. Since this adapter has been around for a while, chances are that the b43 kernel module will work. Note that Broadcom firmware must also be installed, which is done with the b43-fwcutter package during installation. The b43 module is installed in a terminal with```

sudo modprobe b43
```
You might add it to /etc/modules for automatic loading at boot time.

that brings up another problem...when i tried to extract the ndisgtk to /etc/ it said access was denied

also i tried this guide:
[http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs](http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs)
but when i tried the "make" and "sudo make install" commands, there were a bunch of errors so it didnt install :(

---

