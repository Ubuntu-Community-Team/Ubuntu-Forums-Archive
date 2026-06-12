---
title: "windows 7 does not shows up while booting"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by thetechfreak on 2010-08-23
HI everyone 
I installed ubuntu 10.04 LTS. The problem is that while booting the list of OS'es does not shows up. I mean while booting ubuntu boots up automatically.
So please help as i want to use windows also.

Thanks :)

---

### Post by anand_30 on 2010-08-23
have u tried this?
```
sudo update-grub
```

---

### Post by LowSky on 2010-08-23
hoefully you didn't choose to Delete windows when you installed Ubuntu

---

### Post by Elfy on 2010-08-23
Have you tried pressing shift when grub is loading to see the menu?

---

### Post by thetechfreak on 2010-08-23
HI all 
Thanks for your replies.
Well I have tried the code 

sudo update-grub



It says "done" but still ubuntu boots up :(

@LOw sky : No man. I can still view files of windows 7. 

@forestpiskie : which menu are u talking about ?
Thanks all ! :)

---

### Post by Elfy on 2010-08-23
The boot menu. Try shift when the screen says grub loading ...

Alternatively you can edit the file so that the menu shows anyway.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Edit the file 

```
gksudo gedit /etc/default/grub
```

Put a # in front of GRUB_HIDDEN_TIMEOUT=0

---

### Post by thetechfreak on 2010-08-23
Ya I saw the list but 3 are of ubuntu and 2 are of memtest

now what to do ?
and ya I have NTFS and EXT4 partitons

---

### Post by thetechfreak on 2010-08-23
Yes I have performed all the updates

Ok. Now what if i format the partition in which ubuntu is installed. I mean I want to get rid of ubuntu and then later install it with wubi method *from windows*.
So basically i am just asking how to remove ubuntu but be sure that window boots up.

Thanks a lot guys.

---

### Post by thetechfreak on 2010-08-23
In the menu (while booting)
I get these 3 options of ubuntu
and 2 are of memtest.

Now some hope ??

And why would i need the windows recovery disk ?

---

### Post by thetechfreak on 2010-08-23
hey this is the last line
Setting up grub (0.97-29ubuntu60) ...

now shall i reboot ?

---

### Post by thetechfreak on 2010-08-23
Hey i appreciate your help
but i was getting those 5 options again
which one to choose ??

---

### Post by spydeyrch on 2010-08-23
> **anand_30 said:**
> have u tried this?
```
sudo update-grub
```


I though that the command was:

```

sudo update-grub2

```I seem to have read somewhere that there is a difference between the legacy update command and the newer grub2 command. I could be wrong and it may be that both do the same thing.

-Spydey :lolflag:

EDIT: Ok, so I guess that while I was reading and posting, a number of other people posted before I could get mine posted. sorry about any confusion my post may have caused.

---

### Post by thetechfreak on 2010-08-23
OK i tried all those links 
one is of memtest that actually does something. But does not boots up
and in the another one the cursor blinks up.

So shall i first log on to windows (with help of that article) then delete the partition of ubuntu >?

But dude thanks. You immensely helped me :)

---

### Post by thetechfreak on 2010-08-23
Hey now i am not getting that menu also (Of those 5 options)
WTH ! 
I think i should follow that article

---

### Post by thetechfreak on 2010-08-23
YA man i did that.
But not getting it. Huhhhhhh

I am now installing windows repair disk !

---

### Post by thetechfreak on 2010-08-23
No problem buddy !! I formatted my system and installed win 7 again
btw  u on FB ? wanna discuss something ;)

---

