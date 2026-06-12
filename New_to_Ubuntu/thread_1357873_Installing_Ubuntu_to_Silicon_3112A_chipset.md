---
title: "Installing Ubuntu to Silicon 3112A chipset"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by poisonborz on 2009-12-17
Hola,

I'm trying to install Ubuntu to the mentioned chipset (found on the Asus A7N8X mobo) but the installer doesn't see my SATA hdd (it works well on other PCs - plus, it is detected by the LiveCD OS). Where can I find the driver that I can include at the install?

(I found [this]("http://ubuntuforums.org/showthread.php?t=2557&highlight=howto+raid") thread, but I'm not geek enough to patch kernel...)

---

### Post by leprkhn on 2009-12-17
[THIS]("http://linuxmafia.com/faq/Hardware/sata.html") may help.
Or go straight to your Sil 3112 [HERE]("http://linuxmafia.com/faq/Hardware/sata.html#sil")

---

### Post by poisonborz on 2009-12-17
Solved it, with this method:

# Boot Ubuntu Karmic LiveCD as usual
# Once booted, open a terminal and type:
sudo apt-get remove dmraid
# check everything went fine with the following command, value must be zero 0
echo $?
# Double click on Install Ubuntu 9.10
# Proceed as usual Forward-> Forward->
# Hopefully your disk must be recognized now.

---

