---
title: "Accidently deleted network-manager."
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by juiced301 on 2007-10-17
Version: 7.10 (up to date as far as I know)

I'm a newbie when it comes to Linux so I'm going to ask for some slack. ;)

Long story short: I liked KDE way more than GNOME, ran the command 'sudo aptitude remove ubuntu-desktop' and then cringed when it removed 'network-manager-kde' and 'network-manager'. (along with the gnome version too)

I found my ol' Ubuntu 7.04 disc laying around, so I'm using the live CD googling around for something, but I was wondering if anyone could help? I'd like to avoid reinstalling, I have a fair amount of files that are important to me.

---

### Post by Bothered on 2007-10-17
Do you have the kubuntu-desktop package installed? Try:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by juiced301 on 2007-10-17
I installed that package, removing the ubuntu-desktop somehow decided it should take it upon itself and remove KDE4 files and a few kubuntu-desktop ones... and because of it, it seems I have no way to connect to the internet without network-manager. (unless someone knows an alternative so i can grab that package ;])

---

### Post by Bothered on 2007-10-17
Individual packages can be downloaded direct from the repository in a web browser, but it'd be tricky for a package like kubuntu-desktop as you'd have to manually resolve the dependencies. Maybe chrooting from the LiveCD could help fix this? I don't know enough about how to do this to give more specific instructions.

---

### Post by juiced301 on 2007-10-18
Thanks, I was able to figure it out after you gave me that chroot bit. :)

---

