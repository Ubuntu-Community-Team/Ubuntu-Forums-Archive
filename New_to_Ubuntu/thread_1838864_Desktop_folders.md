---
title: "Desktop folders"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Dead root on 2011-09-04
Hello,

I am using Ubuntu 11.04 classic view (no unity) when I logged in there's no folders in the desktop. I tried to make the "Home" folder appear on the desktop but it appears as a screenshot. How can i put the same "Home" folder in the desktop? like the unity version?

Thanks.

---

### Post by mikewhatever on 2011-09-04
Why, was the home folder ever on the desktop?

---

### Post by Dead root on 2011-09-04
> **mikewhatever said:**
> Why, was the home folder ever on the desktop?
When you install it you can see "Home" folders. I don't know if it's shortcut but the icon is different.

Like this pic
[IMG]http://arrasthemes.com/wp-content/uploads/2011/06/1307602813-97.jpg[/IMG]

How can i add the real icon of Home in the desktop?

---

### Post by coffeecat on 2011-09-04
> **Dead root said:**
> How can i put the same "Home" folder in the desktop? like the unity version?

Unity doesn't have the home folder on the desktop by default. Anyway...

Press Alt-F2. Type "gconf-editor" (no quotes). In gconf-editor, apps -> nautilus -> desktop. Tick the home_icon_visible box. You can also enable computer, network and trash icons as well.

Note that this will not work in 11.10/Oneiric when it is released because Oneiric is based on gnome 3.

---

### Post by Dead root on 2011-09-04
> **coffeecat said:**
> Unity doesn't have the home folder on the desktop by default. Anyway...

Press Alt-F2. Type "gconf-editor" (no quotes). In gconf-editor, apps -> nautilus -> desktop. Tick the home_icon_visible box. You can also enable computer, network and trash icons as well.

Note that this will not work in 11.10/Oneiric when it is released because Oneiric is based on gnome 3.
YEY it works :) I can see the Home icon now :)

I have another question, what about the Filesystem? I mean I see a lot of folders, what to do there? The dekstop / home /..everything are there?

---

### Post by coffeecat on 2011-09-04
> **Dead root said:**
> I have another question, what about the Filesystem? I mean I see a lot of folders, what to do there?

Best left alone until you have some experience and you know what you are doing. All the folders except /home are system ones. You can read an overview of the Linux filesystem hierarchy here:

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

> **Dead root said:**
>  The dekstop / home /..everything are there?

If you are looking at the filesystem, open /home and you will see your account folder. Open that and you will see a Desktop folder which is your desktop. More or less the same as in Windows. But if you want to view your desktop as a folder, you can do that from inside the nice shiny home folder icon you now have on your desktop! :)

---

### Post by Dead root on 2011-09-04
This is so good :) Thank you my friend. 

Yes I used Windows since I was 9 years old and using Ubuntu now but it seems great, I need to read more (do you know a good tutorial site?) like tricks and few things? I still need to discover more :)

Btw, Now I plugged my USB, I click remove, it removed but after 5 secs it opened again :confused: is that a bug?

---

### Post by coffeecat on 2011-09-04
> **Dead root said:**
> Btw, Now I plugged my USB, I click remove, it removed but after 5 secs it opened again :confused: is that a bug?

Yes. Some people are seeing this with nvidia USB controllers, and some with some (but not all) Intel USB controllers. If you "safely remove" a second time it won't remount again.

---

### Post by zero2xiii on 2011-09-04
> Yes I used Windows since I was 9 years old and using Ubuntu now but it seems great, I need to read more (do you know a good tutorial site?) like tricks and few things? I still need to discover more

Hay, glad to hear you switched :)... The awsum thing about linux is its hard to break. If you are promoted for a password, STOP. Other than that, you can pretty much screw around as much as you want, all the 'damage' you can do as a normal user is reversable without format. But the moment you need to enter a password to continue, you KNOW this effects the entire system.

As far as guides go, there are a few, google it. But experience is best gather trough personal experimentation, just like you had to learn windows, you need to learn linux. Wikipedia is stacked with very good and up to date information. Play around the forums (esp the newbie section). But get your hand dirty, its the only way you will learn the inner workings :)

Enjoy! And welcome...

---

