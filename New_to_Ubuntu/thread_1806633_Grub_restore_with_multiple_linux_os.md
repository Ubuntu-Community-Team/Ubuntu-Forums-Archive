---
title: "Grub restore with multiple linux os"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by djpemberton on 2011-07-17
So, here is what I have done. Vista was on my computer. I moved it and installed Ubuntu 11.04, also creating a couple other partitions for other Linux OS's. No problem. Computer booted with Grub from Ubuntu, just as I want.   

Now, I installed another Linux OS (Pinguy) just to try out. The computer now boots from Grub in Pinguy without issue, but I want it to continue booting from Grub in Ubuntu (I will be keeping Ubuntu while others come and go.   How do I restore Grub to Ubuntu (I don't know that I am using the right terminology or concepts) without messing anything up. There are many posts and articles around telling how to restore Grub after reinstalling Windows, but I couldn't find anything addressing my concern directly. I thought mine would need to be approached differently.

Any Help?

---

### Post by ercferret18 on 2011-07-17
1. Boot from an ubuntu live cd
2. Mount your root ubuntu filesystem at /mnt ("mount -t auto /dev/sdaX /mnt")
3. Run "sudo grub-install --root-directory=/mnt /dev/sda

See if that works

---

### Post by lmarmisa on 2011-07-17
You will need an Ubuntu 11.04 Live CD / USB for restoring your Ubuntu grub.

I recommend to follow this method:

[https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files]("https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files")

If this fails, try the **chroot** method:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

If you are not sure about the partitions you have to mount when you run both methods, open a terminal, type this command and post the results:

```

sudo fdisk -l

```A last comment: if you want to test a new distro, I recommend to use a virtual machine and not your physical computer. VirtualBox would be fine for that:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Best regards,

Luis

---

### Post by idoitprone on 2011-07-17
> **djpemberton said:**
> So, here is what I have done. Vista was on my computer. I moved it and installed Ubuntu 11.04, also creating a couple other partitions for other Linux OS's. No problem. Computer booted with Grub from Ubuntu, just as I want.   

Now, I installed another Linux OS (Pinguy) just to try out. The computer now boots from Grub in Pinguy without issue, but I want it to continue booting from Grub in Ubuntu (I will be keeping Ubuntu while others come and go.   How do I restore Grub to Ubuntu (I don't know that I am using the right terminology or concepts) without messing anything up. There are many posts and articles around telling how to restore Grub after reinstalling Windows, but I couldn't find anything addressing my concern directly. I thought mine would need to be approached differently.

Any Help?
 if you can boot to ubuntu, then it is easy
step 1 add ubuntu to pingus


If you cant boot  into ubuntu. Try adding ubuntu to grub menu. It depends it grub 1 or 2

I assuming grub 2 then all you have to do is 
```
sudo update-grub
```grub 1 you have to manual add to menu.lst

step 2 reinstall grub
boot to ubuntu
i am guessing your harddrive is /dev/sda
[SIZE=3]```
sudo grub-install /dev/sda
```[/SIZE]

[https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands]("https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands")

---

