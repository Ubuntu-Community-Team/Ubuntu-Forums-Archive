---
title: "my windows disappeared ....!!!!"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by mohameds102004 on 2010-02-03
[CENTER][FONT="Comic Sans MS"][SIZE="5"][COLOR="DarkRed"][SIZE="4"]finally i installed ubuntu on to  my laptop .... but my main problem was my windows ... it's disappeared when i installed ubuntu ... i tried more than way to update the grub to vision 2 and it's updated but no way .... and tried to add windows to the grub list and no waaaaaaaay again .... so wht i can do make my windows appear into the grub list .. thx[/SIZE][/COLOR][/SIZE][/FONT][/CENTER]

---

### Post by admiralspark on 2010-02-03
Hey,
First: try entering
> sudo update-grubIf you haven't already. If that doesn't solve it, try the following:

If you have gparted installed, run 
> sudo gparted
in a terminal, and tell us if you see an NTFS partition. If it's not installed, use
> sudo apt-get install gpartedIt's possible (though not probable) that you erased windows...if this is so, not good. However, default install doesn't usually delete it, and the Guru's here will know the path to the window's boot section.

---

### Post by theozzlives on 2010-02-03
```
sudo update-grub
```
If that don't work then you may have chosen to install to the whole disk. post the output of
```
sudo fdisk  -l
```
that's a lower case L not a 1

---

### Post by nhasian on 2010-02-03
from a terminal try the command:

```
sudo update-grub
```

also the more information you can give us about your problem the faster we can help you resolve it.

---

### Post by presence1960 on 2010-02-03
Before you go running commands or changing anything let's see what you actually have on the machine. 

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

---

