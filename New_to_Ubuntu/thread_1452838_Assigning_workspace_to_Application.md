---
title: "Assigning workspace to Application"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by kdev10 on 2010-04-12
Can we assign workspace for application automatically when it starts  say , firefox automatically starts on workspace 1  even though iam  working in workspace 2 . 
If so how. 

I know i can manually move from one workspace to other but if i wish to do automatic how. 

Please suggest

---

### Post by wojox on 2010-04-12
[Devil's Pie]("http://foosel.org/linux/devilspie") It's in the repo's .

```
sudo apt-get update; sudo apt-get install devilspie
```


```

; Move firefox to workspace 1
(if 
  (is (application_name) "firefox-bin") 
  (set_workspace 1)
)

```

For the above you need to make a firefox.ds file and put it in .devilspie directory.

---

### Post by lovinglinux on 2010-04-12
There is a Compiz plugin that allows you to specify the workspace for each application. I just don't remember the name of the plugin, since I'm using KDE for a while. I guess it is Window Rules or something else.

---

### Post by nothingspecial on 2010-04-12
> **lovinglinux said:**
> There is a Compiz plugin that allows you to specify the workspace for each application. I just don't remember the name of the plugin, since I'm using KDE for a while. I guess it is Window Rules or something else.

I don`t think window rules does, or any compiz plugins.....default at least.

Ofcourse I don`t use it either so could be wrong.

---

### Post by lovinglinux on 2010-04-12
> **nothingspecial said:**
> I don`t think window rules does, or any compiz plugins.....default at least.

Ofcourse I don`t use it either so could be wrong.

[Here it is](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=7320754&postcount=6).

---

### Post by nothingspecial on 2010-04-12
> **nothingspecial said:**
>  so could be wrong.

Educated by lovinglinux once again.


****no offence meant, just I remember this happening once before****

minimal kde maybe?????

---

### Post by lovinglinux on 2010-04-12
> **nothingspecial said:**
> Educated by lovinglinux once again.


****no offence meant, just I remember this happening once before****

minimal kde maybe?????

I use kde-minimal too, with kwin. Is getting harder to remember how to do things in gnome every day. :)

I guess I should install Gnome on a VM, just to provide support for other users.

---

### Post by nothingspecial on 2010-04-12
Nah, I meant [COLOR="Magenta"][this]("http://ubuntuforums.org/showthread.php?t=1388660")[/COLOR]

How do you keep so up to date?

---

### Post by lovinglinux on 2010-04-12
> **nothingspecial said:**
> Nah, I meant [COLOR="Magenta"][this]("http://ubuntuforums.org/showthread.php?t=1388660")[/COLOR]

How do you keep so up to date?

Ah, I see. It was just a coincidence, because before installing kde-minimal on Karmic I tried the psychocats tutorial and couldn't find kde-core package. So I did some research and found that kde-minimal was what I wanted.

---

### Post by Greenbean209 on 2010-04-12
I can see this thread is already going off topic. Kdev, on my system what usually happens is that the window appears on the workspace where it was when it last closed. You can move it to workspace 2 by pressing a key combination, or if you have the the Compiz cube activated you can simply slide it offscreen and into the second workspace. You can find the key combinations under your compiz settings. I'll get back to you on where the settings are specifically located.

---

