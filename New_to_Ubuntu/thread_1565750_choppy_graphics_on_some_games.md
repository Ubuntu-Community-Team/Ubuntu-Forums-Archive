---
title: "choppy graphics on some games"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by m3t3ors on 2010-09-01
im running ubuntu 10.04 on my dell latitude d520 with intel graphics card but on some games under wine it seems to give choppy graphics. anyone help me out please

---

### Post by chinoto on 2010-09-01
According to [CNET]("http://reviews.cnet.com/laptops/dell-latitude-d520-intel/4507-3121_7-31861593.html?tag=rnav") you have a GMA 950, which is the lowest in the line of GMA chips. Compared to practically any ATI or nVidia chip, GMA is garbage. So unless you are playing a very simple (graphics wise) game, expect your games to be slow and bad quality.

Sliver of Hope: Did you make sure to install the driver for your chip? In the top panel go to System > Hardware Drivers, and activate whatever seems newest. After I installed my nVidia driver I didn't notice a difference, so I went into the settings, it told me to do nvidia-xconfig in terminal, you may need to do something similar.

---

### Post by Jazzy_Jeff on 2010-09-01
Also make sure you disable the compiz desktop effects as they use your graphics card as well.

---

### Post by Mark Phelps on 2010-09-01
> **chinoto said:**
> ... In the top panel go to System > Hardware Drivers, and activate whatever seems newest. After I installed my nVidia driver I didn't notice a difference, so I went into the settings, it told me to do nvidia-xconfig in terminal, you may need to do something similar.

Nvidia and ATI are different from Intel in that they sometimes offer proprietary driver updates through the Hardware Drivers panel.

In the case of Intel, the drivers are already loaded as part of the initial setup.  Don't expect to find anything offered in the Hardware Drivers panel.

---

### Post by m3t3ors on 2010-09-01
> **chinoto said:**
> According to [CNET]("http://reviews.cnet.com/laptops/dell-latitude-d520-intel/4507-3121_7-31861593.html?tag=rnav") you have a GMA 950, which is the lowest in the line of GMA chips. Compared to practically any ATI or nVidia chip, GMA is garbage. So unless you are playing a very simple (graphics wise) game, expect your games to be slow and bad quality.

Sliver of Hope: Did you make sure to install the driver for your chip? In the top panel go to System > Hardware Drivers, and activate whatever seems newest. After I installed my nVidia driver I didn't notice a difference, so I went into the settings, it told me to do nvidia-xconfig in terminal, you may need to do something similar.

in hardware drivers it doesnt show anything

how do i disable desktop effects?

---

### Post by [::AP::] on 2010-09-01
I feel your pain. My current laptop has Intel GMA 945, and it really can't run any heavy graphics. 

There are some solutions, however, like taking the load off of it (disable eyecandy when playing).

I did this in Windows:

[http://www.gmabooster.com/home.htm]("http://www.gmabooster.com/home.htm")

It gave an ever so slight increase in performance. It is slightly like overclocking (be careful). 

Best of luck,

[::AP::]

---

### Post by [::AP::] on 2010-09-01
> **m3t3ors said:**
> how do i disable desktop effects?

I *think* this is what you mean...

Go to **System > Preferences > Appearance > Visual Effects**

Disable when gaming. 

My GMA 945 handles the "Extra" flawlessly when not gaming (I don't play games on Linux). 

Again, best of luck,

[::AP::]

---

### Post by m3t3ors on 2010-09-01
how do i install or run gmabooster?

ive tried all kinds of commands

---

### Post by Mark Phelps on 2010-09-01
> **m3t3ors said:**
> how do i install or run gmabooster?

Basically ... you don't! It's an MS Windows app, not a Linux app.

You basically have a low-end graphics chip. You have what you have.

---

### Post by chinoto on 2010-09-02
Before playing a game it may help to look at "System> Administration> System Monitor" and ending a few hungry processes. Make sure to close anything using Flash because the Linux version isn't optimized very well. Try out Nexuiz, I would like to hear how well it runs on a GMA chip. [Site]("http://alientrap.org/nexuiz/") | [Torrent]("http://morfar.affro.net/nexuiz/torrents/nexuiz-252.zip.torrent")

---

