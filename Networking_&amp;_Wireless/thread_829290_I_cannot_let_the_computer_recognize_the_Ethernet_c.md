---
title: "I cannot let the computer recognize the Ethernet card at startup"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by michelnacouzi on 2008-06-14
I added the DNS server first, and then i set a static ip, and the connection worked. I still have a problem however. I had this problem before, and it still persist. After working about 6 hours, (because i'm new in linux) i was able to generate an sc92031.ko file and i put it in .../drivers/net/, then, according to the instructions, i wrote 'insmod sc92031.ko' on the terminal, and then the computer recognized the ethernet card. however, every time i reboot my computer, the eth0 is not recognized, i have to go again to the terminal and write insmod sc92031.ko, Is there any way that i can tell my computer to do this automatically.
In the readme file they told me to make sure that the line : 'alias eth0 sc92031' is found in /etc/modules.conf. On my computer i have /etc/modules without an extension, i didn't find this line so i added it, and it didn't work. Then i tried putting only 'sc92031', and it didn't work as well. Any sugeggestions please?

---

### Post by pytheas22 on 2008-06-14
I'm not sure, but you might need to add the line:
```

alias eth0 sc92031
```

to the file /etc/modprobe.d/aliases

as well as have sc92031 (and nothing else) in the file /etc/modules.

---

### Post by michelnacouzi on 2008-06-15
I tried this and it didn't work, i even tried to put the full path of the driver and it didn't work as well. when i write 'insmod sc92031.ko' the module is inserted, but when i reboot, i have to reinsert it again. in the modules file, it is written that the following modules are loaded at boot time, and it contains the modules: lpmouse and lp (not sure of the spelling), i added 'sc92031', and nothing work. plz any solution???

---

### Post by pytheas22 on 2008-06-15
I don't know why it's not being loaded if it's mentioned in the appropriate files, but another solution is just to write a script to load it and place it in /etc/init.d.  Then it will be loaded at boot.  There are plenty of instructions online about how to write custom scripts for /etc/init.  Don't forget that you need to run update-rc.d after you put the script in.

---

### Post by michelnacouzi on 2008-06-16
I'm new to linux, please can you explain more how to do this?

---

### Post by lswest on 2008-06-16
create a file called "startEth0.sh" (without the quotes) on your desktop (right-click your desktop create document-->empty file), then add these lines to it:
```
#!/bin/bash

insmod sc92031.ko
``` save it and then do this:
```
chmod a+x ~/Desktop/startEth0.sh
sudo cp ~/Desktop/startEth0.sh /etc/init.d/startEth0.sh
update-rc.d startEth0.sh defaults
```
quick explanation of the commands:
first line: makes it executable
second line: copies the file to /etc/init.d/
third line: configures it to be run at boot (try the command like that first, if it errors out, try it with sudo).

Basically the script tells it to insert the module, and update-rc.d gets it to run on boot, so every time you start the computer eth0 should work fine.  If you have any questions, feel free to ask.

---

### Post by michelnacouzi on 2008-06-16
I tried this, and everything went well. in the 3rd line i used sudo because permission was denied. i restarted the computer, and it didn't work. I tried to put the full path of sc92031 in the file. I restarted the computer and it worked. Thank you so much.

---

### Post by lswest on 2008-06-16
No problem, I'm glad it worked for you.  Sorry about not realizing you needed to include the whole path.  Thanks for the thanks.

---

