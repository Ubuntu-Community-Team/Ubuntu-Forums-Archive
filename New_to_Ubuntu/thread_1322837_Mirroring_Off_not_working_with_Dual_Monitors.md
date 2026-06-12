---
title: "Mirroring Off not working with Dual Monitors"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Azrael3000 on 2009-11-11
Hi,

I'm currently trying to use to monitors on my computer. Both of them currently show the same (i.e. are mirrored). When I run gnome-display-properties I get the gui where I can deselect "Mirror screens". If I then click apply nothing changes on the screens. But in the terminal there is a short error message:

```

***:/etc/X11$ gksudo gnome-display-properties

(gnome-display-properties:29194): Gtk-WARNING **: No object called: 
gnome-display-properties: symbol lookup error: gnome-display-properties: undefined symbol: ubuntu_compute_virtual_size_for_configuration

```

While running gnome-display-properties if I uncheck the box I can actually 'see' my two monitors in the small graphics inside the gui. So the monitors are recognised and I can even shift their position.

Do I need to setup Xinerama or something like that to make it work?

Some information:
```

***:/etc/X11$ lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
***:/etc/X11$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
DVI1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0*+
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

```Thanks in advance,
Arno

---

### Post by Azrael3000 on 2009-11-13
More information...

If I execute
```
xranrd --output VGA1 --pos 767x0
```everything is fine and one monitor is actually shifted as I want it. If I enter 768 the monitors both look weird (i.e. all messed up, can't recognise anything). Note that a shift of 768 means that my total resolution is 2048 x 1024 (both screens run on 1280x1024). As soon as my total resolution goes above 2048 the screens go black, shifting back solves the problem. Is this 2048 px a hardware limitation or something that can be overcome by software?

Hardware is actually not so much possible since this guy here: [http://n2.nabble.com/Intel-915GM-dual-screen-1280x1024-and-1024x768-td1464888.html](http://n2.nabble.com/Intel-915GM-dual-screen-1280x1024-and-1024x768-td1464888.html) got it all running apparently. However note that I'm using a DVI connection for the second monitor and he doesn't.

[edit]
If I shift to 0x1023 I do have two seperate monitors. But of course one is above the other which is kinda inconvenient. Again if I shift to 0x1024 (= total resolution 1280x2048) the screens crash.
[/edit]

Best,
Arno

---

