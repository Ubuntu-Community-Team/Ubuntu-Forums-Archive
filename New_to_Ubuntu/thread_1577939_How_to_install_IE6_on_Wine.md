---
title: "How to install IE6 on Wine?"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by bilbo.san on 2010-09-19
Hello everyone!
I wanted to install IE6 (for web testing purposes) on wine, downloaded it from MS, and it says that I have it installed already. Went into the Wine C disk and found a IEXPLORER file, which opens a one page only, the Wine.org.

Any ideas on how to do this?
Many thanks

---

### Post by adobrakic on 2010-09-19
Have you tried [ies4linux](http://www.tatanka.com.br/ies4linux/page/Main_Page)? Prerequisites are wine & cabextract.

[http://www.tatanka.com.br/ies4linux/download.html](http://www.tatanka.com.br/ies4linux/download.html)


I think the installation of this is simple and self-explanatory, but if you need help don't hesitate to ask.

---

### Post by bilbo.san on 2010-09-19
> **adobrakic said:**
> Have you tried [ies4linux](http://www.tatanka.com.br/ies4linux/page/Main_Page)? Prerequisites are wine & cabextract.

[http://www.tatanka.com.br/ies4linux/download.html](http://www.tatanka.com.br/ies4linux/download.html)


I think the installation of this is simple and self-explanatory, but if you need help don't hesitate to ask.

Thanks!,
I downloaded the file, extracted it... but dont know what to do next. There is no executable file or any guide I could follow to run the program. 
Can you help me?

e.

---

### Post by sandyd on 2010-09-19
```

wget -c  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
chmod 667 winetricks
WINEPREFIX="/home/***username***/.wine-ie6" bash ./winetricks ie6

```note that the instructions above install ie6 seperately from the default WINE installation.

If you find the text too aliased, you can try
```

WINEPREFIX="/home/***username***/.wine-ie6" bash ./winetricks droid fontsmooth-rgb allfonts

```
to install the font smoother, and all the fonts.

---

### Post by bilbo.san on 2010-09-19
> **sandyd said:**
> ```

wget -c  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
chmod 667 winetricks
WINEPREFIX="~/.wine-ie6" ./winetricks ie6

```
note that the instructions above install ie6 seperately from the default WINE installation.

Thanks... tried that and I get an error:
wine: invalid directory ~/.wine-ie6 in WINEPREFIX: not an absolute path
wine: invalid directory ~/.wine-ie6 in WINEPREFIX: not an absolute path
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string

Any help is greatly appreciated!

---

### Post by dirghrabadia on 2010-09-19
Make sure you have Wine installed already. If not, 
```

sudo apt-get install wine 

```Then, carry out the following:
 ```

 wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) 

```

```

 sh winetricks ie6 

```

To run IE:
```

wine iexplore 

```

IE7 didn't work out well for me. Hence IE6. Hope that helps :)

---

### Post by sandyd on 2010-09-19
> **bilbo.san said:**
> Thanks... tried that and I get an error:
wine: invalid directory ~/.wine-ie6 in WINEPREFIX: not an absolute path
wine: invalid directory ~/.wine-ie6 in WINEPREFIX: not an absolute path
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string

Any help is greatly appreciated!
typo.
fixed

---

### Post by bilbo.san on 2010-09-22
Thank you all!!!
I got it working now!.

---

