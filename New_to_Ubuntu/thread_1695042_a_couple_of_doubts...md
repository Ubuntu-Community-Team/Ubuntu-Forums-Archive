---
title: "a couple of doubts.."
date: 2011-02-25
forum: New to Ubuntu
---

### Post by John Galt on 2011-02-25
Hello respected members,

I migrated to ubuntu from windows a few months and now fully convinced that it was the best decision.

Before I put forward my doubts, my computer configuration is as follows:

asrock   845gv chipset mobo
512 ram
p4 2.4 ghz
40+80 gb hdd
cd/dvd combo drive
nvidia geforce 4 mx 4000 graphics card

The doubts are as below:

1) although i did install ubuntu, (it is a completely different thing that i had to put in a blacklist command in vga mode.) It works out of the box, no drivers are needed as of now, but do i have to install a third party driver for my graphics card from the software repository? When installing ubuntu, the screen did show a few commands which had the tag nvidia in them. Is it that nvidia drivers come bundled with the installation? 

2) I did install restricted extras, but i am not able to play dvds. Do  need install anything else? Will i be able to play dvds with totem?

Please advise...

---

### Post by seawolf167 on 2011-02-25
To play DVDs you'll need to do the following

Open a terminal, Applications -> Accessories -> Terminal

Then type the following commands in:

```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdread4[FONT=monospace]
[/FONT]sudo /usr/share/doc/libdvdread4/install-css.sh
```As for your video card drivers, [go here]("http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html"), download and install the proprietary drivers directly from Nvidia

---

### Post by philinux on 2011-02-25
> **John Galt said:**
> Hello respected members,

I migrated to ubuntu from windows a few months and now fully convinced that it was the best decision.

Before I put forward my doubts, my computer configuration is as follows:

asrock   845gv chipset mobo
512 ram
p4 2.4 ghz
40+80 gb hdd
cd/dvd combo drive
nvidia geforce 4 mx 4000 graphics card

The doubts are as below:

1) although i did install ubuntu, (it is a completely different thing that i had to put in a blacklist command in vga mode.) It works out of the box, no drivers are needed as of now, but do i have to install a third party driver for my graphics card from the software repository? When installing ubuntu, the screen did show a few commands which had the tag nvidia in them. Is it that nvidia drivers come bundled with the installation? 

2) I did install restricted extras, but i am not able to play dvds. Do  need install anything else? Will i be able to play dvds with totem?

Please advise...

For the graphics driver I would personally try this.

System>admin> additional driver or it might be Hardware drivers depending on the version of ubuntu you installed.

See if it offers to install an nvidia driver.

---

### Post by John Galt on 2011-02-26
Thanks, problem solved.

This is exactly why I say migrating to ubuntu as the best decision ever.

People helping people, everyone as one.

Keep it up guys.

Thanks again

---

