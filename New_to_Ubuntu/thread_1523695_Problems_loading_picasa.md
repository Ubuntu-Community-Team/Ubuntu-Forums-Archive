---
title: "Problems loading picasa"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Alexd2010 on 2010-07-04
Hi,
 

 I'm brand new to Ubuntu (10.04) & Linux in general and would really appreciate some help with installing Picasa.
 

 I managed to download it OK (even though I was surprised by how tricky that was – what's all this about repositories and keyrings?  I had assumed Ubuntu would be simple and straightforward to use) but it wasn't showing anywhere – I couldn't find it on my computer anywhere (HP mini).  On reading the forums I became aware of the 'main menu' and located it there.
 

 However, when I tried to tick the little box next to it to make appear in the applications menu, nothing happened.  I found that when you tick other applications to make them appear in the menus, the text they are written in goes from italics to bold – italics apparently signifying something like 'programme is on the computer but not in normal use' and bold indicating it will appear in menus.   
 

 Well, picasa would not go bold when I ticked the box and repeatedly failed to appear in any menus (other than main menu).  So I can't find it anywhere on my machine and can't use it.  It doesn't appear anywhere either in the ubuntu software centre so I can't download/install from there.
 

 So, I tried removing it all together (using the package manager) and reinstalling the previously downloaded version located in the 'downloads' folder.  When I try and do this a box appears telling me 'same version is available in a software channel' and 'you are recommended to install the software from the channel instead'.   
 

 But nowhere does it tell you where this 'software channel' may be found, or how to access it, and apparently in ubuntu language the word 'recommended' actually means 'forced' as you are given no option other than to use this 'software channel'.
 

 Can anyone help me?  As I said, I'm a complete beginner so am probably being thick, but would really appreciate some help.  I really like the look (and principles) of ubuntu but if everything is this difficult I will have to go back to MS Windows, which I'd really hate to do!
 

 Any help much appreciated.
 

 Thanks,
 

 Alex

---

### Post by kimikrishna on 2010-07-04
Uninstall any existing picasa. 

And then

Follow the steps in this link : 

[http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html](http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html)

*_After_* installing picasa using the steps in this link, Do this :


Close  picasa  if it is opened.
Then run

```

gksudo nautilus /opt/google/picasa/3.0/wine/drive_c/Program\ Files/Google/Picasa3/runtime/geotag 
```

Rename the "geopanelscript.html" file to "geopanelscript.abc" 

The places button (in picasa) won't work.

And then start picasa 3.6 from App > Graphics 


Thanks to the webupd8.org  
and swiniak who posted a comment on the page to solve the "places" problem.

---

### Post by Garthhh on 2010-07-04
> **Alexd2010 said:**
> Hi,
 

 I'm brand new to Ubuntu (10.04) & Linux in general and would really appreciate some help with installing Picasa.
 

 I managed to download it OK (even though I was surprised by how tricky that was – what's all this about repositories and keyrings?  I had assumed Ubuntu would be simple and straightforward to use) but it wasn't showing anywhere – I couldn't find it on my computer anywhere (HP mini).  On reading the forums I became aware of the 'main menu' and located it there.
 

 However, when I tried to tick the little box next to it to make appear in the applications menu, nothing happened.  I found that when you tick other applications to make them appear in the menus, the text they are written in goes from italics to bold – italics apparently signifying something like 'programme is on the computer but not in normal use' and bold indicating it will appear in menus.   
 

 Well, picasa would not go bold when I ticked the box and repeatedly failed to appear in any menus (other than main menu).  So I can't find it anywhere on my machine and can't use it.  It doesn't appear anywhere either in the ubuntu software centre so I can't download/install from there.
 

 So, I tried removing it all together (using the package manager) and reinstalling the previously downloaded version located in the 'downloads' folder.  When I try and do this a box appears telling me 'same version is available in a software channel' and 'you are recommended to install the software from the channel instead'.   
 

 But nowhere does it tell you where this 'software channel' may be found, or how to access it, and apparently in ubuntu language the word 'recommended' actually means 'forced' as you are given no option other than to use this 'software channel'.
 

 Can anyone help me?  As I said, I'm a complete beginner so am probably being thick, but would really appreciate some help.  I really like the look (and principles) of ubuntu but if everything is this difficult I will have to go back to MS Windows, which I'd really hate to do!
 

 Any help much appreciated.
 

 Thanks,
 

 Alex
Uninstall picasa & go to the Synaptic package manager, which you will find under system
installing in this way will generally also install the other programs/applications/libraries/dependencies for some thing like picasa to work properly

when looking for new application, you can also try the software manager, which you can also find under system

It's always much easier to install this way than directly off the internet.

---

### Post by Yvan300 on 2010-07-04
You do know that they offer a deb on their website......right? If you want updates and stuff, then you should install the repos. But since google seems to neglect linux a bit, those update won't be coming around this time . So hey, just download the deb and enjoy! It's like a .exe file for windows.

---

### Post by Garthhh on 2010-07-04
> **Yvan300 said:**
> You do know that they offer a deb on their website......right? If you want updates and stuff, then you should install the repos. But since google seems to neglect linux a bit, those update won't be coming around this time . So hey, just download the deb and enjoy! It's like a .exe file for windows.

the problem is it doesn't actually work as delivered from their website [google earth either]
the synaptic versions may not be the latest & the greatest, but they do work, you can update once working versions are on board

---

### Post by kimikrishna on 2010-07-04
> **Yvan300 said:**
> You do know that they offer a deb on their website......right? If you want updates and stuff, then you should install the repos. But since google seems to neglect linux a bit, those update won't be coming around this time . So hey, just download the deb and enjoy! It's like a .exe file for windows.


It's still an .exe packed in a .deb. :(


And that is an old version 3.0


@Alexd2010

If you want latest picasa (3.6), use my post above.

---

### Post by oldfred on 2010-07-04
I generally agree to install from the repros as those will work. But I was able to download and install 3.6 into wine.

From my history:
                                         114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
    [LEFT]  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)[/LEFT]
    [LEFT]  116  sudo chmod 777 winetricks[/LEFT]
    [LEFT]  117  sudo apt-get install cabextract wine wine-gecko[/LEFT]
    [LEFT]  118  winetricks allfonts fontsmooth-rgb gecko allfonts[/LEFT]
    [LEFT]Then download picasa for windows
 ([http://dl.google.com/picasa/picasa36-setup.exe]("http://dl.google.com/picasa/picasa35-setup.exe"))
 [/LEFT]
    [LEFT]move to wine programs[/LEFT]
    [LEFT]run it, and the installer should start.[/LEFT]
    [LEFT][/LEFT]
    [LEFT][/LEFT]

---

### Post by Alexd2010 on 2010-07-05
[kimikrishna]("http://ubuntuforums.org/member.php?u=737076"), many thanks for your help - couldn't get up to 3.6 for some reason but picasa 3.0 seems to work fine - so thanks very much to you and for the suggestions of everyone else - for a 'newbie' like me it's very reassuring to know there is so much expertise available out there!

Cheers,
Alex

---

### Post by alfh on 2010-07-30
Following this guide at [www.webupd8.org]("http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html") I succesfully installed Picasa 3.

Didn't try the 3.6 part

---

