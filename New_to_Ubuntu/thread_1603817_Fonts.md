---
title: "Fonts"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by SEECo on 2010-10-23
Can any one tell me to how to get segoe ui font for ubuntu

---

### Post by cchhrriiss121212 on 2010-10-23
First you would have to pay for it as it is a proprietary font owned by Microsoft. Once you have done that you can just place it in your ~/.fonts folder.

If you want some free fonts then look here:
[http://www.dafont.com/](http://www.dafont.com/)

---

### Post by ivarn on 2010-10-23
The location is /home/user/.fonts.
This folder is not created by default, so create the folder.
Idk what font formats it will recognize but at least ttf will work.
Edit: here's the ting.
There are various locations in Linux in which fonts can be kept. These locations are defined in /etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and /home/<username>/.fonts (where <username> is your user name).

---

### Post by SEECo on 2010-10-23
Isn't there any location from where i can free download it.

---

### Post by lotharmat on 2010-10-23
You could look at a windows installation and get it from there..

---

### Post by SEECo on 2010-10-23
Does it will include .ttf file in it

---

### Post by lotharmat on 2010-10-23
It should do!

---

### Post by CharlesA on 2010-10-23
lotharmat: I've removed the download link

You can purchase the font [here]("http://www.ascendercorp.com/font/segoe-ui/").

Also see [here]("http://www.linuxquestions.org/questions/linux-general-1/segoe-ui-font-alternates-for-linux-536010/") for some alternatives.

---

### Post by Verbeck on 2010-10-23
i think you'll need to refresh font cache after copying over a new font
[B]fc-cache -f -v
[/B]

---

### Post by SEECo on 2010-10-23
Does xp uses segoe ui

---

### Post by CharlesA on 2010-10-23
Only if you install Windows Live.

---

### Post by SEECo on 2010-10-25
> **CharlesA said:**
> Only if you install Windows Live.
 
I have xp and live installed on it so tell me the location where i can found the font in xp

---

### Post by Verbeck on 2010-10-25
> **SEECo said:**
> I have xp and live installed on it so tell me the location where i can found the font in xp

control panel (classic view) > Fonts

*i think :|

---

### Post by SEECo on 2010-10-26
Yes, i have got the font file where to drop it.

---

### Post by Verbeck on 2010-10-26
> **SEECo said:**
> Yes, i have got the font file where to drop it.


There are various locations in GNU/Linux in which fonts can be kept. These locations are defined in /etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and /home/<username>/.fonts (where <username> is your user name). 
The  easiest way to install a truetype font is to press alt-F2 and enter the  following code (this will open nautilus in the right directory): 

```
gksu nautilus /usr/share/fonts/truetype
```Then  create a new directory, name the directory whatever you like (choose a  name that you remember if you ever need to backup your fonts personal  fonts). Copy the fonts into that directory and finally rebuild the font  information files by pressing alt-F2, mark 'run in terminal' so you can  see the progress and entering the following code: 
```
sudo fc-cache -f -v
```
from:
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by SEECo on 2010-10-27
Thnks for that you the man and one and only

---

