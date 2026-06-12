---
title: "I messed up nvidia driver upgrade"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2011-07-17
after installing new EVGA GTX 460 i tried to install the new drivers and i checked the "not recommended" driver by mistake ;(
Now i boot up and after the ubuntu splash page we move on to a blank page with blinking cursor. Need help. Not good with blinking cursor. 
must sleep now. ever grateful for even smallest hints.

---

### Post by realzippy on 2011-07-17
Press "shift" during boot,select a recovery mode,then
select low graphics mode.Now you have a low-graphics GUI,which should let you uninstall the driver.

If low graphics mode should not work for some reason,drop to shell
instead,log in with username & password,then run

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

mind capital "X"

```
sudo reboot now
```

---

### Post by kindafunnylookin on 2011-07-17
thanks  for the reply.
got back```
mv: cannot stat '/etc/X11/xorg.conf  /etc/X11/xorg.conf.old
No such file or directory
```I have been trying to use the installation disc to get in and back up my files, NO joy there either. If I could access my files to back them up I would be happy to make a clean install. Can I get some direction on that or perhaps have another go at fixing my graphics driver.

---

### Post by fractalman on 2011-07-17
i had to upgrade my nvidia driver a few days ago,  i was using the one from 'additional drivers' but i needed the nvidia xdriver for milkdrop.

you should be able to get it through synaptic package manager, just open synaptic and search for nvidia-current, then mark for installation and click apply,

this installed the latest nvidia xdriver for me, im using a nvidia geforce 8400gs.
you should be able to configure the driver after installation from administration>nvidia settings.

if you have no nvidia settings in the menu, try a reboot and if it's still not there pop back to synaptic and install nvidia-settings, then check the menu and it should be there.

hope this helps

---

### Post by realzippy on 2011-07-17
recovery mode,low graphics session does not work?

---

### Post by kindafunnylookin on 2011-07-17
It does not.
I have made several tries but keep coming back with blank page w/ blinking cursor. Now I'm trying to figure out how to get at my files that I had saved on my desktop to move them to secure location. I am using the install disc to do this. When that is done I will do a clean install. Thanks again for trying with me.

---

### Post by wildmanne39 on 2011-07-17
> **kindafunnylookin said:**
> It does not.
I have made several tries but keep coming back with blank page w/ blinking cursor. Now I'm trying to figure out how to get at my files that I had saved on my desktop to move them to secure location. I am using the install disc to do this. When that is done I will do a clean install. Thanks again for trying with me.Hi, Livecd use a root

```
sudo -i nautilus
```

opens the root file browser window in the live cd, no password required.

Then you should be able to copy your files.

---

### Post by kindafunnylookin on 2011-07-18
> **wildmanne39 said:**
> Hi, Livecd use a root

```
sudo -i nautilus
```opens the root file browser window in the live cd, no password required.

Then you should be able to copy your files.
wildmanne ---- great tip '-i nautilus' i love that one. Thank you for helping.

---

### Post by wildmanne39 on 2011-07-18
Hi, your welcome! glad to help.

---

