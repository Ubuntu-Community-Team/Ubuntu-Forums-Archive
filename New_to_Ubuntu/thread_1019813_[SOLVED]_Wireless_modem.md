---
title: "[SOLVED] Wireless modem"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Jacroe on 2008-12-23
I have a Acer with an AMD processor. I'm trying to be able to use my wireless card included with my computer but I cannot figure out how in the world to do so. I've heard of ath5k and others although I cannot see how to set it up to work. Any help is appreciated.

---

### Post by kestrel1 on 2008-12-23
What Acer machine do you have & what wireless card does it have?

---

### Post by anewguy on 2008-12-23
Do the following:

(1) click on Applications, then scroll to Accessories and over to terminal and click

(2) type:

sudo lspci <press enter>

Post those results back here, and we can go from there.


Dave :)

---

### Post by TBomBM3879 on 2008-12-23
I'm going to safely assume you have an atheros AR5007EG since it's common with acer and you're trying to run ath5k.

To get this card working:

Open up a terminal (Applications > Accessories > Terminal)

Type in the following:

wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz)

Once that downloads, copy and paste the following (one at a time)

tar zxvf madwifi-hal-0.10.5.6-r3879-20081204.tar.gz

cd madwifi-hal-0.10.5.6-r3879-20081204

sudo make uninstall

sudo make clean

sudo make

sudo make install

sudo modprobe ath_pci

Restart your computer, you should now have wireless!

:)

---

### Post by Jacroe on 2008-12-24
You make a very correct assumption. I followed your instructions and I now have wireless. Thank you very much. Now my laptop can be a laptop instead of a very small desktop.

---

