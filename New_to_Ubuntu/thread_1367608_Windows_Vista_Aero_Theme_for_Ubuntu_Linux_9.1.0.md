---
title: "Windows Vista Aero Theme for Ubuntu Linux 9.1.0?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by lollard on 2009-12-29
Could someone please tell me how to install a pure Windows Vista Aero theme that looks like the real thing on Ubuntu Linux 9.1.0? I'm a bit a of a newbie at running scripts on Ubuntu, so detailed instructions are much appreciated.

---

### Post by nerdy_kid on 2009-12-29
first thing google turned up: [http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html](http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html)

---

### Post by lollard on 2009-12-29
Yes, I did google the problem. I did read the site which you linked, and I tried to do what it said. I was not able to understand the site, as the directions weren't very clear to me. One of the downloads was not working. I have spent some time googling the issue and I was not able to come up with a way to install the theme, which is why I posted on the forums asking for help.

---

### Post by tom.swartz07 on 2009-12-29
> **lollard said:**
> Yes, I did google the problem. I did read the site which you linked, and I tried to do what it said. I was not able to understand the site, as the directions weren't very clear to me. One of the downloads was not working. I have spent some time googling the issue and I was not able to come up with a way to install the theme, which is why I posted on the forums asking for help.

Sorry to hear that. Since this is a "Beginners" thread, many times posters assume that the Original Poster doesnt know what to search for or how to go about doing something.

Lets break this down into manageable parts.
That thread on UbuntuGeek is fairly complete, save for the problem you said you experienced. 
What download wasnt working? Perhaps I could help by finding an alternative to that link.

Let me know, and Ill help walk you through it.

---

### Post by thatguruguy on 2009-12-29
Let's pretend for a second that you don't come across as angry when people are trying to help you.

What, exactly, are you having an issue with w/r/t the instructions given?  Which download site didn't work for you?

Maybe give some more detail in your description of your issues, and you can get more detailed answers.

---

### Post by ankspo71 on 2009-12-30
Hi,
Visit gnome-look.org and download any one of the many gtk2 themes that look like vista.
You can search that site for "aero", "vista", and "win7", and you are sure to find some vista themes to your liking.

Once you have downloaded the gtk2 theme, extract the contents to your /home/lollard/.themes folder . Replace lollard with your actual username for ubuntu. The dot in the folder name means it will be a hidden folder. Once you do that you can select the theme in your "Appearance" preferences in your System - Preferences menu. Just remember that you might have to click on the customise button to select the "control" and "window border", as not all themes have a preview image to select from in the themes window. The theme preview window also supports drag and drop installation, but it doesn't always work considering not all packages are packed the same way. 

Next, I recommend downloading and installing [gnomenu_2.2.2-1~ppa1_all.deb]("https://launchpad.net/%7Egnomenu-team/+archive/ppa/+files/gnomenu_2.2.2-1%7Eppa1_all.deb") from here [https://launchpad.net/~gnomenu-team/+archive/ppa/+packages]("https://launchpad.net/%7Egnomenu-team/+archive/ppa/+packages") . Install that to give you a Vista like start menu and start button. You can find round vista images for the start button by surfing the web, or even back at gnome-look.org  

Next up is dockbarx to give you the panel-dock like buttons on your panel. [http://www.androidtux.co.cc/posts/dockbarx-deb-rpm-packages-with-extra-themes/](http://www.androidtux.co.cc/posts/dockbarx-deb-rpm-packages-with-extra-themes/)
download the deb file and install it.

Now log out and log back in. (This is needed for installing most applets so they can be loaded into the gnome panel) Anyways, after doing that, start dockbarx and gnomenu by right clicking on any open/unused area of your panel and select "add to panel" Select gnomenu and dockbarx. 

If you need widgets for your desktop, you can search for and install screenlets and gdesklets in Synaptic Package Manager.


This should get you started. 
Hope it helps.
PS. You might like this link... [http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093) 
It's outdated from 2006 though.

---

### Post by wirate on 2009-12-30
In addition to the post above.

to get those transparent window borders, open a terminal and type

```
sudo apt-get install emerald
```

visit [this]("http://gnome-look.org/index.php?xcontentmode=103") and download some theme which says windows 7/vista/aero etc.

then goto system>preferences or administration (i dont remember) and click emerald. Now install the .emerald theme you downloaded and apply it.

Finally press alt+F2 and type

```
emerald --replace
```

in the dialog box.

hope you have pretty window borders now

---

### Post by nerdy_kid on 2010-01-01
> Yes, I did google the problem. I did read the site which you linked, and I tried to do what it said. I was not able to understand the site, as the directions weren't very clear to me. One of the downloads was not working. I have spent some time googling the issue and I was not able to come up with a way to install the theme, which is why I posted on the forums asking for help.

sorry, i sometimes do what tom.swartz07 said and assume that people dont google before posting; i apologize for that.  I can help you more if you still need it, as I had all the fancy GNOME prettiness going before i switched to KDE.  I had people drooling over all the compiz effects i had spent hours tweaking :lolflag:

---

### Post by Felix-the-Cat on 2010-04-20
check out this: [[URL="http://code.google.com/p/gnome-vista-aero-theme-automated/"]http://code.google.com/p/gnome-vista-aero-theme-automated/]("http://code.google.com/p/gnome-vista-aero-theme-automated/")[/URL]

---

### Post by anewguy on 2010-04-20
> **wirate said:**
> In addition to the post above.

to get those transparent window borders, open a terminal and type

```
sudo apt-get install emerald
```

visit [this]("http://gnome-look.org/index.php?xcontentmode=103") and download some theme which says windows 7/vista/aero etc.

then goto system>preferences or administration (i dont remember) and click emerald. Now install the .emerald theme you downloaded and apply it.

Finally press alt+F2 and type

```
emerald --replace
```

in the dialog box.

hope you have pretty window borders now

I think that it would be compiz, not emerald with the later releases of ubuntu.  After installing compiz (it should actually be installed by default), go to synaptic package manager and install compizconfig-settings-manager, then look for it under system/preferences.  There are a TON of things to set there, including things that are very similar in appearance to what you want.

Dave ;)

---

