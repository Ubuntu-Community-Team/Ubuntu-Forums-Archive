---
title: "AWN - How To Maximize Window"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by rclowery on 2010-04-12
Hi Everyone,

I'm trying to use AWN with Ubuntu 9.10 on a small 13 inch laptop. I'd like to be able to maximize my windows to take up the entire empty desktop, but for whatever reason AWN keeps the space it needs for the dock below each window empty, even when the dock is hidden. What I'd like it to do is let me expand the window to fill the screen and allow me to raise the dock from hiding while overlapping the expanded window. 

Does anyone know the setting I need to alter to make this possible?

Thank you,

RC

---

### Post by labinnsw on 2010-04-19
> **rclowery said:**
> I'd like to be able to maximize my windows...

Does anyone know the setting I need to alter to make this possible?

1.    Right click on the dock.
2.    Select "Dock Preferences."
3.    Ensure the "General" tab is selected
4.    Under the "Bar behaviour" heading, uncheck "Maximized windows don't cover the bar."
5.    In a terminal, type ```
killall awn
``` then ```
awn
```
And you are set

Perfect title by the way.

---

### Post by scottiw2000 on 2010-04-19
By the way, you might want to try out "Docky" as a replacement for AWN. I find it much faster and easier on resources. It also is much better at handling things like vertical docks on the side of a screen, something I use a lot on my wide-screen laptop where vertical screen-space is at a premium. 

Docky is in the repositories for the upcoming 10.4 (Lucid Lynx) release, so you'll be able to just install it from Ubuntu Software Centre. Since you're running Karmic you can just open a terminal and run:

sudo add-apt-repository ppa:docky-core/ppa

That will add the official Docky repository to your software sources list. Then just:

sudo apt-get install docky

---

### Post by fabounet on 2010-04-20
try also Cairo-Dock, which is imho the best of the 3. There are several visibility modes (like auto-hide or keep the dock below) that will allow windows to be maximised.

---

### Post by empty_spaces on 2010-04-20
Since we have a vote for Docky and Cairo, I'd like to put in my vote for AWN.
Having tried all three (AWN, Docky, CairoDock) docks, I prefer the latest AWN dock. Version 0.4 of AWN is a vast improvement over previous versions, and I don't find it resource heavy at all. Although Docky does feel pretty snappy, I thought AWN had a lot more features/customizations. 
I've used Cairo the least, and have found it to be the most unstable of the 3.

Here are a few screenshots of AWN 0.4.1 on my system.

---

