---
title: "NVIDIA FX5200 fuzzy screen"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by imtheshade on 2009-07-18
Hi! I have a machine with a NVIDIA FX5200 grafic card and ubuntu 9.04 running. I activated the standard drivers for it, but whenever I change my resolution from 800x600 to 1024x768 my screen gets fuzzy and starts shaking. What can I do to fix this? Thanks in advance.

---

### Post by ~sHyLoCk~ on 2009-07-18
Post o/p of:
```
nvidia-settings -version
```

---

### Post by imtheshade on 2009-07-18
nvidia-settings:  version 1.0  (buildmeister@builder57)  Thu Jun 25 19:53:44
PDT 2009
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.

  Copyright (C) 2004 NVIDIA Corporation.

---

### Post by ~sHyLoCk~ on 2009-07-18
> **imtheshade said:**
> nvidia-settings:  version 1.0  (buildmeister@builder57)  Thu Jun 25 19:53:44
PDT 2009
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.

  Copyright (C) 2004 NVIDIA Corporation.

I'm so sorry, but I hoped that would provide me with your driver version. Anyway just type nvidia-settings and a window will pop up, see which driver you have installed. If its 173.14.20, then it's alright , however if you have 180+ then you have to uninstall and downgrade to 173.14.20. Since 5 series doesn't support 180+ drivers.

---

### Post by imtheshade on 2009-07-18
The version of the driver that's active right now is 96.43.10 but I got 173 installed as well, it's just that sometimes when I activate it, it won't display anything when I start my ubuntu, although the system appears to load, because I can hear the sound it plays when it starts up.

---

### Post by imtheshade on 2009-07-18
never mind.. I'm just gonna install another linux distro... the problems seem endless in ubuntu when it comes to my grafic card..

---

### Post by 3rdalbum on 2009-07-18
> **imtheshade said:**
> never mind.. I'm just gonna install another linux distro... the problems seem endless in ubuntu when it comes to my graphic card..

Realistically, the old Nvidia cards don't work that well in Linux because the drivers are from a time when Linux was much less user-friendly and less well supported by hardware vendors, and so Nvidia never copped the flak for making fussy drivers.

By all means, try another Linux distribution; but you will probably find that the best solution is to get a newer card.

---

### Post by imtheshade on 2009-07-19
actually, the card works perfectly under Mepis 8.0. My internet connection is also automatically detected in that distro, which only shows a lack of competence when it comes to ubuntu. Only problem there is that I can't get python 3.1 working.. synaptic is kinda broken and now my internet connection won't run on it for some odd reason..

---

### Post by ktrnka on 2009-07-19
Yes it is Ubuntu's fault cause THEY make the NVIDIA driver ...... YEA RIGHT! Misplaced blame right here!

If you were still having graphics driver problems you could have gone here:

[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by imtheshade on 2009-07-19
I gave ubuntu another chance and reinstalled it. The application on that site worked like a charm( the driver installed ok and works ). Only problem now is that my max resolution is 640x480 and the windows don't work properly any more. Any thoughts on how can I fix this ?

---

### Post by louieb on 2009-07-19
I have an fx5200 on a pc running hardy. works great with the 169.12 driver - might give that a shot.

---

### Post by imtheshade on 2009-07-19
is that ubuntu 8.04 ?

---

### Post by ktrnka on 2009-07-19
You should be able to access the nvidia-settings from the terminal

Applications > Terminal

```
sudo nvidia-settings
```

Once that launches, it should allow you to change the resolution.

---

### Post by kaibob on 2009-07-19
> **louieb said:**
> I have an fx5200 on a pc running hardy. works great with the 169.12 driver - might give that a shot.
Same here. I have an fx5200 and use Hardy with the 169.12 driver. No problems at all.

---

### Post by imtheshade on 2009-07-19
how do I install the 169.12 driver ?

---

### Post by imtheshade on 2009-07-19
> **ktrnka said:**
> You should be able to access the nvidia-settings from the terminal

Applications > Terminal

```
sudo nvidia-settings
```

Once that launches, it should allow you to change the resolution.

That is what I did, but the biggest resolution I could use was 640x480. I reinstalled ubuntu since then and installed the 173 driver using synaptic, but every time I run nvidia-settings I get an error message box telling me: "you do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

L.E.: Which I did, but after running nvidia-xconfig I did not get any response. The prompt jus switched to a new line just as if I were to plainly press enter.

---

### Post by louieb on 2009-07-19
> **imtheshade said:**
> how do I install the 169.12 driver ?

In Hardy (8.04) I just used System>Administration>Hardware Drivers

That was right after Hardy was released. Don't know if it works the same now. 

Might try getting from the Nvidia site [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

### Post by imtheshade on 2009-07-19
I will try that, thank you.

---

### Post by imtheshade on 2009-07-20
I solved the problem by installing Ubuntu Ultimate. It works perfectly.

---

