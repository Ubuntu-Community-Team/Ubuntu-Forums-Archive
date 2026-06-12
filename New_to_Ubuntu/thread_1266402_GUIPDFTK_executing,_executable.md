---
title: "GUIPDFTK: executing, executable???"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by B9 hummingbird hovering on 2009-09-14
At this site:
[http://www.paehl.de/pdf/gui_pdftk.html]("http://www.paehl.de/pdf/gui_pdftk.html")
I downloaded the guipdftk.tar.gz and extracted from it the
'guipdftk' which is an executable and the plain text document 'guipdftk.config' which only has the text in it "usr/bin". I tried to copy and paste the executable there but it wouldn't let me.  I would really appreciate assistance. I have installed the pdftk and it is enabled on my commandline in terminal as well but I can't figure out how to work it from the instructions.
:confused:

---

### Post by KIAaze on 2009-09-15
**_Command-line:_**
pdftk is not that hard to use by command-line.
Just look at the examples here:
[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

_**guipdftk:**_
However, I managed to compile, run and use the guipdftk.
First of all, install lazarus and pdftk:
```
sudo apt-get install lazarus pdftk
```

The source code had some errors in it, and the text on the buttons wasn't very readable, so I made a few modifications.
I attached the fixed source code.
Download and extract it.
Then launch lazarus and open the "project1.lpi" project file through:
"Project->Open project...".
Then build through "Run->Build all".

That's it, you should now be able to run guipdftk with:
```
./guipdftk
```
:)

The guipdftk.config file tells guipdftk where pdftk is installed (default: /usr/bin) and should always be in the directory you run guipdftk from!

Note: If you don't trust me, you can of course also download the original source code from [http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html)
Just make sure you put guipdftk.config into the same directory.
Join and merge don't work correctly however. That's what I fixed. ;)
You might also need to change the compiler options: "Project->Compiler options...->Code->Target processor->Default".


_**Konqueror/Dolphin integration:**_
Just save the following file in the given directory. You should then have access to pdftk through the context menu in Konqueror and Dolphin (KDE4).

~/.kde/share/kde4/services/ServiceMenus/pdftk.desktop
```
# Author: Mikolaj Machowski ( mikmach AT wp DOT pl )               
# Licence: GPL                                                     
#                                                                  
# vim:tw=1000                                                      
# Adapted for KDE4 by KIAaze                                        

[Desktop Entry]
Type=Service   
ServiceTypes=KonqPopupMenu/Plugin,application/pdf
Actions=testmulti;burstpdf;mergepdf;_SEPARATOR_;encryptpdf;encryptpdfprint;decryptpdf;infopdf
X-KDE-Submenu = PDF Toolkit                                                                  
X-KDE-Submenu[pl] = Narz&#281;dzia PDF                                                            

[Desktop Action burstpdf]
Name=Burst PDF           
Name[pl]=Rozsyp plik     
Icon=                    
Exec=cd "%d";pdftk %u burst;cd -

[Desktop Action mergepdf]
Name=Merge files...      
Name[pl]=Po&#322;&#261;cz pliki... 
Icon=                    
Exec=pdftk %U cat output `kdialog --getsavefilename "out.pdf"`

[Desktop Action encryptpdf]
Name=Encrypt PDF...
Name[pl]=Zaszyfruj PDF...
Icon=
Exec=pdftk %u output `kdialog --getsavefilename "%u" ""` owner_pw `kdialog --password "Enter owner password:"`

[Desktop Action encryptpdfprint]
Name=Encrypt PDF, Allow Print...
Name[pl]=Zaszyfruj PDF, mo&#380;na drukowa&#263;...
Icon=
Exec=pdftk %u output `kdialog --getsavefilename "%u" ""` owner_pw `kdialog --password "Enter owner password:"` allow printing

[Desktop Action decryptpdf]
Name=Decrypt PDF...
Name[pl]=Odszyfruj PDF...
Icon=
Exec=pdftk %u input_pw `kdialog --password "Enter owner password:"` output `kdialog --getsavefilename "%u" ""`

[Desktop Action infopdf]
Name=Properties
Name[pl]=W&#322;a&#347;ciwo&#347;ci
Icon=info
Exec=kdialog --msgbox "`pdftk %u dump_data`"

```

Adapted for KDE4 from: [http://www.accesspdf.com/pdftk/#service_menus](http://www.accesspdf.com/pdftk/#service_menus)

More stuff:
[http://lindesk.com/2008/10/action-context-custom-service-menus-konqueror/](http://lindesk.com/2008/10/action-context-custom-service-menus-konqueror/)
[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html)
[http://techbase.kde.org/Development/Tutorials/Creating_Konqueror_Service_Menus](http://techbase.kde.org/Development/Tutorials/Creating_Konqueror_Service_Menus)
[http://www.kde-look.org/content/show.php/KDE4-servicemenus?content=80131](http://www.kde-look.org/content/show.php/KDE4-servicemenus?content=80131)
[http://www.kde-apps.org/content/show.php?content=37321](http://www.kde-apps.org/content/show.php?content=37321)

_**Nautilus integration:**_
[http://g-scripts.sourceforge.net/cat-fileproc.php#pdf](http://g-scripts.sourceforge.net/cat-fileproc.php#pdf)

---

### Post by tazztone on 2009-10-25
i compiled the project but did not find a "guipdftk.config" file. what's in it?

---

### Post by KIAaze on 2009-10-25
It just contains "/usr/bin/" with no new line at the end.
You can create it like this:
```
echo -n /usr/bin/ > guipdftk.config
```

If I remember correctly, it's the path of "pdftk" that should be in it.

Apparently, the creator of guipdftk put my new version on his site: v0.33. :)

---

### Post by tazztone on 2009-10-25
i sudo 'cp'ed the guipdftk.config file to usr/bin/ the oldschool way:P , but however thx for your help! you shall be blessed :popcorn:

---

### Post by dodjob on 2009-11-24
Hi Folks!
I' trying to make it work on my Karmic 64bit. Unfortunately it doesn't work due to missing library:
"/usr/bin/guipdftk: error while loading shared libraries: libgdk_pixbuf.so.2: cannot open shared object file: No such file or directory"
I've read and try to find a workaround but didn't found nothing :-(
Can someone help me? :-)
Grüß von Regensburg,
Dodjob

---

### Post by KIAaze on 2009-11-25
Normally, you would have to install the package libgdk-pixbuf-dev, but apparently it's not available for Karmic anymore.

You can try installing the old jaunty version from here eventually:
[http://packages.ubuntu.com/jaunty/libgdk-pixbuf-dev](http://packages.ubuntu.com/jaunty/libgdk-pixbuf-dev)

I'm trying to find out what happened to this package in Ubuntu 9.10:
[https://answers.launchpad.net/ubuntu/+source/gdk-pixbuf/+question/91632](https://answers.launchpad.net/ubuntu/+source/gdk-pixbuf/+question/91632)

---

### Post by dodjob on 2009-11-25
Hi,
Thanks for the reply!
I've tried to install it.. but well the link you sended me wasn't the lib I was needing (I think I'm a pseudo Noob)
I've choose this one:
[http://packages.ubuntu.com/jaunty/libs/libgdk-pixbuf2](http://packages.ubuntu.com/jaunty/libs/libgdk-pixbuf2)
but the message is the same (cannot find blabla) even if it is inside!!
Well I will take more time this evening.
Thanks again!
dodjob

---

### Post by tazztone on 2009-11-27
do you want to split or merge pdf's? if so, you can use [http://www.pdfsam.org]("http://www.pdfsam.org/")

---

