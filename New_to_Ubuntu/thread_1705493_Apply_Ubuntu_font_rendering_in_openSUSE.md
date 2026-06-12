---
title: "Apply Ubuntu font rendering in openSUSE"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by maciej234 on 2011-03-12
The way fonts look in Ubuntu 10.10 is clean and "normal", and I want to apply the look/style to openSUSE 11.4.  For some reason the font is very poor looking non matter what font I try.  Is anyone familiar with how to get this done? Thanks

---

### Post by howefield on 2011-03-12
Have you tried copying the font to /usr/share/fonts and running SuSEconfig ?

---

### Post by coffeecat on 2011-03-12
Font rendering still dreadful in the latest Suse release, is it? Thanks for warning me. That's at least two hours of my life you've saved now that I know I'll be confronted with some of the ugliest font rendering in the known universe if I were to try the latest Suse.

It's a shame, because around the 9.3 release of Suse, its font rendering was about the best in the Linux world. But it seems to have been a steady downhill progression ever since. I don't think it's the fonts themselves that are the problem; it's the configuration for rendering. And the rendering choices in the gnome appearance preferences won't help unfortunately.

In a previous version of Suse I tried removing the whole contents of /etc/fonts/ where all the configurations are kept and replacing them with the contents of /etc/fonts/ from Ubuntu. I don't think that helped all that much, but you could try that.

---

### Post by howefield on 2011-03-12
> **coffeecat said:**
> Font rendering still dreadful in the latest Suse release, is it?

It is for me, so I understand the OP wanting to better it.

I'm trying out openSUSE 11.4 KDE, I seem to remember something about it being one of the best KDE implementations, however the default font rendering is quite awful.

Not to say it can't be improved, I'll play about a bit more later.

---

### Post by coffeecat on 2011-03-12
> **howefield said:**
> I'm trying out openSUSE 11.4 KDE, I seem to remember something about it being one of the best KDE implementations, however the default font rendering is quite awful.

KDE font rendering seems to be different from gnome font rendering, but I don't know enough about the subject to work out exactly what's wrong - for my eyes at least. I've got Natty Ubuntu and Natty Kubuntu on adjacent partitions on my main desktop machine. The font rendering in Ubuntu is beautiful. In Kubuntu, it's.... meh! But not as bad as I've seen in earlier versions of Suse, and the gnome Suse font rendering in 11.3 looked very much like the rendering in KDE. Not good to my eyes.

I'm so glad there are at least two people who feel the same as me. I posted a "nice distro - pity about the font rendering" about Suse 11.3 on another forum and someone said that I needed a new monitor. :|

---

### Post by coffeecat on 2011-03-13
> **coffeecat said:**
> The font rendering in Ubuntu is beautiful. In Kubuntu, it's.... meh!

I have done Kubuntu a gross injustice. Mea culpa!

Kubuntu comes with anti-aliasing disabled by default. System Settings > Application Appearance > Fonts > Use anti-aliasing = enabled, Configure button > Hinting Style = Slight, and then it's almost as good as in Ubuntu/gnome. Or at least it is after you click on Apply and restart the application you want to use, or log out and log in again if you want to see the changes in the desktop. Which is something of a contrast to the instant changes you see in gnome's font configuration. KDE configuration... Meh! :rolleyes:

This is in Natty Kubuntu, by the way.

@maciej234 and/or @howefield, back on-topic, have you had any luck making openSUSE's fonts look any better?

---

### Post by maciej234 on 2011-03-14
> **coffeecat said:**
> Font rendering still dreadful in the latest Suse release, is it? Thanks for warning me. That's at least two hours of my life you've saved now that I know I'll be confronted with some of the ugliest font rendering in the known universe if I were to try the latest Suse.

It's a shame, because around the 9.3 release of Suse, its font rendering was about the best in the Linux world. But it seems to have been a steady downhill progression ever since. I don't think it's the fonts themselves that are the problem; it's the configuration for rendering. And the rendering choices in the gnome appearance preferences won't help unfortunately.

In a previous version of Suse I tried removing the whole contents of /etc/fonts/ where all the configurations are kept and replacing them with the contents of /etc/fonts/ from Ubuntu. I don't think that helped all that much, but you could try that.


Yeah not sure why I couldn't make it look good, I ended up just bailing out on the distro and going to Mint.

---

### Post by coffeecat on 2011-03-14
> **maciej234 said:**
> Yeah not sure why I couldn't make it look good, I ended up just bailing out on the distro and going to Mint.

To be honest, I quite understand, although I did eventually go back on my promise to myself and try a test installation of the gnome version of opensuse 11.4. Despite my prior bad experience of fonts in earlier versions, it didn't take long to get the fonts looking almost as good as in Ubuntu. It is doable. Nevertheless, I won't be spending much time with it. There were some other things that put me off.

---

### Post by antekone on 2011-05-11
Anyway, here's a small how-to regarding better fonts in OpenSUSE 11.4 (sorry, but I don't know anything about other versions). It's probably not the same way as Ubuntu does, but it's better than original and similar to Ubuntu's.

1. do a **zypper dup**, to get your system up-to-date.
2. add the **[namtrac]("https://build.opensuse.org/project/show?project=home%3Anamtrac")** subpixel repository from OpenSUSE's Build service: 

```
zypper ar http://download.opensuse.org/repositories/home:/namtrac:/subpixel/openSUSE_11.4/home:namtrac:subpixel.repo
```3. update your repository cache: **zypper ref**
4. then, update your system again (**zypper dup**, this time it will use freetype binaries from namtrac's repo (which includes **[infinality]("http://www.infinality.net/blog/")** patches)
5. restart, and you're done.

Please note that I did this on a newly installed system, and zypper dup's didn't damage anything. Make sure you know what zypper dup does before you use it!

Here's a screenshot of original fonts: [here]("http://kozacki.net/images/opensuse/snapshot1.png")
Here are the fonts after using namtrac's stuff: [here]("http://kozacki.net/images/opensuse/snapshot3.png")

Works for me ;)

---

### Post by detook on 2011-05-31
> **antekone said:**
> 
1. do a **zypper dup**, to get your system up-to-date.


Please be careful with **zypper dup. **It will sync your packages with all enabled repositories. That means that there is a risk to downgrade some packages and lost data. In my case YaST died and wl-broadcom driver stopped working:)

So > **antekone said:**
> 
Please note that I did this on a newly installed system, and zypper  dup's didn't damage anything. Make sure you know what zypper dup does  before you use it![LEFT][COLOR=#CCCCCC][FONT=Trebuchet MS][/FONT][/COLOR][/LEFT]

---

### Post by kshep92 on 2011-10-16
Yes this solution worked flawlessly! Look at these beautiful fonts :D Any word on if this rendering engine will be default in 12.1?

---

