---
title: "I don't want linux to start automatically"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by chrisbentley84 on 2010-08-19
I'm new to linux stuff.

I installed Ubuntu on a portion of my hard drive so now it gives me an option to choose which OS to start when i go to turn it on.  it gives me 6 seconds to choose or it starts ubuntu automatically.  how can i make it so windows is at the top of the list so the others who use this comp wont get confused so easily?  The screen at the beginning shows these options in the order i wrote them...

Ubuntu, with linux 2.6.32-24-generic
Ubuntu, with linux 2.6.32-24-generic (recovery mode)
Ubuntu, with linux 2.6.32-24-generic
Ubuntu, with linux 2.6.32-24-generic (recovery mode)
Memory Test
memory test
windows xp

Also, I noticed I don't have any sound.  I have a Dell Dimension E510 computer with Windows XP on it and Ubuntu installed on a portion of the hard drive.

---

### Post by Gone fishing on 2010-08-19
If you open a terminal and run

sudo apt-get install startupmanager

It will install startup manager 

System > Administration > Startup-Manager wher you can change the default OS etc

---

### Post by NCLI on 2010-08-19
Or, if you don't want to use the terminal, just open the Ubuntu Software Center, then search for and install StartupManager.

---

### Post by tmos22 on 2010-08-19
You are better off using the terminal and getting used to it.

---

### Post by drs305 on 2010-08-19
chrisbentley84,

Welcome to the Ubuntu forums.

There are ways to edit the existing Grub2 scripts to place the Windows entry at the top of the menu, but it is pretty geeky stuff. If you like working with scripts, visit the "G2 Title Tweaks" thread in my signature line.

An easier method would be to provide Grub2 with a custom menu which contains your Windows entry. The name of the custom menu will determine where the entry appears in your boot menu.

Note: What follows is how to place the Windows entry at the top of the menu (which I think is what you are asking for), NOT how to make it the default selection (which is easily done with StartUp-Manager).

Here is how to make an entry at the top of your menu. Note I said *easier*, not easy.

Open a terminal: Applications, Accessories, Terminal.

Open /etc/grub.d/40_custom and grub.cfg as root. 40_custom is a sample custom file, grub.cfg contains what is currently described in the boot menu. If you haven't used "sudo" or "gksu" before, it will ask for your password. You won't see it as you type - just press ENTER after you have typed it in.
```
gksu gedit /etc/grub.d/40_custom /boot/grub/grub.cfg
```

In the grub.cfg file, find the Windows entry. It should look *something* like this:
> menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ceecff9eecff7f51
	drivemap -s (hd0) ${root}
	chainloader +1
}

The section will begin with "menuentry" and end with "}".

Copy the entire section and paste it into the 40_custom file. The entire contents will now look something like this:

> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ceecff9eecff7f51
	drivemap -s (hd0) ${root}
	chainloader +1
}


Save the file as **06_custom**. 

Next, you want to make the file executable so it's contents will be included in the main menu. To do this, run the following command in the terminal:
```
sudo chmod +x /etc/grub.d/06_custom
```

Finally, add it to the Grub menu:
```
sudo update-grub
```

Your Windows menu entry will now be at the top of your list. You will also have another Windows entry further down.

As mentioned in an earlier post, setting the default OS is probably easiest with StartUp-Manager. See the "SUM" link in my signature line.

To make some basic changes to the menu, such as how long the menu is displayed, if SUM doesn't do it, check out the link "G2-Tasks".

---

### Post by jimbop99 on 2010-08-19
> **NCLI said:**
> Or, if you don't want to use the terminal, just open the Ubuntu Software Center, then search for and install StartupManager.

+1 (easy)

---

