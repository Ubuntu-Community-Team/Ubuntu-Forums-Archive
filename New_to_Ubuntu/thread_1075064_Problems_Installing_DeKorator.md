---
title: "Problems Installing DeKorator"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by mpl34 on 2009-02-19
Hi

I have really been wanting to change my default theme for kubuntu as I find the pre-installed themes very ugly.

From what i can tell DeKorator is the piece of software I require. I basically wish to change the look of the windows and the minimize, maximize and close buttons.

I have installed the deb package for DeKorator and have also downloaded the source file but am unsure how to install the source file (thats why I ised the deb)

However when i go into my appearance-system settings --> windows, I then select DeKorator as my Window Decoration but only get the message 
> No Preview available
Most probably there
was a problem loading the plugin
here is a link to the kde-look page where I found DeKorator, [link]("http://www.kde-look.org/content/show.php/deKorator?content=87921")

The second screen shot is similar to what I am looking for, any help would be much appreciated.

---

### Post by abn91c on 2009-02-19
**Adept** has a dekorator for kde, I just installed it and it works OK, in the Themes tab scroll down to the bottom then click "install new themes", go to the folder you downloaded the themes and select from there, then you have to click on the "set theme path" to activate the theme then click "apply"

---

### Post by mpl34 on 2009-02-19
I am unable to find any window decorators in adept except for emerald which requires compiz-fusion.

---

### Post by abn91c on 2009-02-20
see attached
ordo ```
sudo apt-get install kwin-style-dekorator
```

---

### Post by sdaf on 2009-03-03
I install the kwin-style-dekorator package, but I cannot find anything at the window decoration tab (system setting->appearance->windows).
How exactly is it used?
Thanks :)

---

### Post by ruik on 2009-03-13
I'd like to know it too :P

---

### Post by abn91c on 2009-03-13
click on the windows decoration tab, select dekorator from the pulldowm menu, then follow post #2 above

---

### Post by ruik on 2009-03-13
Heh, yeah, thanks. I actually managed to find it right after posting the reply. :)

---

### Post by scroorage on 2009-03-16
I installed kwin-style-dekorator, but even after reboot I am still unable to find deKorator in the pull down menu of the window decoration tab.

I am using kde 4.2

Could someone help me please?

---

### Post by Armin_Fan on 2009-03-23
scroorage, ever get your answer? I have the same problem. dekorator never shows up in windows decoration list after installing it from adept. maybe it needs to be compiled. kde-look has various versions.

---

### Post by scroorage on 2009-03-23
Hi Armin_Fan, actually I did today. I have downloaded the fedora rpm package of dekorator.

[http://www.kde-look.org/content/show.php/deKorator?content=87921]("http://www.kde-look.org/content/show.php/deKorator?content=87921")

Then I have installed alien - which can be used to transform rpm to deb package
```
sudo apt-get install alien
```

then transform rpm package to deb package using this command:
```
sudo alien kde4-windeco-dekorator-0.3-11.1.i386.rpm
```


Now you can install dekorator from newly created kde4-windeco-dekorator-0.3-11.1.i386.deb package.

But after applying dekorator theme I still have a little gap between maximizing and closing buttons. Please let me know if you have the same problem? Maybe I should compile the source- but I am not really sure how to do it properly??? :(

---

### Post by Armin_Fan on 2009-03-23
wow, converting of the rpm to deb using alien, allows dekorator to be an opton in windows decorations. now I have the problem of the decorations dissappearing totally (no max or min buttons) as i select dekorator. I read somewhere there is a fix for that. Before using your method, I tried deb made by someone on that link u posted, person posted it in the comments, but when i ran it, it didnt work properly (i believe the dekorator was 1.3-4.1, but it doesnt work, your method does.)

---

### Post by Armin_Fan on 2009-03-23
the fix for no window decoration buttons showing is explained here: [http://ubuntuforums.org/showthread.php?t=132069&highlight=dekorator](http://ubuntuforums.org/showthread.php?t=132069&highlight=dekorator)

namely Jucato response:

When you install new deKorator themes thru the "Themes" tab, make sure to click "Set Theme Path's" at the bottom so that it will automatically adjust the paths.

---

