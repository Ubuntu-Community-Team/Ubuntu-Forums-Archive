---
title: "Emerald in Jaunty"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Evilhugbear on 2009-04-28
Hello, I was looking at something on the forums and it said that Emerald can Install custom themes. I decided to try it and found a theme I would like to try. My problem is that when It tells you how to make it run at startup it says go to system>preferences>Sessions but I don't have it here. Is there a different way to do this? And also, I imported my theme into emerald but I don't know how to enable it. Can someone tell me how?

Thanks

---

### Post by Evilhugbear on 2009-04-28
This is the theme : [http://ptpbs.deviantart.com/art/Union-Limited-Blue-107449353](http://ptpbs.deviantart.com/art/Union-Limited-Blue-107449353)
Do I need anything extra or something?

---

### Post by oldos2er on 2009-04-28
Once you import it into Emerald, click on it to enable it.

---

### Post by Evilhugbear on 2009-04-28
> **oldos2er said:**
> Once you import it into Emerald, click on it to enable it.
I do and nothing happens. :confused:

---

### Post by emeraldgirl08 on 2009-04-28
I have the same question.

Does the GTK designation have anything to do with this? Is there an extra program I need to download from the synaptic packet manager???

I've installed the linux-version of 7zip and extracted the folders. I've tried dragging them into the themes menu. 

No luck yet.

---

### Post by oldos2er on 2009-04-28
> **Evilhugbear said:**
> I do and nothing happens. :confused:

 Are you running compiz as window manager? You need to be in order for Emerald to work.

---

### Post by Evilhugbear on 2009-04-28
> **oldos2er said:**
> Are you running compiz as window manager? You need to be in order for Emerald to work.
how do I do this? I have window decoration enabled. Is that it?

---

### Post by oldos2er on 2009-04-28
System, Preferences, Appearance, Visual Effects, Extra.

---

### Post by Evilhugbear on 2009-04-28
I went and enabled extra there and went into emerald and clicked the theme but still nothing happened.
Do I have to like restart?

---

### Post by tjwoosta on 2009-04-28
> I do and nothing happens. 

nothing is happening because you need to start emerald first


press alt-f2 and in the box that pops up type emerald --replace
(this will only run emerald for this session, so you need to add the command to the startup programs)

the startup programs used to be located at system-preferences-sessions but i have not used jaunty yet so i dont know where it is located now


actually there are two ways to start emerald

1. add emerald --replace to the startup programs 


2. install compiz fusion icon and add fusion-icon to the startup programs, then select emerald as the window decorator in the fusion-icon options


EDIT: ok turns out the startup programs in jaunty should be located at System -> Administration ->Startup Programs

---

### Post by Almighty on 2009-04-28
Also make sure that you set your window decorator is set to Emerald also. I had the same issue when I first installed the app. For some reason Ubuntu didn't select Emerald by default, I had to tell it to.

---

### Post by Kareeser on 2009-04-28
That's correct. By default, compiz-decorator is used.

You can either set "emerald --replace" to start-up automatically, as instructed, or you can change the setting "Window Decorator" in compizconfig-settings-manager to reflect /usr/bin/emerald.

---

### Post by Evilhugbear on 2009-04-29
Thanks Guys. I got it to work but I don't know how to make it start on startup. And also, Ubuntu will freeze after I click a second custom theme.

---

### Post by Evilhugbear on 2009-04-29
> **Kareeser said:**
> That's correct. By default, compiz-decorator is used.
 
You can either set "emerald --replace" to start-up automatically, as instructed, or you can change the setting "Window Decorator" in compizconfig-settings-manager to reflect /usr/bin/emerald.
 Wait, so if I change it to that in compiz, emerald will start on startup?

---

### Post by Evilhugbear on 2009-04-29
thanks I got emerald to work by doing alt+f2 and running it. I also set it to run on startup, and that crash didn't happen :D

---

