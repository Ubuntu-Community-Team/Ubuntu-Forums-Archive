---
title: "Which is better for low memory systems? KDE, Gnome, Or xfce?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by NTpspE on 2009-05-16
Personally i prefer gnome, and so does my friend, but he has a low memory system, and it needs an easy and quick way to run.
So will Gnome work better?
Or KDE
or xfce?
Thanks

---

### Post by fahadsadah on 2009-05-16
XFCE is the most efficient for low powered systems.

How much RAM does he have?

---

### Post by NTpspE on 2009-05-16
246mb of ram.
Im installing 9.04 on his, because i did download the text based installer, but its loaded a graphics based installer and is doing it now.
I'll see how gnome DO loads up on it, but if it dosent work, how do i download xfce? 
I know how to do KDE, from the add/remove bit, is xfce the same way?

---

### Post by kpkeerthi on 2009-05-16
You can install XFCE on a running GNOME setup using
```
sudo apt-get install xubuntu-desktop
```

If you are happy with XFCE environment, you can get rid of GNOME using
```
sudo apt-get purge ubuntu-desktop
```

You can choose which environment you need from the login screen.

---

### Post by gn2 on 2009-05-16
Lxde is worth a try.

Xubuntu isn't that great for older/low memory hardware anymore, although "old/low memory" is relative ;)

---

### Post by Sir Jasper on 2009-05-16
Hi kpkeerthii,

I would like to ask if:

sudo apt-get purge ubuntu-desktop

also removes Nautilus and everthing not needed to run Xubuntu?

My regards

---

### Post by NTpspE on 2009-05-16
Well gnome actually seems to be working fine, allthough i thought 9.04 came with gnome DO with the mac-like dock, but it isnt there, but he dosent want it anyway :D

---

### Post by nfcampos on 2009-05-16
In a laptop with 768 MB of RAM and a Pentium 4 CPU is there any real advantage in using Xubuntu instead of Ubuntu?

Thanks, Nuno Campos.

---

### Post by halitech on 2009-05-16
You may see some speed increase. I changed from gnome to xfce and noticed a small increase on my previous system that was a P4 1.8 with 896meg of ram. Noticed a bigger increase when I did a base install and added the apps I needed instead of using xubuntu-desktop

---

### Post by gn2 on 2009-05-16
> **nfcampos said:**
> In a laptop with 768 MB of RAM and a Pentium 4 CPU is there any real advantage in using Xubuntu instead of Ubuntu?

Thanks, Nuno Campos.

Not really.

---

### Post by XubuRoxMySox on 2009-05-16
LXDE is much more light weight and speedy than XFCE. Use Synaptic Manager to install it, and let PCMan (LXDE's file manager) manage the desktop. Applications are in /usr/share/applications

Drag and drop icons for the apps you want right to your desktop for a newbie-friendly, "Windowsy-looking" familiarity.  You can even add wicked cool wallpapers from the web to this directory:

usr/share/lxde/wallpapers

so you can select them from the PCMan Preferences window. The default is a pretty blue LXDE wallpaper (and you can choose a green or a red one), but I've added a dozen others.

-Robin

---

### Post by juliobahar on 2010-03-12
> **kpkeerthi said:**
> You can install XFCE on a running GNOME setup using
```
sudo apt-get install xubuntu-desktop
```

If you are happy with XFCE environment, you can get rid of GNOME using
```
sudo apt-get purge ubuntu-desktop
```

You can choose which environment you need from the login screen.

It was nice to mention XFCE and I just tried it on my old Toshiba 512Mb Ram laptop with a share memory Intel graphic card. Running Karmic 9.10.

This is the first time I try XFCE (I've always used gnome and sometimes  KDE) My feedback is that I didn't really find my computer fast with XFCE, honestly I guess it is consuming more memory that gnome - I know that might be stupid- but Open Office seems to run very slow almost jamming the computer on XCFE, actually gnome was faster.

Btw, I ran the "$> free" command in terminal and it seems I have less free memory with XFCE as opposed to gnome. Can anybody explain please!!

---

