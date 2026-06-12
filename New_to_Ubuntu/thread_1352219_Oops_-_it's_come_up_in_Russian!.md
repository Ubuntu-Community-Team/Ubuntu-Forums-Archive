---
title: "Oops - it's come up in Russian!"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by prenoob on 2009-12-11
Hallo All,

Sorry to bother you with what must seem a trivial matter but my inabilty to put it right is causing me some problems with my wife.  I have been fiddling around to make it possible for me to use UK English, German and Russian keyboards and writing and thought I had everything under control.  However, last night I started up and found I had the*** ubuntu*** "home page" as below.

/home/trevor/Pictures/Screenshot-&#1044;&#1086;&#1084;&#1072;&#1096;&#1085;&#1103;&#1103; &#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1072; Ubuntu - Mozilla Firefox.png

As you will see, it is in Russian and I just can't get rid of it.  This doesn't bother me as I can use Russian but it annoys my wife, who also uses the machine.  A Russian edition of Firefox 3.5.2 shows up in the "Languages" Add-Ons but I have disabled it.  Although I have tried, it does not appear to be possible to installer it.

Any help and suggestions would be much appreciated.

Trevor

---

### Post by ukripper on 2009-12-11
in the address bar put this:
```
about:config
```

click on the message.

and then in filter field put "language". Make sure it is set to ```
intl.accept_languages      en-gb
```

---

### Post by Greenwidth on 2009-12-11
Easy to do, UK is Ukranian not United Kingdom.

---

### Post by prenoob on 2009-12-11
> **ukripper said:**
> in the address bar put this:
```
about:config
```click on the message.

and then in filter field put "language". Make sure it is set to ```
intl.accept_languages      en-gb
```[SIZE=2]Not sure which is the "filter field".  The line I get is copied below -

intl.accept_languages;en-gb,de-de,ru

Do I simply delete de-de and ru?  If I do, will the other languages still be accepted in the search box?   

Many thanks for coming to my aid again.

Trevor     [/SIZE]

---

### Post by prenoob on 2009-12-12
> **prenoob said:**
> [SIZE=2]Not sure which is the "filter field".  The line I get is copied below -

intl.accept_languages;en-gb,de-de,ru

Do I simply delete de-de and ru?  If I do, will the other languages still be accepted in the search box?[/SIZE]

[FONT=Verdana][SIZE=2]Well, I did that and the line in about:config nows shows [/SIZE][/FONT]**initl.accept_languages   en-gb **[FONT=Verdana][SIZE=2] only.  However, it has made no difference.  Any ideas?  I was wondering if there is a cache somewhere with this Russian page stored in it?

Trevor
[/SIZE][/FONT]

---

### Post by prenoob on 2009-12-13
> **prenoob said:**
> [FONT=Verdana][SIZE=2]Well, I did that and the line in about:config nows shows [/SIZE][/FONT]**initl.accept_languages   en-gb **[FONT=Verdana][SIZE=2] only.  However, it has made no difference.  Any ideas?  I was wondering if there is a cache somewhere with this Russian page stored in it?

Trevor
[/SIZE][/FONT]
[SIZE=2][FONT=Verdana]Well, I found the answer by trial and error.  Removing the "ubufox" extension seems to have solved the problem "at a stroke".  I subsequently found in Launchpad that nobody seems to know exactly what the extension does!!!!

Thanks to all who tried and I hope this information proves to be helpful to someone else, somewhere, some time.

Trevor
[/FONT][/SIZE]

---

