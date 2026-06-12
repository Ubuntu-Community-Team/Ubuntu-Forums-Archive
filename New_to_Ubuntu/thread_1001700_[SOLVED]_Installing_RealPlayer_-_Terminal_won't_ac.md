---
title: "[SOLVED] Installing RealPlayer - Terminal won't accept password"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-04
I am trying to install RealPlayer on my +64, following the "How to.. " that I found in the forums.
Working in the Terminal, everything goes fine until I have to put in my password. No matter which letter I try nothing happens.

Here is a C&P of the screen:

george@george-desktop:~$ cd Desktop
george@george-desktop:~/Desktop$ chmod +x RealPlayer11GOLD.bin
george@george-desktop:~/Desktop$ sudo ./RealPlayer11GOLD.bin
[sudo] password for george: 

AS far as I remember, usually a dialogue box comes up for the password, but this is not happening here, either.
How do I proceed, please?

---

### Post by djbushido on 2008-12-04
There is no password box. You are given a prompt to enter your password, and nothing shows up for security purposes. Go ahead and enter your password, and see if that doesn't work.

---

### Post by Dedoimedo on 2008-12-04
Try:

```

sudo sh ./RealPlayer11GOLD.bin
```

If it does not help, we can try strace ...

Cheers,
Dedoimedo

---

### Post by akshay.sulakhe on 2008-12-04
No box comes out...nothing can be sen also for security purposes...just type the password and hit enter..Also dont give sudo ./Realplayer....just give ./Realplayer...aka remove the sudo..so that it gets installed in home and easy to manage...i prefer that):P

---

### Post by djbushido on 2008-12-04
Yeah, like he said, whenever you use sudo in a terminal, you will get:
```

[sudo] password for george: 

```

then just type in your password, and you are good to go.

---

### Post by billgoldberg on 2008-12-04
> **thadacto said:**
> I am trying to install RealPlayer on my +64, following the "How to.. " that I found in the forums.
Working in the Terminal, everything goes fine until I have to put in my password. No matter which letter I try nothing happens.

Here is a C&P of the screen:

george@george-desktop:~$ cd Desktop
george@george-desktop:~/Desktop$ chmod +x RealPlayer11GOLD.bin
george@george-desktop:~/Desktop$ sudo ./RealPlayer11GOLD.bin
[sudo] password for george: 

AS far as I remember, usually a dialogue box comes up for the password, but this is not happening here, either.
How do I proceed, please?


I know this has been answered, but no one seem to put it in a decent sentence.

When you need to enter you password in the terminal there will be no pop-up box.

You will see 

xxxxxx: 

Just type your password and press enter.

There will be no visual indication you are typing anything.

Also you don't need sudo for this one, using sudo when it isn't needed can be dangerous (security wise).

---

### Post by thadacto on 2008-12-04
Thanks to all who replied.
Got it installed - but there's no sound nor picture . Tried AVI, mpg and other files. Looks like I will delete RealPlayer unless I post another thread to get it playing.
Many Thanks again

---

