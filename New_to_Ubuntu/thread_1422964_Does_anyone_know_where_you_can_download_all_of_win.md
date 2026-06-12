---
title: "Does anyone know where you can download all of windows fonts"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Fläsh on 2010-03-06
Hello Ubuntu Once Again,

After installing wine ive had a problem with fonts windows comes with 200 fonts but i have no idea on how to get all of these fonts. Also another question does winetricks corefonts come with every 200 fonts that come stocked with windows ?

Thank you for your time,
-Flash

---

### Post by HermanAB on 2010-03-06
The Red Hat Freedom Fonts are designed to be identical to the common Windows fonts.

---

### Post by oldfred on 2010-03-06
When I installed picasa I ran these commands which included fonts. (list from my history)

                                       [LEFT]  [SIZE=1]114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/SIZE][/LEFT]
    [LEFT][SIZE=1]  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/SIZE][/LEFT]
    [LEFT][SIZE=1]  116  sudo chmod 777 winetricks[/SIZE][/LEFT]
    [LEFT][SIZE=1]  117  sudo apt-get install cabextract wine wine-gecko[/SIZE][/LEFT]
    [LEFT][SIZE=1]  118  winetricks allfonts fontsmooth-rgb gecko allfonts[/SIZE][/LEFT]
    [LEFT][SIZE=1]Then download picasa for windows
 ([http://dl.google.com/picasa/picasa36-setup.exe]("http://dl.google.com/picasa/picasa35-setup.exe"))
 run it, and the installer should start.[/SIZE][/LEFT]
    [LEFT][SIZE=1]rename to picasa and move to wine programs[/SIZE][/LEFT]
    [LEFT][/LEFT]

---

### Post by 73ckn797 on 2010-03-06
Have you tried this:
[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

---

### Post by Bachstelze on 2010-03-06
> **Fläsh said:**
>  Also another question does winetricks corefonts come with every 200 fonts that come stocked with windows ?

No. Most of those fonts are proprietary, so it would be illegal to redistribute them. corefonts will give you Arial, Times New Roman, Courier New, Trebuchet MS and a few others that are free to redistribute.

---

### Post by abcuser on 2010-03-07
In Application | Ubuntu Software Center search box write:
microsoft core fonts
and Microsoft Core Fonts package will be displayed.

This are core fonts, not all of them, but some of them.

---

