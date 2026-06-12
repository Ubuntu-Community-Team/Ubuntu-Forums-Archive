---
title: "Problem booting up Ubuntu from the list"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by YourNeighbourNinja on 2009-04-26
Hi,
I have a problem with loading Ubuntu but of different kind. My friend installed Ubuntu for me and created a bootup list for me to choose an OS. I decided to delete the Windows and use only Ubuntu on this computer. Now, problem is that someone tried to load Windows from the bootup list and now it keeps booting it up without the list at the beginning. How can I get the bootup list back on so that I choose Ubuntu again?

---

### Post by YourNeighbourNinja on 2009-04-26
I forgot to mention that it displays a message: "GRUB loading...error 17" and that's when it just stops. I'm sorry about my very bad posting manner, I am an Ubuntu beginner but I want to learn. Thank you.

---

### Post by unutbu on 2009-04-26
Please use [these instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  run boot_info_script and post the RESULTS.txt file here.

---

### Post by ikisham on 2009-04-26
Boot from the live-cd, open Applications>Accessories>Terminal
```
sudo grub
```
```
find /boot/grub/stage1
```it will output where GRUB is (like (hd0,1) - for you may be different)
```
root (hd0,1)
```
```
setup (hd0)
```
it's restored!

Then if you want to delete the Windows entry in GRUB
```
sudo gedit /boot/grub/menu.lst
```
so you can open menu.lst as root, then scroll down and delete everything after ```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by unutbu on 2009-04-26
I think what ikisham is referring to is this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That probably will work, but note that after 
```

find /boot/grub/stage1
```

you need to run something like
```

root (hdX,Y)
```

The values for X and Y depend on the output of "find /boot/grub/stage1".

---

### Post by ikisham on 2009-04-26
Thanks unutbu, I fixed the message!

---

### Post by YourNeighbourNinja on 2009-04-26
Thank you everyone for helpful advice but I don't have the live cd with me. Is there any other way I can bring up the bootup list?

---

### Post by unutbu on 2009-04-26
Currently the Windows boot loader is installed on the first sector (MBR) of your hard drive. One way or another, we'll need to install the GRUB boot loader to the MBR.

Windows does not have a way to install GRUB to the MBR as far as I know. 
Ubuntu can install GRUB, but you can't boot Ubuntu at the moment.
So the next easiest possibility is to boot from a LiveCD.
It is a good idea to have a LiveCD in your possession. Occasionally, it is a useful tool for fixing your computer (such as now).

While booted into Windows you can download a LiveCD from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by YourNeighbourNinja on 2009-04-26
I am already downloading Ubuntu so I can make a cd and do what you advised. Thank you again. I now know I should not go anywhere without my live cd.

---

### Post by YourNeighbourNinja on 2009-04-26
After burning the ISO of Ubuntu liveCD I popped it in and got into a Terminal application like you said. I did what you said (with the aid of [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)) and I got the next message after grub> setup (hd0):


Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /bootgrub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

---

