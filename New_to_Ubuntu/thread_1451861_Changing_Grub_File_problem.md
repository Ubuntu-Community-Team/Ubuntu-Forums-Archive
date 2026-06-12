---
title: "Changing Grub File problem"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Folkus on 2010-04-11
Hi ,
Ubuntu 9.10
I tried to change grub file from directory /etc/default/grub manully and by the  terminal for the OS selection list changings. 
But I can't write changes manually coz 'Permission denied' and I also tried to do that with 
"sudo -s" and "sudo bash" root privilege on the terminal,  but it's  still not opens.:confused:
plz, help.

---

### Post by Folkus on 2010-04-11
plz help, I also read Grub manual basics from this forum and I know how to change grub list selection, but I can't work with that {default/grub and grub.d} even with the root mode.

---

### Post by philinux on 2010-04-11
Open a terminal. Copy and paste this in.

```
gksudo gedit /etc/default/grub
```

Or for just changing default OS install startupmanager from Synaptic.

---

### Post by Folkus on 2010-04-11
Thanks for help, man, but I have make another mistake, I've set a HIDDEN TIMEOUT 2
and basic TIMEOUT 0 :(

at startup grub is  not loading untill I must pusuh on SHIFT (that say manual)? but it not works, I've tried all keys, plz. help again I beg you!

---

### Post by philinux on 2010-04-11
Whenever you change /etc/default/grub or any other grub config file you must run the following command for the effects to take place

```
sudo update-grub
```

This regenerates /boot/grub/grub.cfg

Also click the grub2 link in my signature for more info.

---

### Post by Folkus on 2010-04-11
can anybody help me to bring back the grub menu? I really tried to hold and rapidly press shift and esc but it not works, damned/](*,)

---

### Post by Folkus on 2010-04-11
> **philinux said:**
> Whenever you change /etc/default/grub or any other grub config file you must run the following command for the effects to take place

```
sudo update-grub
```This regenerates /boot/grub/grub.cfg

Also click the grub2 link in my signature for more info.

I know about updating-grub it has been already applied, but now I cant  hit on the grub menu, holding shift key like says your manual, the system loading damned XP as a deafult without my permission.

I also tried to pressing esc then the grub trying to load the menu, but it not works, I swear.

---

### Post by Folkus on 2010-04-11
OK, I figured out what I must load from LiveCD, I also changed deafult/grub settings choosing previously 'safe' loading. But I can't understant how I shall to make a 'update-grub' command from the LiveCD terminal? (it makes changes for liveCD grub file, not for my installed Ubuntu)

can I make it manually or can  I  change the user from LiveCD terminal, and acting like installed on my hard drive user? 
help me, I'm still stock. :shock:

---

### Post by drs305 on 2010-04-11
> **Folkus said:**
> OK, I figured out what I must load from LiveCD, I also changed deafult/grub settings choosing previously 'safe' loading. But I can't understant how I shall to make a 'update-grub' command from the LiveCD terminal? (it makes changes for liveCD grub file, not for my installed Ubuntu)

can I make it manually or can  I  change the user from LiveCD terminal, and acting like installed on my hard drive user? 
help me, I'm still stock. :shock:

You can, but it might be easier at this point to just reinstall Grub 2 from the LiveCD desktop. I will use "sda1" as your Ubuntu install. **Change the designation if necessary.** If you have questions about it, ask first. Do not use a partition number in the second command.

```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

```

Reboot, then:
```
sudo update-grub
```
Then we can fix G2 to work the way you wish.

---

### Post by Folkus on 2010-04-11
> **drs305 said:**
> I will use "sda1" as your Ubuntu install. **Change the designation if necessary.** If you have questions about it, ask first. Do not use a partition number in the second command.


You mean I must install it on a linux installed patrition? I guess  my ubuntu installed in sda7 and swap sda8, but I'm not sure well, how can I verify that information from LiveCD?

---

### Post by Folkus on 2010-04-11
OK I installed in dv7 and  "installation finished. No error reported".
but after rebooting the system, I'm still passing my grab menu, loading XP. I tried to reboot from liveCD again and make sudo update-grub command like you recommend, but it says "cannot find a device for /."
what's wrong now?

---

### Post by drs305 on 2010-04-11
Folkus,

Let's just start over. There are a number of commands but it shouldn't be too hard. This procedure will remove grub from your system and then reinstall it. 

From the LiveCD, add the necessary system files to a new mount point:
 
```
sudo -i
mount /dev/sda7 /mnt
mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr
chroot /mnt

```

Now everything you do will affect your *real* Ubuntu install on sda7. Commands you run will act on your actual installation, not the LiveCD files.

At this point, you could actually run "update-grub" and it should update as normal. However, since the changes you made aren't exactly clear to me, it might be best to just start with a fresh, default Grub 2 install. You will get a warning about not having a boot loader. Don't worry, we are going to put it right back. Just make sure you have an Internet connection and your power won't get interrupted:

As grub-pc is installed, it will ask twice if you want to include any extra items in the default boot lines. Just accept what is already in the line, if anything.

As you run the following commands, you will be asked where to install grub. Choose "sda" by highlighting it and pressing the space bar. That should place an * next to "sda". Then press the TAB key to highlight "OK" and press ENTER to continue.

```
sudo -i
apt-get purge grub-pc grub-common
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

```

Exit by pressing CTRL-d.

Now unmount what you previously mounted:
```
umount /mnt/dev /mnt/proc /mnt/sys /mnt/usr 
umount /mnt

```

Reboot, then run:
```
sudo update-grub
```

---

### Post by Folkus on 2010-04-11
thank you, man for your particular briefing, after a several attempts I'd maid that!
you my god and I've already printed your avatar (is that Tomas Jefferson?) and attached it at my wall! :popcorn:
good luck.

---

### Post by drs305 on 2010-04-11
Glad it worked out for you. And welcome to Ubuntu and the Ubuntu forums! :-)

You can mark the thread "Solved" by using the "Thread Tools" link near the top right of the first post. It lets helpers concentrate on unresolved problems and assists other users with similar problems locate threads which have provided a usable solution.

And you have a good eye - it is indeed TJ...

---

