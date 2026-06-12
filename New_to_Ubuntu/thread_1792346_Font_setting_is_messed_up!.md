---
title: "Font setting is messed up!"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by maqtanim on 2011-06-28
I am a GNOME guy! I've been using Ubuntu for more than 2 years and actually never used Kubuntu before! So I've no clear idea about KDE or Kubuntu.

Two days ago I installed Kubuntu 11.04 in my new desktop. Everything was going perfectly. A few hours ago I Installed 3 softwares (Kget, Q4wine, Arista) and then my fonts became ugly! The whole desktop and all the application is showing dotted ugly fonts. I am not sure whether these softwares caused the problem.

I tried to fix it from System Settings > Application Appearance > Fonts, but with no luck. I've attached 3 screenshot of my desktop. First one shows my current font setting, And the second one shows my current 'messed up fonts' in my computer. The third one shows the dotted fonts more clearly.

Any suggestion to overcome this problem?

---

### Post by nomko on 2011-06-28
Hallo stadsgenoot!
 
What's the content of your font.conf? Did you made any changes in that file? Installed some new fonts?

---

### Post by maqtanim on 2011-06-28
> **nomko said:**
> Hallo stadsgenoot!
 
What's the content of your font.conf? Did you made any changes in that file? Installed some new fonts?
Hallo stadsgenoot! Goedemorgen!! :)

Yes I've installed some fonts which are available to [Google Webfonts]("http://www.google.com/webfonts").

My font.conf content is as follows:
```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font">
  <edit mode="assign" name="rgba">
   <const>rgb</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hinting">
   <bool>true</bool>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hintstyle">
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>
 <match target="font">
  <test compare="more_eq" name="size" qual="any">
   <double>8</double>
  </test>
  <test compare="less_eq" name="size" qual="any">
   <double>15</double>
  </test>
  <edit mode="assign" name="antialias">
   <bool>false</bool>
  </edit>
 </match>
 <match target="font">
  <test compare="more_eq" name="pixelsize" qual="any">
   <double>11</double>
  </test>
  <test compare="less_eq" name="pixelsize" qual="any">
   <double>20</double>
  </test>
  <edit mode="assign" name="antialias">
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>

```

---

### Post by nomko on 2011-06-28
Which version of libcairo you have installed? Maybe you need an update on that file.

---

### Post by maqtanim on 2011-06-28
> **nomko said:**
> Which version of libcairo you have installed? Maybe you need an update on that file.
cairo 1.10.2 is installed ... this one is the latest so far!

BTW... having no other way, I deleted the *font.conf* and everything is working fine now.

---

### Post by nomko on 2011-06-28
> **maqtanim said:**
> cairo 1.10.2 is installed ... this one is the latest so far!

BTW... having no other way, I deleted the *font.conf* and everything is working fine now.

i thought so it was the font.conf.

---

### Post by specospec on 2011-11-25
i faced the same problem, after installing kde in my 10.04 box, i lost the subpixel smoothing, 
i fixed this problem by editing .fonts.conf in home directory,
the values of all fields with anti aliasing were changed to true, and voila :guitar:

---

