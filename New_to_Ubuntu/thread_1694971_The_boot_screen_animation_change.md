---
title: "The boot screen animation change"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Ben Page on 2011-02-25
Hey fellow Ubuntuers!

I have installed various desktop environments om my Ubuntu 10.10 installation, to test some things out. I have installed KDE4 desktop last and now my bootscreen animation says Kubuntu 10.10. and is all blueish (it's the default Kubuntu bootscreen).

I've been looking for a solution, there are some threads, but they are not helpful.

I want to restore my Ubuntu bootscreen. Is there a specific package that I need to uninstall/reinstall/replace in order to get back the desired bootscreen animation? Or is there another way?

---

### Post by zenwalker on 2011-02-25
If i am not wrong, there should a application where you can select which one you want as your loging screen. Btw i hope ur not talking about boot image which is your grub screen.

---

### Post by Ben Page on 2011-02-25
No, I'm not talking about the login screen or GRUB loader. I need to change the boot animation, the animation which is showing while the OS is booting, loading kernel, drivers and stuff...

I mean this screen:

[IMG]http://images.techtipsgeek.com/post/speed-up-booting-in-ubuntu-boot.gif[/IMG]

...and instead of it I'm getting this one:

[IMG]http://cache.techie-buzz.com/images/postimg/ricky/kubuntu_plymouth.jpg[/IMG]

---

### Post by zenwalker on 2011-02-25
This is called splash screen. This might helps [http://ubuntuforums.org/showthread.php?t=11478](http://ubuntuforums.org/showthread.php?t=11478)

---

### Post by Ben Page on 2011-02-25
Yeah, now I see why I couldn't find anything...:oops:

I found a couple of methods on how to do this, also the thread you linked has good instructions, there are great custom Splash screens on Deviant art, but this still doesn't fully answer my needs.

How to get the >default< Ubuntu 10.10 Splash screen back?

---

### Post by Ben Page on 2011-02-25
Ha, I found a solution!

The default Ubuntu 10.10 boot splash screen is in /lib/plymouth/themes directory, with this command you can choose between all installed boot splash screens:

```
sudo update-alternatives --config default.plymouth
```

Then you can select (by pressing in the corresponding theme number) which boot splash screen you want to use. 

Hope this helps somebody in need :)

Thnx Zenwalker for pointing me in the right direction ):P

---

