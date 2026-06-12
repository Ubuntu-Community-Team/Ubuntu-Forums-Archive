---
title: "Need help with Google Earth 4.3"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by mvalviar on 2008-12-17
Hi,

I installed GE enabling medibuntu repos and typing "sudo apt-get install googleearth". It runs fine but it told me to upgrade to GE4.3. I read a guide on the net on how to upgrade. I downloaded from the GE website the bin file, gave it execute permission and ran with "sudo ./GoogleEarthLinux.bin" as instructed by the guide I read. It installed but I can't run is a regular user. The window pops up but I can't see planet earth. I tried to install it without sudo but I got the same result. From another guide I tried to install it using "sudo apt-get install googleearth-4.3. But its still the same result. What should I do?

---

### Post by iponeverything on 2008-12-17
I have to turn off desktop effects for it to work on my machine.

Syetem -> Preferences -> Appearance  (Visual Effects Tab)

---

### Post by mvalviar on 2008-12-17
It works with effects on when I use "sudo googleearth".

---

### Post by vanadium on 2008-12-17
Change the user of  ~/.config/Google directory and files from root to yours. This can be done with the following command (you can copy/paste this directly in the terminal - $USER will automatically be replaced by your actual user name)

```

sudo chown -R $USER:$USER ~/.config/Google

```

---

