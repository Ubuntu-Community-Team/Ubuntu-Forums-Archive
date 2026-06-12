---
title: "Kid Was influenced into ubuntu"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by HamzahQaisar on 2009-10-12
OK so i downloaded ubuntu and mounted it onto ma usb stick i absolutly love ubu but im gettin stuck alot can someone help me install this theme
[http://gnome-look.org/content/show.php?content=86048&forumpage=4](http://gnome-look.org/content/show.php?content=86048&forumpage=4)
even though im 14 can i just get the terminal code to install it
thanks in adavnce

add me on [EMAIL="the-parrot@hotmail.com"]the-parrot@hotmail.com[/EMAIL]

---

### Post by MelDJ on 2009-10-12
open up system-preferences-appearance. under the theme tab, press install and then select the file you downloaded. no need to extract it

---

### Post by coldReactive on 2009-10-12
> **MelDJ said:**
> open up system-preferences-appearance. under the theme tab, press install and then select the file you downloaded. no need to extract it

Or simply drag the tar.gz/bz2 into the themes list there.

---

### Post by HamzahQaisar on 2009-10-12
ive tried all these things already ive extratced and deag n install and a error comes up
saying it is not valid and cannot be installed well all i kno is that its gtx i totaly love this theme if someone help me out ill be estatic obver the moon

---

### Post by MelDJ on 2009-10-12
you don't have to extract it. just drag or install the tar file. 
and please don't type in short form, it's quite hard to decipher what you are saying ;)

---

### Post by coldReactive on 2009-10-12
Oh for pete's sake, the guy made it so you have to install it all manually. See attached file for the base files of the theme.

*gives you all a cookie so you have something to eat while you wait for someone to tell you how to install themes manually.*

---

### Post by HamzahQaisar on 2009-10-12
im sorry about the short form
it stills says the samething even if i dont extract it ...
can someone please install it and tell me how they installed it?
please

---

### Post by mcduck on 2009-10-12
I downloaded the package, and it seems that the theme's creator has made annoying little mistake when creating the package..

Anyway, first try renaming the package from "Raptor_by_Ardenarbroriger**.gz**" to "Raprot_by_Ardenarbrodiger**.tar.gz**", and then installing as suggested above.

If it still doesn't work, extract the package manually into ~/.themes (a hidden directory inside your home directory, if it doesn't exist yet then just create it). The extracting should work fine after the file has been renamed to correct name.

---

### Post by MelDJ on 2009-10-12
this link may help you out: [http://www.techzilo.com/how-to-install-ubuntu-linux-themes-skins/](http://www.techzilo.com/how-to-install-ubuntu-linux-themes-skins/)

---

### Post by HamzahQaisar on 2009-10-12
> **mcduck said:**
> I downloaded the package, and it seems that the theme's creator has made annoying little mistake when creating the package..

Anyway, first try renaming the package from "Raptor_by_Ardenarbroriger**.gz**" to "Raprot_by_Ardenarbrodiger**.tar.gz**", and then installing as suggested above.

If it still doesn't work, extract the package manually into ~/.themes (a hidden directory inside your home directory, if it doesn't exist yet then just create it). The extracting should work fine after the file has been renamed to correct name.


thanks man ill brb with the news

---

### Post by sigurnjak on 2009-10-12
Hi there ! I just downloaded your theme , and yes it is little different . 
It is a compressed file with whole bunch of stuff in it . 
Right click it and choose extract , then repeat it again on newly extracted file until you get folder . 
Then i created new folder on the desktop and named it Raptor . 
When done open Raptor v9.7.1 Elegant Predator  and copy gtk and metacity folder in raptor folder . 
Then right click raptor and choose create archive . 
When done open appearance and drag it in and apply theme . 
It worked for me like a charm . One thing i did was , moved raptor folde somewhere  for keeping and then added wallpaper . 

ENJOY  RAPTOR !

---

### Post by HamzahQaisar on 2009-10-12
problem no.2

it says this

"This theme will not look as intended because the required GTK+ theme "raptor" is not installed"

soo how do i fix this?

---

### Post by HamzahQaisar on 2009-10-12
Thanks man

but how do i get that amazing bar at the bottom of the desktop like in mac if you see the pic on the link i gave u..

soo how do i get that?

this is how i want to make my desktop look

[http://gnome-look.org/content/preview.php?preview=1&id=86048&file1=86048-1.jpg&file2=86048-2.jpg&file3=86048-3.jpg&name=Raptor+(Slickness+remix](http://gnome-look.org/content/preview.php?preview=1&id=86048&file1=86048-1.jpg&file2=86048-2.jpg&file3=86048-3.jpg&name=Raptor+(Slickness+remix))

---

### Post by mcduck on 2009-10-12
> **HamzahQaisar said:**
> problem no.2

it says this

"This theme will not look as intended because the required GTK+ theme "raptor" is not installed"

soo how do i fix this?

Seems that the theme package has some extra annoyances as well.. Seems that the best solution is to just do what sigurnjak suggested (or instead of creating a new package from the gtk-2.0 and metacity directories you can also move the new "Raptor" directory into ~/.themes without compressing it). This helps to get rid of the extra theme definition files in the packages which assume that you have several extra themes installed on your system.

What comes to the dock visible in screenshots, that would be some additional program. Cairo-Dock or AWN, perhaps.

---

### Post by HamzahQaisar on 2009-10-12
so how do i download these dock softwares?

---

### Post by mcduck on 2009-10-12
From Ubuntu's repositories, using your which ever package management tool you prefer..

[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by HamzahQaisar on 2009-10-12
i cant find any dock applications on add/remove :(

---

### Post by coldReactive on 2009-10-12
> **HamzahQaisar said:**
> i cant find any dock applications on add/remove :(

Make sure All available applications is selected from the drop down on add/remove, it defaults to canonical maintained, etc. instead when you first use it.

search for awn, cairo, gnome do.

---

### Post by fabounet on 2009-10-13
for Cairo-Dock you can find the way here (the version in the Ubuntu repository is way too old) :
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

---

