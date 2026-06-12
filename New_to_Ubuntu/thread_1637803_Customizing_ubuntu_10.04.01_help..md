---
title: "Customizing ubuntu 10.04.01 help."
date: 2010-12-04
forum: New to Ubuntu
---

### Post by mayt on 2010-12-04
I watched a lot of videos about people with really cool setups and I'm wondering how i set this up myself. I have ubuntu 10.04.01. It's my first time using linux and a figured out how to change basic settings like i have a new theme,background,icons,whopply window. I see some people say they you get it from compiz which i download but it doesn't look i can get much custom from it. 

what my compiz looks like [http://img338.imageshack.us/i/screenshotxa.png/](http://img338.imageshack.us/i/screenshotxa.png/)

where do i go so i can test out use some cool effects. i want something like in this video [http://www.youtube.com/watch?v=VvfRpmqKRbs](http://www.youtube.com/watch?v=VvfRpmqKRbs)

the main things I'm trying to get are:

-bottom tool bar with tux walking around
-fire when opening windows
-weather and cpu usage side bars
- where you can stack window behind another
- the cool 3d cube view 
-move mouse and get water drops 
-write on the screen with fire

thanks for the help


also people tell me i don't need anti virus for linux, but are there anti virus.antispyware,firewall that work on Linux?

---

### Post by conradin on 2010-12-04
Beryl will do the fire animations. AWN is also very useful. Though not as hip perhaps, docky tends to work well. 
Conky will give you the runtime info and can be customised in nearly limitless ways.

What's your graphic controller? I have a intel 915 which I know wont do half of that stuff smoothly. Just a thought.

---

### Post by mayt on 2010-12-04
> **conradin said:**
> Beryl will do the fire animations. AWN is also very useful. Though not as hip perhaps, docky tends to work well. 
Conky will give you the runtime info and can be customised in nearly limitless ways.

What's your graphic controller? I have a intel 915 which I know wont do half of that stuff smoothly. Just a thought.
  I'm not sure which i have how can i find this out? also this is on a laptop if it matters. where do i download that stuff software center?

---

### Post by sikander3786 on 2010-12-04
> **mayt said:**
> I'm not sure which i have how can i find this out? also this is on a laptop if it matters. where do i download that stuff software center?
Applications > Accessories > Terminal

```
lspci | grep VGA
```

Post the output ;-)

---

### Post by mayt on 2010-12-04
> **sikander3786 said:**
> Applications > Accessories > Terminal

```
lspci | grep VGA
```Post the output ;-)
this is what it says VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

---

### Post by sikander3786 on 2010-12-05
> **mayt said:**
> this is what it says VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
System > Administration > Hardware Drivers lists any active drivers?

---

### Post by akand074 on 2010-12-05
Your missing some Compiz settings. Go to Accessories > Terminal and paste this:

```
sudo apt-get install compiz-fusion-plugins-extra
```

To run desktop cube just enable it from compiz. Make sure you have your proprietary drivers installed. (System > Administration > Additional Drivers).

---

### Post by mayt on 2010-12-05
> **sikander3786 said:**
> System > Administration > Hardware Drivers lists any active drivers?
no drivers are listed how can i add my driver

---

### Post by sikander3786 on 2010-12-05
> **mayt said:**
> no drivers are listed how can i add my driver
I believe drivers for X1200 are no longer supported on Lucid and Maverick. There is a workaround though.

You can install the open source ATI as per instructions here.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

