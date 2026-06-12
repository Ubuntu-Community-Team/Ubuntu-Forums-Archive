---
title: "Boot Loader List Order"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by username in use on 2010-01-10
Hey, I am very new to Ubuntu and it is my first Linux OS, so please have patience with me.

Can anyone please explain how I change my boot-loader list order, so it shows Windows 7 at the top entry?

Currently this is the list:

> Ubuntu...
...
...
...
...
Windows 7 (loader) (on /dev/sda1)

I have read a lot of guides and still can't get it to work, so any step by step instructions would be greatly appreciated. Thanks in advance.

---

### Post by username in use on 2010-01-10
bump, nobody? :( :(

---

### Post by stoogiebuncho on 2010-01-10
This is different in different versions of Ubuntu, so can you please tell us which version of Ubuntu you are using.

Also, if you are using 9.10, please tell us if you installed fresh or if you upgraded from 9.04.

---

### Post by username in use on 2010-01-10
> **stoogiebuncho said:**
> This is different in different versions of Ubuntu, so can you please tell us which version of Ubuntu you are using.
 
Also, if you are using 9.10, please tell us if you installed fresh or if you upgraded from 9.04.
 
Thank you very much for the response stoogie, I had given up till I read your response :)
 
I am using Ubuntu 9.10 and it is a fresh install.

---

### Post by drs305 on 2010-01-10
The easiest way to move Windows to the top is to create a /etc/grub.d/06_custom file. The contents of this file will always be placed at the top of the grub.cfg menu.

Open the default custom folder for editing and rename it 06_custom:
```
cd /etc/grub.d
sudo cp 40_custom 06_custom
gksu gedit /boot/grub/grub.cfg 06_custom
gksu gedit /etc/grub.d/40_custom
```

Now, find the Windows entry in grub.cfg. It may look something like this:

> menuentry "Microsoft Windows XP Home Edition" {
   insmod ntfs
   set root=(hd0,1)
   search --no-floppy --fs-uuid  --set adkkf-07889-io6kfi
   drivemap -s (hd0) ${root}
   chainloader +1
}

It doesn't matter if it's the same as the above, just copy the entire block starting with "menuentry" and ending with the "{" into 06_custom, below the existing lines.

Save 06_custom and run
```
sudo update-grub
```

The Windows entry will now be at the top of your list. The disadvantage of this method is that this menu item will never change unless you manually edit it. This can also be a good thing. You will also have your Windows entry in it's normal place using this method. If you have no other OSs (Windows/Linux/OSX), you could remove the executable bit from the 30_os-prober file to prevent duplicate entries.

If you really want to tweak the menu, check out the link in my signature line: G2-Tweaks.

---

### Post by username in use on 2010-01-10
Thank you very much for the response.
 
I got it to work using startup manager. I was expecting my former attempts to change the entry list, but by changing the etc/default/grub and setting default=6 it only marks the entry chosen as default and doesn't change the listing...
 
Boy I feel stupid. Thanks for your guide though. I will try it out ^^

---

