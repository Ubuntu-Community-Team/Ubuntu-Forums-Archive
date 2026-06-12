---
title: "Video drivers"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by whatawholeone on 2010-04-12
I installed the recomender video card driver and now it cant boot, what can i do?

---

### Post by sydbat on 2010-04-12
> **whatawholeone said:**
> I installed the recomender video card driver and now it cant boot, what can i do?We need a lot more information before we can help you properly.

What version of Ubuntu are you using?
What video card do you have?
What is happening at boot?

---

### Post by whatawholeone on 2010-04-12
Im using  9.10

The video card is a Geforce GT 130M in an acer laptop

and im duel booting windows 7 after selecton to boot ubuntu the screen just stays blank and this onll started after installing the drivers.

---

### Post by sydbat on 2010-04-12
OK. When you boot, the Grub menu shows up with your OS choices. There should be at least 2 for Ubuntu (they are the kernel versions), one that is for a normal boot and the one under it for recovery. Choose the recovery one.

Then it will show you a screen with some more choices, similar to this one.
[IMG]http://1.bp.blogspot.com/_LKra8AUL9bY/SRleYPWhWfI/AAAAAAAAALY/MetRjP9OxqU/s400/20081111149.jpg[/IMG] 

The option to "**xfix**" *should* fix any problem with the graphics driver and allow you to boot into your desktop. There is also the dpkg option, which fixes broken packages (like a video driver).

You can do both of these before booting normally (resume).

---

### Post by whatawholeone on 2010-04-12
In the recovery menu i only get 

[LIST]
[*]resume
[*]clean
[*]dpkg
[*]grub
[*]netroot
[*]root
[/LIST]
I tried the dpkg but this has made no difference.

---

### Post by sandyd on 2010-04-12
> **whatawholeone said:**
> In the recovery menu i only get 

[LIST]
[*]resume
[*]clean
[*]dpkg
[*]grub
[*]netroot
[*]root
[/LIST]
I tried the dpkg but this has made no difference.
choose root.

type this in.
```

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
shutdown 0 -r
```

---

### Post by whatawholeone on 2010-04-13
> choose root.
 
 type this in.
      Code:
     mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
shutdown 0 -r 
 OK thanks that's worked, but what did it do?
and now I cant enable visual effects they worked before i installed the nvidia driver

---

### Post by realzippy on 2010-04-13
> **whatawholeone said:**
> OK thanks that's worked, but what did it do?
and now I cant enable visual effects they worked before i installed the nvidia driver


..this disabled your nvidiadriver.Which one did you install?
	
195.36.15  should be the one for your card.

---

