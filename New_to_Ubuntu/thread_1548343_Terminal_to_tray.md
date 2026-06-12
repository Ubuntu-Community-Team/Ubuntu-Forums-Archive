---
title: "Terminal to tray"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-08-08
Is there any way to send Terminal to tray on the LXDE desktop?

When I was using Gnome I would do this by using the AllTray app. But, in LXDE sending some apps don't behave correctly when sending to tray by AllTray. When I do this in LXDE Terminal won't pop back up when clicking on the icon in the tray. For me to get Terminal to pop back I have to actually hit the Undock option. Then if I want to send it back to tray I have to use AllTray again.

Basically I pretty much only want to send Terminal to tray for when I use Rtorrent. I keep Rtorrent open almost always, so I would have it be sitting in the task tray rather than on panel.

Any help will be greatly appreciated. Thanks.

---

### Post by kerry_s on 2010-08-08
what about installing a different terminal? there's even terminals that can pop in & out. i think i used tilda back in the day.

---

### Post by h8uthemost on 2010-08-08
So you think my only solution will be installing a different Terminal? I'll look into others. And see if Tilda docks in LXDE.

EDIT: Actually, are there Terminals that have a minimize to try option built into it? Because it looks like AllTray just doesn't work well with LXDE desktop. AllTray will dock whatever, but you just can't simply click on the icon to pop it up. You have to undock.

Also, I gave wterm an install(supposed to be a very light Terminal), and it doesn't appear in any of my menus(even after logging out and back in). So I had to start by starting LXTerminal and then type wterm. So it's installed, it's just not showing up in my menu. Anyone happen to know why that is? If it's lighter than LXTerminal then I'm going to keep wterm and delete lxterminal.

Thanks.

---

### Post by h8uthemost on 2010-08-09
Bump.

Any other help on this? Also, I'm still trying to figure out why wterm isn't showing up in my menus? Think it will show up if I uninstall LXterminal?

Thanks.

---

### Post by kerry_s on 2010-08-09
wterm probably doesn't have a *.desktop file, thats why it's not in the menu.

uninstalling lxterminal will not help.

why not just put it on another virtual desktop?
you could even use your ctrl+alt+f1 thru f6.

what if you try using a different system tray, like trayer, docker, etc...

---

### Post by cavalier911 on 2010-08-09
Lubuntu/lxde/openbox use *.desktop files for the menu/launcher icons.
When the .deb packagers exclude a .desktop file you have to make your own.
I dup/rename/edit one from a similar program in the same location of the menu where I want the new one to go--->/usr/share/applications/lxterminal.desktop  
```
sudo cp /usr/share/applications/lxterminal.desktop /usr/share/applications/wterm.desktop
``````
sudo nano /usr/share/applications/wterm.desktop
```Leave everything the same except:
Name=wterm 
TryExec=wterm   
Exec=wterm 

Now you have menu/Accessories/Wterm

---

### Post by h8uthemost on 2010-08-09
Very cool cavalier. Thank you so much for this. wterm is now in my Accessories menu.

By the menu, what would wterm show up as in the task manager? All that I'm seeing it show up as is bash. I thought it would show up as wterm. If bash is indeed wterm, then it's only taking 3MB. Where LXterminal takes 9MB. So that would be great and I could uinstall LXterminal.

One more thing, can I use this same method to make a launcher for rtorrent?  Just type in the two terminal codes that you posted, and then edit:

Name=rtorrent 
TryExec=rtorrent
Exec=rtorrent 

Thank you for your help.

---

### Post by cavalier911 on 2010-08-09
top lists wterm as (2.3MB).9% MEM out of 256MB ram.

If you like the icons your using for wterm copy/rename before you uninstall lxterminal which will remove them.
 
```
sudo cp /usr/share/pixmaps/lxterminal.png /usr/share/pixmaps/wterm.png
``````
sudo cp /usr/share/pixmaps/lxterminal.xpm /usr/share/pixmaps/wterm.xpm
``````
sudo nano /usr/share/applications/wterm.desktop
```Icon=wterm

For rtorrent use /usr/share/applications/transmission.desktop for the template.

I dup/rename the transmission icons like lxterminals.

Ncurses/terminal programs:

Exec=x-terminal-emulator  -e /full/path/to/binary

[Desktop Entry]
Name=rtorrent
GenericName=BitTorrent Client
Comment=Download and share files over BitTorrent
Exec=x-terminal-emulator -e /usr/bin/rtorrent
Icon=rtorrent
Terminal=yes
Type=Application
MimeType=application/x-bittorrent;
Categories=Network;FileTransfer;P2P;

menu/internet/rtorrent

---

### Post by h8uthemost on 2010-08-10
Thank you once again cavalier911, that worked. One thing though, rtorrent pops up in LXterminal. What should I edit to have it pop up in wterm?

Also, I'm guessing why distros aren't using this lightweight wterm because it has pretty much no basic functions. No tabs, no copy/paste ability, etc. It's incredibly light, but a very basic terminal.

---

### Post by cavalier911 on 2010-08-10
This will open rtorrent in wterm:

```
sudo update-alternatives --config x-terminal-emulator 
```returns
```
There are 2 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

  Selection    Path                 Priority   Status
------------------------------------------------------------
* 0            /usr/bin/lxterminal   40        auto mode
  1            /usr/bin/lxterminal   40        manual mode
  2            /usr/bin/wterm        20        manual mode

Press enter to keep the current choice
[*], or type selection number: 2
update-alternatives: using /usr/bin/wterm to provide /usr/bin/x-terminal-emulator (x-terminal-emulator) in manual mode.

```

---

### Post by h8uthemost on 2010-08-10
Yep, that indeed did it. I hit rtorrent in my Internet menu and it pops up in wterm.

Thank you so much for your help. It is really appreciated.

EDIT: One more question. Now that rtorrent has taken the place of Transmission in the Internet menu, if I uinstall Transmission from Synaptics, will that affect the rtorrent icon at all?

---

### Post by cavalier911 on 2010-08-10
The transmission deb packages when removed can only delete file/folder names it installed. A power tool called apt-file let's you find any filename within debs in your repository lists.The only drawback is it downloads it's own lists from your /etc/apt/sources.list, around 17MB on lubuntu. 

```
rj@lubuntu:~$ apt-file find transmission.xpm
elementary-icon-theme: /usr/share/icons/elementary/apps/24/transmission.xpm
elementary-icon-theme: /usr/share/icons/elementary/apps/48/transmission.xpm
transmission-common: /usr/share/pixmaps/transmission.xpm
xubuntu-icon-theme: /usr/share/icons/elementaryXubuntu/apps/24/transmission.xpm
xubuntu-icon-theme: /usr/share/icons/elementaryXubuntu/apps/48/transmission.xpm
```transmission-common owns /usr/share/pixmaps/transmission.xpm 

rtorrent icon will not be removed if you either cp or mv rename the transmission icons to rtorrent.png and rtorrent.xpm then link to them in the rtorrent.desktop file as Icon=rtorrent

If the icon your linking to is removed you end up with the dead link icon:  
menu/Other/Openbox Session

---

### Post by h8uthemost on 2010-08-11
Honestly, I have no idea what all that means. :p You are obviously way more advanced in the command line then I am.

But, I did uninstall Transmission, and the rtorrent icon in the Internet menu is gone.

Thanks for the reply.

---

