---
title: "i ruined my vid drivers"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by stevek123 on 2010-07-13
I'm installing Jaunty on a very old machine. I was almost done with everything installed & running. It has an old ati 7500 vid card and was running OK with the std xserver.org drivers but I went and used Add/Remove to put in the ati fxgl drivers. This blew my 3D and Stellarium would crash instead of running poorly (but RUNNING!). So I went to remove them but was directed to synaptic. There I saw xserver still installed and thought it might be interfering - so I removed them. Now X will not load and I just get some funky mess screen colors. I pulled the ati card and installed an OLD 32meg viper card I had. I couldnt get it to boot thru - screen goes black at X load.... but the card works! I'm sending this now running with it off a live CD session. 

Frustrated! What do I do to get a vid card going without reinstalling everything???

---

### Post by 3rdalbum on 2010-07-13
Dude, the X server is what gives you a graphical display on Linux.

Boot up Ubuntu normally and then press Control-Alt-F2 to get to a command-line. Log in and type:

```
sudo apt-get install xserver-xorg
```

Then reboot.

---

### Post by stevek123 on 2010-07-13
I would if I could! I cannot get to the terminal screens using F1-F6 after the ubuntu loading screen passes and the messy splash shows up. Mouse and keyboard stop responding. Can I get there using 'esc' while grub loads? Or can I access another feature to get it to load into terminal only? Or can it be corrected from a live session?

---

### Post by stevek123 on 2010-07-13
OK - lets put this ? another way...

How do I get this machine to boot into a terminal before it enters the grub menu?  It does not require password login and does not stop there.

---

### Post by masque7 on 2010-07-13
> **stevek123 said:**
> OK - lets put this ? another way...

How do I get this machine to boot into a terminal before it enters the grub menu?  It does not require password login and does not stop there.
Mount your / partition using the LiveCD and edit from there. You could even copy your working configs onto the partition.

---

### Post by stevek123 on 2010-07-13
I was hoping I could do that - I've peeked around but dont really know which folder in file sys that holds the video config files. ? any direction plz...

---

### Post by stevek123 on 2010-07-13
Is there a way - command - that will allow me to access synaptic as admin on the mounted system? from terminal? It looks like there may be but I dont understand it...

---

### Post by masque7 on 2010-07-14
What you've done is removed the x server. That is what 'draws' the screen and communicates with your keyboard and mouse.

There are 2 options you can try.

1) Ubuntu rescue mode from GRUB menu. You would need to use the command-line

```
sudo apt-get purge xorg
```This will get rid of old config files too.

Then you'd get X fresh with new default configs that would come with it, and then I believe would be stable enough for you to use and boot back into the system
```
sudo apt-get install xorg
```2) You can try and use the Ubuntu LiveCD to access your filesystem and make changes. 

Xorg aka X aka xserver lies here

```
/etc/X11/xorg.conf
```You would mount your Ubuntu partition in the LiveCD which it should do automatically. You would then either use the file manager or the terminal to 

a) replace xorg.conf with the one that the LiveCD has generated. So you would go to the directory I have given you above "/etc/ ...." on the LiveCD filesystem, and copy the xorg.conf over to your installed Ubuntu partition into that directory. Make sense?
*(Optional): even though the current xorg.conf on your installed Ubuntu partition is either not there or broke, you could back it up. Rename it to xorg.conf_old or something, just incase.*

b) edit, change, repair xorg.conf via a text editor (gedit). That would mean you would post the content of your file here.

To get to that 'root' directory (it's owned by the admin/'root' user, therefore we cannot do stuff in it without permissions):

alt+f2 -->

```
gksu nautilus
```

---

