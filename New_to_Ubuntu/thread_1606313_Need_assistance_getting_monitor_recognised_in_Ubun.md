---
title: "Need assistance getting monitor recognised in Ubuntu 10.10"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by I Am Noob on 2010-10-26
Hey Guys,

I'm having trouble getting Ubuntu 10.10 to recognise my LG M228WA - BZ monitor!

Its a 22" screen and has always run at much higher resolutions than  1024x768, I do realise that my Nvidia graphics card(s) may have had some  role to play in that but i'm sure this monitor can run at something like 1680 x 1050 or above... so my question is HOW do I get Ubuntu to  recognise the true potential of my monitor? :confused:

I am a complete noob so if you could give me step-by-step instructions that would be great... also if I need to edit files I would need to know how to back-up the old and how to restore if I ended up at command line on re-boot!

:mrgreen:I Am Noob

p.s.

I have had some Nvidia issues in Ubuntu 10.10 but hoping i've fixed most of the issues in regards to that, you can see what i've installed to correct these issues in my other thread here: [http://ubuntuforums.org/showthread.php?t=1605491](http://ubuntuforums.org/showthread.php?t=1605491)

---

### Post by TeoBigusGeekus on 2010-10-26
```
gksu nvidia-settings
```
Select the resolution and then save to x configuration file.

---

### Post by I Am Noob on 2010-10-26
Hey [TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094"),

Thanks for the reply, I execute that command in the terminal but nothing appears to happen :(

:mrgreen:I Am Noob

---

### Post by Zzl1xndd on 2010-10-26
Have you installed the Nvidia driver yet? If not I believe the option is under System > Administration > Drivers (I am not at home and don't remember 100%) 

Ones installed you should be able to use the Nvidia control panel to adjust the settings.

---

### Post by I Am Noob on 2010-10-26
Thanks [tweakedenigma]("http://ubuntuforums.org/member.php?u=161141"),

But unfortunately I cannot install the Nvidia Driver and its settings because it doesn't work in Ubuntu 10.10... I have to use the Nouveau drivers that come default with the new Ubuntu distro :(

:mrgreen:I Am Noob

---

