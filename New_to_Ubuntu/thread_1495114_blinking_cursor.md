---
title: "blinking cursor"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by outlaw45k on 2010-05-27
today i got this problem for the first time i boot the ubuntu 10.4 x64 and i got a black screen and a blinking cursor a bit cursor seams the screen resolution low then the cursur got small seams the ubuntu got the proper resolution then stay like that for 2 min or more until finally i get the log in screen 


do i have to worry about this ? if yes is there any fix ? 

tia

---

### Post by linuxman94 on 2010-05-27
The problem is in plymouth (the graphic you usually see when you boot up.)

You can try this command in terminal (Applications -> Accessories -> Terminal) and it might be fixed.  No guarantees.

```
sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash && sudo update-initramfs -u
```

---

### Post by outlaw45k on 2010-05-27
```
bash: /etc/initramfs-tools/conf.d/splash: Permission denied

```
got this :(

---

### Post by dnairb on 2010-05-28
I believe that it's not enough to use sudo for this. One needs to have full root priveleges.

First, type this in terminal:

```
sudo -s
```

The enter your password as normal for sudo.

You will then see something like:

```
root@brian-desktop:~#
```

Now, try the following (which is the above command without the "sudo" as this is now uneccessary as you have full root priveleges):

```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash && update-initramfs -u
```

---

### Post by outlaw45k on 2010-05-28
:( i still get this bilking cursor  for few minutes then i get the log in screen

---

### Post by outlaw45k on 2010-05-29
should i put 9.10 and wait few moths until this get stable ?

---

