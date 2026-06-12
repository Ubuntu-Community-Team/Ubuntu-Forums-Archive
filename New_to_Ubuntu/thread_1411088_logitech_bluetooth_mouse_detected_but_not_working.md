---
title: "logitech bluetooth mouse detected but not working"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by ghostier on 2010-02-19
Hi, I've installed a fresh copy of karmic yesterday and from the beginning my bluetooth mouse gets detected but does not work. When I tried using 'setup new device' once I select my mouse and click forward, it will either try to connect for a few minutes and say failed to connect to mouse or just display the fail message right away. I had karmic on the same computer a few weeks ago (I accidentally removed it) and the same bluetooth mouse worked just fine.

I also might add that the detection is fairly weak, in 'setup new devices' the mouse sometimes take very long to be discovered. Also, during startup I always get messages of whether to grant or deny access from the mouse, I check the box 'always grant' and clicked grant but that message still comes up every now and then.

---

### Post by rustutzman on 2010-02-19
I think changing to the Blueman Bluetooth manager helps. Also to get my MS 3000 Bluetooth mouse going I had to run ```
sudo hidd --search
``` after the Bluetooth manager found/connected with it. HTH

Russ

---

### Post by ghostier on 2010-02-19
I dont have the hidd command, is that from blueman? Also my mouse is just being completely ignored by ubuntu now, the manager does not even detect it.

---

### Post by rustutzman on 2010-02-19
That command does come from the Blueman installation. I know I didn't have any luck at all with the standard Bluetooth Manager. Try Blueman and see if it will work for you.

Russ

---

### Post by ghostier on 2010-02-19
i just went to windows again and it seems like the mouse's connection with windows was severed as well. I had to remove the device from windows then add it again to get it working. Now im back and ubuntu and its starting to ask me for permission to the mouse again. the same problem still persists. I'm want to use blueman as last resort because this mouse worked with gnome-bluetooth before and I hate installing redundant programs.

---

