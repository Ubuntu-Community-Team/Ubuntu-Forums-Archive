---
title: "Configure Logitech LX7 Cordless buttons Ubuntu 9.10"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by rpachecoh on 2009-12-24
Hi all,

I am a Linux beginner right now, usig Ubuntu 9.10 x64. I have a 7 buttons mouse (Logitech LX7) and I would like to know if I can configure their functionalities. I've been reading about earlier Ubuntu distributions, but I cannot make it work right now. 

First of all, using xev I get that:

        b1 left
        b2 wheel press
        b3 right
        b4 wheel up
        b5 wheel down
        b8 secondary button left
        b9 secondary button right
        b11 wheel left
        b12 wheel right

I usually used wheel left and right to go back and forward (what is right now configured in secondary buttons) and secondary buttons to minimize and maximize windows. What can I do to change that configuration now?

Thanks in advance.

---

### Post by milosz.galazka on 2009-12-24
Maybe you can start searching for answer here:
[http://ubuntuforums.org/showthread.php?t=1360558](http://ubuntuforums.org/showthread.php?t=1360558)

---

### Post by rpachecoh on 2009-12-24
Thanks Milosz,

I searched before posting but I got nothing, cause I tried what you have just posted. I've been trying further and I found out some of my problems.

Using xev, when I push the wheel to the left, I get b6 and b11 (b7 and b12 to the right), so I do not know how to configure .xbindkeysrc to make it work. Now, I have this (the first two lines are working properly

```
"echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStr D KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:8
"echo 'KeyStrPress Alt_L KeyStr F10 KeyStrRelease Alt_L' | xmacroplay :0"
b:9
"echo 'KeyStrPress Alt_L KeyStr Left KeyStrRelease Alt_L' | xmacroplay :0"
b:6
"echo 'KeyStrPress Alt_L KeyStr Right KeyStrRelease Alt_L' | xmacroplay :0"
b:7
```

---

### Post by milosz.galazka on 2009-12-24
Unfortunately on this computer I don't have bluetooth, but later I could try to check logitech v470 with allows pushing wheel to the sides.

I only saw examples:
```
"/usr/bin/xvkbd -xsendevent -text '\[Control_L\]\[Next]'"
m:0x0 + b:11

"/usr/bin/xvkbd -xsendevent -text '\[Control_L\]\[Prior]'"
m:0x0 + b:12
```

```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```

```
"/usr/bin/xvkbd -xsendevent -text "\[left]""
b:11
"/usr/bin/xvkbd -xsendevent -text "\[right]""
b:12
```

```
"echo ButtonPress 2 ButtonRelease 2 Delay 0 | xmacroplay -d 0 :0.0"
release+b:11

"echo ButtonPress 2 ButtonRelease 2 Delay 0 | xmacroplay -d 0 :0.0"
release+b:12
```

```
"dcop kwin KWinInterface previousDesktop"
m:0x10 + b:11
"dcop kwin KWinInterface nextDesktop"
m:0x10 + b:12
```

---

### Post by nishant.singh28 on 2009-12-24
Try using Imwheel....works fine with my Dell BT Travel Mouse...

---

### Post by rpachecoh on 2009-12-24
Finally I used: 

```
"echo 'KeyStrPress Control_L KeyStrPress Alt_L KeyStr D KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:8
"echo 'KeyStrPress Alt_L KeyStr F10 KeyStrRelease Alt_L' | xmacroplay :0"
b:9
"echo 'KeyStrPress Alt_L KeyStr Left KeyStrRelease Alt_L' | xmacroplay :0"
b:6+b:11
"echo 'KeyStrPress Alt_L KeyStr Right KeyStrRelease Alt_L' | xmacroplay :0"
b:7+b:12
```

Left and Right Wheels, what means combined buttons, works fine for Nautilus and fails some times for Firefox, but is good enough right now. 

Thanks for your help.

---

