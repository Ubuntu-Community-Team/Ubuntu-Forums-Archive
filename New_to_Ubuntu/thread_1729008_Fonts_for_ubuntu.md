---
title: "Fonts for ubuntu"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by abnordude on 2011-04-14
I need to download fonts for my ubuntu.
I had used ubuntu studio recently.
I kind of liked its variety of fonts.
How can i get the same fonts and more in ubuntu.?

---

### Post by Enigmapond on 2011-04-14
Download the font(s) you want to install. Create a folder in your home directory named .fonts (with a "." at the beginning as it's hidden). Put all the fonts in there and simply run, in the terminal:

```
sudo fc-cache -f -v
```

This will install the font(s) system-wide.

---

### Post by abnordude on 2011-04-14
> **Enigmapond said:**
> Download the font(s) you want to install. Create a folder in your home directory named .fonts (with a "." at the beginning as it's hidden). Put all the fonts in there and simply run, in the terminal:

```
sudo fc-cache -f -v
```This will install the font(s) system-wide.


yes but from where do i download the fonts from is what i'm asking.

---

### Post by Enigmapond on 2011-04-14
What fonts in particular? Ubuntu Family fonts?

---

### Post by Enigmapond on 2011-04-14
Ubuntu Studio fonts?...there is an easier way...scroll to the bottom of this page [http://packages.ubuntu.com/lucid/ubuntustudio-font-meta](http://packages.ubuntu.com/lucid/ubuntustudio-font-meta)

and download the deb for you architecture, double click and they will install...

---

### Post by ~Plue on 2011-04-14
> **Enigmapond said:**
> sudo fc-cache -f -v
iinm, if you run fc-cache with sudo, it'll update the root user's font cache..

actually, as outlined in [this post]("http://ubuntuforums.org/showpost.php?p=10648327&postcount=13"), you wouldn't need to run it if you're copying them to your home directory. as fonts copied to the .fonts folder are picked up by applications once they are restarted. its only needed if you're copying to the system wide directory

and wouldn't one need to copy the font to /usr/share/fonts/ to make it available system wide?

---

### Post by Enigmapond on 2011-04-14
> **~Plue said:**
> iinm, if you run fc-cache with sudo, it'll update the root users font cache..

actually, as outlined in [this post]("http://ubuntuforums.org/showpost.php?p=10648327&postcount=13"), you wouldn't need to run it if you're copying them to your home directory. as fonts copied to the .fonts folder are picked up by applications once they are restarted

Well sorry to disagree...but I have downloaded hundreds of fonts. I use them professionally, GIMP and other apps won't pick them up until I update the font cache. This is the way it's been for years now.. I do it quite a lot.

---

### Post by coffeecat on 2011-04-14
> **~Plue said:**
> iinm, if you run fc-cache with sudo, it'll update the root user's font cache..

actually, as outlined in [this post]("http://ubuntuforums.org/showpost.php?p=10648327&postcount=13"), you wouldn't need to run it if you're copying them to your home directory. as fonts copied to the .fonts folder are picked up by applications once they are restarted. its only needed if you're copying to the system wide directory

and wouldn't one need to copy the font to /usr/share/fonts/ to make it available system wide?

> **Enigmapond said:**
> Well sorry to disagree...but I have downloaded hundreds of fonts. I use them professionally, GIMP and other apps won't pick them up until I update the font cache. This is the way it's been for years now.. I do it quite a lot.

Well - as the person who posted the post that ~Plue linked I have to disagree with your disagreement. But being a practical person I also believe in the scientific method. I have just opened my ~/.fonts folder and dragged a ttf font file into it that I have never used in this system before. I did not run fc-cache; I did not restart the xserver; I did not log out and in again.

When I opened the Gimp, there the font was, ready to use and I used it. Ditto Libre Office. This is in Natty.

---

### Post by coffeecat on 2011-04-14
> **coffeecat said:**
>  This is in Natty.

Lucid as well. Drag a ttf font into ~/.fonts and it is immediately available in Open Office and Gimp. I'm sure Maverick is the same.

---

### Post by Nickjpost on 2011-04-14
> **coffeecat said:**
> Lucid as well. Drag a ttf font into ~/.fonts and it is immediately available in Open Office and Gimp. I'm sure Maverick is the same.
I tried coffeecat's suggestion so I could have more fonts as well.....
 
It worked exactly as he stated.
 
I'm running Maverik

---

### Post by grahammechanical on 2011-04-14
I copy and paste the font into my home folder. I right click and select Open with Font Viewer. Then I click Install Font. This work has worked for me in 10.10 and in 11.04 beta.

Regards.

---

### Post by Wolligog on 2011-04-14
[LEFT]right click on .tff file >open with font viewer>install


then drag and drop the tff into your fonts folder
[/LEFT]

---

### Post by jpc2769 on 2011-04-15
I am having a hell of a time trying to install fonts in 10.10, I downloaded the .ttf files, copied them into my .fonts folder, also in /usr/share/fonts, double clicked the files to install, restarted Ubuntu, updated the cache as described above, but the fonts are still not available in OpenOffice. Any suggestions?

Regards, 
Jason

---

### Post by jpc2769 on 2011-04-15
Actually it turned out to be a problem with the files, I was able to fix it by getting new files.

Regards,
Jason

---

