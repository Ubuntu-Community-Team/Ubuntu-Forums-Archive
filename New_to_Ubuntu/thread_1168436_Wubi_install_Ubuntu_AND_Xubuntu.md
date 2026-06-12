---
title: "Wubi install Ubuntu AND Xubuntu?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by jfloydb on 2009-05-24
Could I wubi install Ubuntu AND Xubuntu? Or would they conflict in some way. Can Windows handle 2 wubi installs?

Why would anybody want to do this? I don't know...

---

### Post by nandemonai on 2009-05-24
> **jfloydb said:**
> Could I wubi install Ubuntu AND Xubuntu? Or would they conflict in some way. Can Windows handle 2 wubi installs?

Why would anybody want to do this? I don't know...

You don't need a separate install just to have Gnome, XFCE and KDE.

If you want to install another window manager:

```
sudo apt-get install ubuntu-desktop
```

Standard Ubuntu Gnome desktop.

```
sudo apt-get install xubuntu-desktop
```

Standard Ubuntu XFCE desktop.

```
sudo apt-get install kubuntu-desktop
```

Standard Ubuntu KDE desktop.

Once you have more than one window manager installed you can pick which you want to use at login by selecting another session.

If you really wanted to, you could always install separate installs to achieve this with different partitions. Maybe with shared swap space and a shared /home partition as well. Why? Testing maybe, isolation. Who knows...

As for wubi? No idea, don't use it. The above would be real installs.

Edit: Found this link: [http://ubuntuforums.org/showthread.php?t=849183](http://ubuntuforums.org/showthread.php?t=849183)

---

### Post by bennachie on 2009-05-24
ASFAIK you can only have one Ubuntu family OS operating under Wubi at any one time. However, you can certainly have a dual-boot situation, in which there are real installations of Windows and, say, Ubuntu. You can then "install", say, Kubuntu, within Windows, using Wubi.

I have routinely done this with Beta or RC versions of Ubuntu. Thus, for example, my main production machine was, until recently, running in a dual-boot environment with Vista and Ubuntu 8.10. I experimented with the emerging versions of 9.04 using Wubi. I have now switched the machine in question to dual-booting Windows 7 and Ubuntu 9.04. 

As soon as 9.10 becomes available with a Wubi installation option, I'll start exploring that version of the system (I'll probably also do a real installation of 9.10 on one of my other machines, if only for comparison purposes).

---

