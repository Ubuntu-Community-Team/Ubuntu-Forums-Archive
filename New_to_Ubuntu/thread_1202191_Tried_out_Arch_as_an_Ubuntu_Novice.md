---
title: "Tried out Arch as an Ubuntu Novice"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by xusword on 2009-07-02
I recently got a hold of a old laptop. Decided to install Linux on it. I wasn't even sure if Xubuntu can run smoothly on it, so I tried Arch Linux. I have been itching to try one of those minimalist distro for a long time. It's interesting how much work it's involved (for me at least) to get the gui showing and running. (Installed Xorg, Hal, Lxde, Openbox, Thunar) I haven't even hard of Xorg, Hal and Thunar before this.

With this kind of minimalist distros, you wouldn't install any package until you need it. It seems to be the best thing for people who really care about performance.

Now I have a question. If you end up needing all packages that ubuntu have and install all of them in arch, who is going to run faster, by how much? or at the same speed? Is it ever worth it to use thses minimal distros if you have good enough hardware? even if you are an expert?

---

### Post by ~sHyLoCk~ on 2009-07-02
[This]("http://wiki.archlinux.org/index.php/The_Arch_Way") is why you should use Arch. Not because which distro boot faster or slower, that doesn't even matter after 3days of install anywayz. My arch runs faster than ubuntu ever did. But yes, if you have a good hardware backing your system up, things won't feel much different no matter which distro you choose.

---

### Post by xusword on 2009-07-02
Interesting

I have always wanted to have more control over my own computer. So annoyed that Windows XP starts up so many processes that I don't know about. Maybe arch is the way to go for me. However, I still know too little about package managements and don't know where to start learning about it.

For example, I downloaded the source code of the video card of that computer (Intel discontinued supports of that card and released source code instead) and I have no idea how to install it. (Compile error, which I don't know how to fix)

---

### Post by decoherence on 2009-07-02
> **xusword said:**
> Interesting

I have always wanted to have more control over my own computer. So annoyed that Windows XP starts up so many processes that I don't know about. Maybe arch is the way to go for me. However, I still know too little about package managements and don't know where to start learning about it.



Arch is an excellent introduction to the 'guts' of a Linux OS. Pretty much all that is required is reading comprehension, and their truly excellent [Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide").

Arch won't do anything automatically for you, but as long as you have the guide and read what's on screen (especially during package updates!) you're very well covered.

> 
For example, I downloaded the source code of the video card of that computer (Intel discontinued supports of that card and released source code instead) and I have no idea how to install it. (Compile error, which I don't know how to fix)

A package manager's job is to make it so that you don't have to manually download source code. A 'package' is a piece of software that has been packaged for your particular package manager. Generally, the package *maintainer* (often a volunteer) downloads the source code, compiles it (in the case of Ubuntu and Arch, anyway) and distributes it as a package for you to install.

You may be able to find a package that has the driver for your video card, in which case you wouldn't need to worry about compiling it.

Arch's package manager is called pacman. From a basic standpoint, it's just as easy to use as apt-get.

---

### Post by oldos2er on 2009-07-02
> **xusword said:**
> For example, I downloaded the source code of the video card of that computer (Intel discontinued supports of that card and released source code instead) and I have no idea how to install it. (Compile error, which I don't know how to fix)

 Sounds like you need to install the package build-essential. Also see [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

