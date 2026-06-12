---
title: "Simple Problem."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Mattattack on 2008-12-17
Hello all! First off i wanted to apologize if the question i am about to ask comes off as a little elementary and super basic. I Usually just search the web for answers to my questions however this is one of those times where a couple hours of searching has failed.

ok, So i've been using ubuntu for about a month now, switching from years of windows usage. and i feel like i have reached enlightenment through this operating system! I was utilizing a Dual boot system just so i could parallel the differences of windows and ubuntu as i began my experimentation, and now i don't want anything to do with windows and am switching over solely to linux. This is where i've been running into my problems.

I deleted my windows xp partition with GParted fine, but when i try to take windows xp  out of the menu list it will not let me. 
it says "could not save the file /boot/grub/menu.lst you do not have the permissions necessary to save the file please check that you typed the location correctly and try again"

even after enabling the root and trying it as a root user it still says i do not have the permissions. Would just like to know why and the way around it so it just boots  ubuntu right from start up.

Thanks
mattattack

---

### Post by nandemonai on 2008-12-17
> **Mattattack said:**
> Hello all! First off i wanted to apologize if the question i am about to ask comes off as a little elementary and super basic. I Usually just search the web for answers to my questions however this is one of those times where a couple hours of searching has failed.

ok, So i've been using ubuntu for about a month now, switching from years of windows usage. and i feel like i have reached enlightenment through this operating system! I was utilizing a Dual boot system just so i could parallel the differences of windows and ubuntu as i began my experimentation, and now i don't want anything to do with windows and am switching over solely to linux. This is where i've been running into my problems.

I deleted my windows xp partition with GParted fine, but when i try to take windows xp  out of the menu list it will not let me. 
it says "could not save the file /boot/grub/menu.lst you do not have the permissions necessary to save the file please check that you typed the location correctly and try again"

even after enabling the root and trying it as a root user it still says i do not have the permissions. Would just like to know why and the way around it so it just boots  ubuntu right from start up.

Thanks
mattattack

Couple ways to do this..

Easiest would be from the terminal:

```
gksudo gedit /boot/grub/menu.lst
```

Remove the XP entry, save and you should be good to go.

You did mention 'enabling root' but not sure what you meant by that.

If that doesn't work, reply and I'll try and suss out what's wrong. ;)

---

### Post by kellemes on 2008-12-17
No need for a root account. [Read this.]("https://help.ubuntu.com/community/RootSudo")
From terminal..
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Tatty on 2008-12-17
You should never need to enable root on a Ubuntu system, doing so is seen as a security risk.  Please read the page below on root and sudo in ubuntu and consider re-disabling root.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

try opening the file for editing with:

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by Mattattack on 2008-12-17
ah thanks a lot! worked like a charm!

just my lack of experience in bash commands that got in my way.

by enabling root i meant that i set up my root account with a password, which i've now learned is not really needed. Anyways, thats what i meant though.

thanks guys.

---

### Post by mrbiggbrain on 2008-12-17
that wierd i was under the impression that by default ubuntu had no root, and no need for a root password, that root was a god-user in ubuntu that noone could controle but throughs sudo. i dont know my root password, and i dont think i need to as long as i know the password i need for sudo

---

### Post by Tatty on 2008-12-17
> **mrbiggbrain said:**
> that wierd i was under the impression that by default ubuntu had no root, and no need for a root password, that root was a god-user in ubuntu that noone could controle but throughs sudo. i dont know my root password, and i dont think i need to as long as i know the password i need for sudo

Almost.  By default the root password is disabled in ubuntu, meaning no one can log in as root.  It can be enabled if you wish but it is highly recommended that you dont.  See the link in post #3 and #4

---

