---
title: "Compiz Fire Animation Missing"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by van1017 on 2011-02-24
Hello all,

I haven't used Ubuntu for several months, so I feel a bit rusty (hence why I'm putting this in "Beginner Talk"). That said, if the solution to this problem is somewhat obvious, please feel free to mock relentlessly...

So I was redoing the appearance of my desktop (version 10.04) and I had the thought that I needed blue fire (haven't we all had such a thought?). So, as such, I brought up Compiz, went to Animations and then to Effect Settings. Much to my dismay, I lacked a "Fire" tab. I had the ability to create fire, but not the ability to alter its' color. 

Obviously, this would not do! When a man wants blue fire, then that man must receive blue-freakin'-fire!

So what did this genius do? Well, he uninstalled compiz, of course! I got rid of everything, then reinstalled it. Now, everything came back, with one exception. Now, I can't even make normal fire! Bloody frick! Burn is no longer an option in the Animations tab.

So, my question to you lovely, linux-y folk is simple: help me make blue fire... Please...

Thank you...

-Van

---

### Post by Asmy on 2011-02-24
Do not worry! I have found a solution.

```
sudo apt-get install compiz-fusion-plugins-extra
```

This will add Paint Fire On Screen (search for it in filter). And yes sir, you can make blue fire.

---

### Post by van1017 on 2011-02-24
> **Asmy said:**
> Do not worry! I have found a solution.

```
sudo apt-get install compiz-fusion-plugins-extra
```This will add Paint Fire On Screen (search for it in filter). And yes sir, you can make blue fire.

Unfortunately, I believed that I had already done that, but I tried again...

I got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-fusion-plugins-extra is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```And still no fire for me... *cries in the corner*

EDIT:
Actually, I just noticed a secondary symptom (probably of the re-installation). My Cairo-Dock animations aren't working anymore. All of the settings are the same as they were before, but nothing is working. Visual Effects are set as high as they'll go... I really don't know what's going on...

---

### Post by NightwishFan on 2011-02-24
You need to enabled animation-extras.

---

### Post by van1017 on 2011-02-24
> **NightwishFan said:**
> You need to enabled animation-extras.

Alright, I'm a complete idiot... That was it... Thanks

However, none of the actual animations are showing in either cairo dock or from compiz. The cube is working, but none of the animations like Burn. I looked in Visual Effects and below Extra is Custom, something I wasn't expecting...

Any ideas?

---

### Post by NightwishFan on 2011-02-24
Something to do with pixel shaders I assume. Perhaps you are using different drivers?

---

### Post by van1017 on 2011-02-24
> **NightwishFan said:**
> Something to do with pixel shaders I assume. Perhaps you are using different drivers?

I don't see how. Everything was working perfectly just two hours ago before I uninstalled everything like an idiot. Now, none of the animations are functioning. I didn't do anything related to the drivers...

I just checked in Hardware Drivers and came up with nothing...

---

### Post by NightwishFan on 2011-02-24
Im sorry, I do not know any other reasons it would fail to work. I do know that some advanced plug-ins use arb fragment shaders (or something like that) that arent supported by all drivers, and if you did not uninstall drivers (you would know if you did) then I cant say why they would fail.

---

### Post by van1017 on 2011-02-24
Well, let me give you some more information then.

This is what I did to uninstall compiz:

```
sudo aptitude remove libgnome-compiz-manager0 compiz-extra  libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings  libcompizconfig-backend-gconf compiz-config-ini gcompizthemer  compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde  compizconfig-settings-manager python-compizconfig compiz-config-gnome  taskbar-compiz compizconfig-plugin compiz-freedesktop-dev  compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager  libgnome-compiz-manager libcompizconfig0-dev compiztools  compizconfig-settings-legacy compiz-fusion-plugins-extra  compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz  compiz-extra-plugins compiz-fusion-plugins-main  libcompizconfig-backend-kconfig compiz-core compiz-decorator  gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome  libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0  libcompizconfig-backend-gconf libcompizconfig0-dev  libcompizconfig-backend-kconfig libcompizconfig-dev 
```I got it from this link: [http://ubuntuforums.org/showthread.php?t=533201](http://ubuntuforums.org/showthread.php?t=533201)

I just restarted my computer, and now two more symptoms have cropped up. First of all, emerald isn't holding up. I can use it, but every time I restart, the changes revert. Plus, now the skydome is screwed up. Instead of my skydome, I'm getting a wierd white and unstable background. It's kind of trippy actually...

Any help would be greatly appreciated from anyone here. However, all of this has given me a headache, so I think I'm going to turn in for the night. I'll check back tomorrow and give thanks to whoever tries...

Thanks to everyone here...

-Van

---

### Post by NightwishFan on 2011-02-25
The way you removed them actually does absolutely nothing to changing any of their configuration. :/ Perhaps just ensure that all the recommend packages for them are installed. If you are seeing white areas and etc, I can only think of missing libraries or a rendering error.

---

### Post by van1017 on 2011-02-25
Well, I honestly have no idea what I could have done, but whatever. I'm just going to do a fresh install of the operating system. 

Thanks anyway...

-Van

---

### Post by van1017 on 2011-02-25
An unfortunate update:

I did a complete re-installation. I wiped the entire hard drive. Now that I've gone back into the OS, I find myself with the same exact problem. 

My graphics are turned up as high as they can go (I clicked on Extra, but now I see that it's on Custom; an option that wasn't there before). There aren't any drivers for me to install. However, none of the animations from compiz work at all for me. Not only that, but I can't change themes on Emerald. 

This is getting incredibly frustrating. Does anyone have any ideas?

-Van

---

### Post by NightwishFan on 2011-02-25
Forgive me if you already did, but could you post what model your gpu is?

---

### Post by van1017 on 2011-02-25
> **NightwishFan said:**
> Forgive me if you already did, but could you post what model your gpu is?

Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by NightwishFan on 2011-02-25
Interesting... I have this same exact model (or a very similar one) and I have no problems at all (except with water plug in)
```
product: Mobile 4 Series Chipset Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
```

Try this, open Applications -> Accessories -> Terminal

Type (while compiz is running):
```
emerald --replace
```

Are there any error messages?

(Do not close the terminal, just log out and back in to disable emerald)

---

### Post by van1017 on 2011-02-25
This is what I get when I type that into the terminal (with both compiz and emerald running):

```
(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

(emerald:6848): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(emerald:6848): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed


```I have absolutely no idea what any of that means, but take it for what it's worth...

---

### Post by NightwishFan on 2011-02-25
Nothing I can debug, try the same with:
```
compiz --replace
```

If nothing there, then I am not sure what to say. My intel 4 works fantastically.

---

### Post by van1017 on 2011-02-25
Ok, I don't what was "supposed" to happen with that one, but it made everything save for my wallpaper disappear for a moment and then all of my applications were on different desktop numbers. It also closed my firefox browser. 

Here's what I got in the terminal:

```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```

Helpful at all?

---

### Post by van1017 on 2011-02-26
If no one can help me here, could anyone tell me who I could go to for help? Or, maybe if upgrading from 10.04 to 10.10 would help? I don't see why it would, but just a thought...

Maybe I should contact Ubuntu customer support?

---

### Post by NightwishFan on 2011-02-26
You might try a live cd of Ubuntu 10.10 to see if the issue is fixed. It does have a more upgraded X stack. I should say though that I never have any problems and I have a similar graphics card. So I do not know what is up with it. :/

---

