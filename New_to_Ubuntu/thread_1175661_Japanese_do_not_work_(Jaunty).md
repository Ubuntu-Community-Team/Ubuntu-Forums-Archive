---
title: "Japanese do not work (Jaunty)"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by berdux on 2009-06-01
Hello!

I have Ubuntu 9.04
i've been trying for some time now to install japanese input. I firstly went to System->Preferences->Keyboard and added japanese layout (i already had English and Greek), but nothing happened, when i selected Jpn it was inputing in english.

Then i went to System->Administration->Language Support and installed japanese language. even after that the SCIM toolbar did not show up when i selected Jpn. It does not show up even if i press Ctrl+Space.

I uninstaled/reinstaled the Jpn keyboard layout and the japanese language several times but i cannot make the SCIM toolbar appear. in System->Preferences there are options for SCIM toolbar but whatever i select it doesn't work.

do you have any suggestions?

thanks in advance :)



edit:
i've been using ubuntu for several months now
on my previous computer I had Japanese installed without encountering any such problem, it had ubuntu 8.10

---

### Post by Cardcaptor Stacey on 2009-06-01
Have you tried this tutorial? [http://kubuntuforums.net/forums/index.php?topic=3099856.0](http://kubuntuforums.net/forums/index.php?topic=3099856.0) Works great for me. Make sure you change skim to scim and it should work for Ubuntu.

---

### Post by berdux on 2009-06-01
i cannot do most of these things... they are for interpid, and most apps and folders are for kubuntu or sth... i tried to add these by replacing interpid with jaunty.. but still i cannot type in japanese.. 

i fear that i have messed things up very much now :$

i tried things from this tutorial also but most things could not work 
[http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552)

---

### Post by berdux on 2009-06-01
well after the last restart it seems to work...

---

### Post by James Keating on 2009-06-04
In case you have further probems:

My experience with installing SCIM in 9.04 (Jaunty) was mostly simple. I added full Japanese support through Administration/Language Support, and SCIM worked fine with the standard set of packages. 

However, I had one problem that I didn't recognize as being related to SCIM: I had constant trouble with losing keyboard input. If I used any input field or blank in my Web browser, the keyboard wouldn't respond again until I forced window manager to focus on the program again by clicking on the title bar or by right-clicking on the page and canceling. The problem with typing showed up mainly with Opera, which uses the Qt toolkit, and in TkDesk, which uses Tcl/Tk. I thought that this might be a problem with my window manager, FVWM, or with GDM, since GDM is the background to everything else. 

The problem was that SCIM defaulted to using XIM, though SCIM-bridge is better. Other posts here refer to editing the file /etc/X11/xinit/xinput.d/scim-bridge. You don't have to go there directly. In your home directory, there should be a hidden directory called .xinput.d, with a file that links to  /etc/X11/xinit/xinput.d/scim-bridge. My file is named en_US. All I had to do was edit it (as root) and change the module lines. For GTK-based programs, I changed them to prefer SCIM-bridge and then SCIM. For Qt-based programs, I changed the module lines to prefer SCIM, then XIM. The only Qt-based program I use is Opera, but Opera won't work with SCIM-bridge, even though the file /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so is present.  

My /etc/X11/xinit/xinput.d/scim-bridge now looks like:

XIM=SCIM
if [ -e /usr/bin/skim ]; then
    XIM_PROGRAM=" "
else
    XIM_PROGRAM=/usr/bin/scim-bridge
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=scim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi
DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"

This also fixed the focus problem with TkDesk. 

Qt programs need the packages scim-bridge-client-qt and scim-qtimm. 
Also, it may help to edit your file ~/.scim/global to add the line 
/DefaultConfigModule = kconfig

Before I found a proper fix for Opera, I was able to start it with
scim -d & XMODIFIERS="@im=SCIM" QT_IM_MODULE="scim" opera

#####

Update for Lucid 10.04:

Ubuntu now uses IBus and no longer supports SCIM. Too bad IBus doesn't work with any Qt-based programs. 

My current language setup:

1. Under System, Administration, Language Support, choose Japanese.

2. Install programs that Ubuntu doesn't include by default (including essential packages ...)
edict
enamdict
gjiten
kanjidic
kdrill
poppler-data (to view Japanese PDFs)
gs-cjk-resource
cmap-adobe-japan1 
cmap-adobe-japan2
xpdf-japanese

I also installed more ttf fonts, but not all: Sazanami and Kochi gothic and mincho, VL Gothic, , Kiloji, Mikachan and ttf-mscorefonts (MS Gothic and Mincho, Osaka).
Other nice fonts are available at [http://www.wazu.jp/gallery/Fonts_Japanese2.html;](http://www.wazu.jp/gallery/Fonts_Japanese2.html;) download and put in your ~/.fonts directory. Not all have romaji, and not all even work. I kept: Aoyagi Kouzan(&#38738;&#26611;&#34913;&#23665;), Soseki and Reishoka (&#38738;&#26611;&#38583;&#26360;&#19979;), Aquafont, Armed Lemon, Azukifont, Cinecaption, Deshima (&#20986;&#23798;), several Epson fonts, HuiFont, Kouzan brush (two), Makiba, Mona, Moon, MtTare, nagurigaki, Ohisama, Onryou, SZG Memo, Sanafon (two), Sea, Sword, unifont 

3. the hidden home directory file ~/.xinput.d/en_US, which links to /etc/X11/xinit/xinput.d/scim-bridge, may need editing (as root)
I changed mine to prefer scim-bridge, then scim, and not xim:

XIM=SCIM
if [ -e /usr/bin/skim ]; then
    XIM_PROGRAM=" "
else
    XIM_PROGRAM=/usr/bin/scim-bridge
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=scim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
else
    QT_IM_MODULE=scim
fi
DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"

4. Opera, and possibly other QT-based applications, may have more trouble than before. If you can't get Opera to work again with scim, you can start it from the command line with 
	scim -d & XMODIFIERS="@im=SCIM" QT_IM_MODULE="scim" opera

To start it from the regular menu, I made a file called ~/.bin/opera-scim:

#!/bin/sh
QT_IM_MODULE="scim"; export QT_IM_MODULE
XIM_PROGRAM="scim -d"; export XIM_PROGRAM
opera

and then edited the menus to change the properties of the Opera item to run that file:
opera-scim %u

---

