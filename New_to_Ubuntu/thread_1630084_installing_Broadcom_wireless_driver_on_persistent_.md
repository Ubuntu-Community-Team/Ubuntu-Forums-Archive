---
title: "installing Broadcom wireless driver on persistent flashdrive install"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by macruadhi on 2010-11-24
I am trying to use a 4gb flashdrive for a persistent install, the only problem is, I need the Broadcom BTA wireless driver to be on the drive also. I tried having the .deb file on the drive along with the installed OS, but that didn't work. Trying to install them while booted up didn't work either since I suppose the OS is loaded onto Ramdisk. How can I create the persistent install that includes the wireless drivers?

---

### Post by wojox on 2010-11-24
Try booting from the USB, do an "sudo apt-get update" and the in Hardware Drivers screen should be able to load the wireless driver STA.

---

### Post by slixz85 on 2010-11-24
Im using a dell mini inspiron 10 also had wifi trouble but unfortunately you need a wired connection to install it. i tried several ways myself but finally just went to a friends house hooked up the cat5 and typed:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

after typing that in the terminal it took 1 minute to install then restarted i was on net in 5 minutes. has worked everytime. there are extra packages it needs besides the dkms also and hard to know what they are.

---

