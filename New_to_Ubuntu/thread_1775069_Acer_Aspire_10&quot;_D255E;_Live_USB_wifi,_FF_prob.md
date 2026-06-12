---
title: "Acer Aspire 10&quot; D255E; Live USB: wifi, FF problems"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by yc2 on 2011-06-04
Hi,

I just bought an **Acer Aspire 10" D255E** netbook. I want to run the Live CD from USB. I downloaded 11.04 Live CD and used two ways to put it on the flash drive:

_1. Unetbootin:_
The netbook will boot properly and show the Unity desktop, but the mousepointer is frozen. Touchpad does not work.

Somewhat better result with Pendrivelinux:

_2. Pendrivelinux:_
The netbook boots properly. The mousepointer works from the touchpad. When I press openoffice it opens openoffice. It tells me that it has found the wifi network I want to connect to. (It gives the name of the wifi network properly)
However:
a. When I enter password for [COLOR="Red"]wifi network it will not connect[/COLOR].
b. When I press Firefox in Unity, nothing happens, [COLOR="red"]no browser opens[/COLOR].

Very grateful for suggestions how to continue.

Thanks

ycc

---

### Post by I2k4 on 2011-06-04
From Windows, I've used these instructions six or eight times on two laptops, including my first gen Acer netbook, and step by step (Review the Show Me How) they are bullet-proof:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

The one extra step is at the end of Step 2 to use the installer to set "persistence" so the USB will save settings between reboots - generally set Persistence for everything above 1GB of USB space - the OS runs quite well even on a 2GB USB drive.  Everything has worked immediately using these directions, including everything on 11.04 in Unity, though I found 11.04 much slower than 10.10 on my netbook and don't like the Unity interface.

There are a few additional tricks to economizing on limited speed and space running from Live USB but that's a longer story.

---

### Post by yc2 on 2011-06-04
Thanks I2k4,

I forgot to say that the instructions in the link you gave were the ones I used for "Pendrivelinux". No problems appeared when I followed the instructions and the netbook booted properly on the flash-drive. (I think i set 4G persistence on a 8G stick)

But like I wrote above, it identifies wifi network but cannot log on. When I click firefox in Unity, nothing happens.

Still need help, please.

---

### Post by yc2 on 2011-06-04
This thread is solved.
Rune.K, chief mod in Swedish ubuntu.se told me there is a problem with the FF in Unity. You have to start FF by typing the pgm name into the terminal.
The wifi connected well. 11.04 maybe needed a little more signal strength than Win7 to connect? (I think that was also the case in Ubuntu vs Win XP some time ago in my laptop.)
Thanks everyone who considered the matter.
(Sorry for tagging wrongly, I tagged Lubuntu instead of Ubuntu. 10" screens are a hazard for old geezers like yours truly ;) I cant find how to retag, sorry.)

---

### Post by I2k4 on 2011-06-04
I'm glad you find it "solved" to your satisfaction, though it sounds very weird to me to have to type something into a terminal to make FireFox work. I don't think that's in the business plan for Ubuntu.  Of course, Sweden is a unique country.

---

### Post by yc2 on 2011-06-04
I dont think the problem with having to start FF from the terminal is unique to Sweden (but I am not sure).

I reside in the Philippines. I bought this netbook here a week ago. I downloaded the Desktop Cd from ubuntu.com

My Swedish friend had experienced the same problem in Sweden.

[COLOR="Red"]Maybe this is a significant problem that the developers should address quickly?????[/COLOR]

(I dont know if the problem is limited to the USB installation, though)

---

