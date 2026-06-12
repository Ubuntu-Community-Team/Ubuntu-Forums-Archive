---
title: "Google Earth Installation Query"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by kenb12 on 2009-04-02
Have downloaded Google Earth to Desktop.
How to install.
When 'clicked' the following message is displayed:
GoogleEarthlinux.bin
Could not display "/home/privateuser/desktop/Googleearthlinux.bin"
There is no application installed for this file type.

I have been into Synaptic Package Manager and Add/Remove but could not get anywhere.(afraid my sheer ignorance) 
Other programs have downloaded and installed OK.
But STUCK at present.

---

### Post by championboxes on 2009-04-02
I think to install a .bin file all you have to do is open the terminal change directory to Desktop ```
cd Desktop
``` then type ```
./GoogleEarthlinux.bin
``` if that doesnt work you have to be root ```
sudo ./GoogleEarthlinux.bin
```

---

### Post by TideMan on 2009-04-02
I installed Google Earth back in Oct 08 and according to my notes, I used:
```
sh GoogleEarthLinux.bin
```

As I understand it, sh is a "shell command interpreter" - whatever that means.

---

### Post by gandaran on 2009-04-02
all the above commands work but only if you make the file executable first, right click the file » properties » permissions » tick the executable box.
you can install google earth from synaptic, to do that you have to add the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository to apt-get/synaptic first.

---

