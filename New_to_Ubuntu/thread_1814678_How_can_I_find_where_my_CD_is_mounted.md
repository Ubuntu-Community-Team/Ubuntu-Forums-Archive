---
title: "How can I find where my CD is mounted?"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by s1baker on 2011-07-29
hi, I have a music disk in my CD player and I am trying to locate it with Audacious music player so that I can load the files in. I can't find where the CD is mounted. I have looked everywhere and I can't find it. The /cdrom folder is empty and I can't find it under /media. What do I need to do to see where it is mounted?

Thanks

---

### Post by wojox on 2011-07-29
Is your CD Player connected by USB?

Run:

```
sudo fdisk -l
```

---

### Post by s1baker on 2011-07-29
No, it is an internal CD

---

### Post by s1baker on 2011-07-29
all sudo fdisk -l shows is my 2 harddrives i have hooked up, sda and sdb.
I don't know how to run the second command you posted.
I know the CD works because I am listening to music on it right now. I have a cd disk icon on my desktop, and I can click on it and see the list of the tracks, and I can open RythmBox and play the music, also I can click on an individual track and it will play with the movie player.

---

### Post by wojox on 2011-07-29
> **s1baker said:**
> No, it is an internal CD

Look in your /dev directory.

---

### Post by s1baker on 2011-07-29
I can't see anything under devs/ directory.
Attached is a screenshot of my devs folder:

---

### Post by wojox on 2011-07-29
Open your file manager, Nautilus and click on your CD and it should show you where it is mounted. You may also try from the terminal:

```
sudo blkid
```

---

### Post by s1baker on 2011-07-29
sudo blkid only shows my UID's of my two hardrives that I have on my ribbon.

The screenshot I posted is from using nautilus

---

### Post by mc4man on 2011-07-30
If you wanted to view the files they're at  ~/.gvfs/cdda mount on sr[COLOR="Blue"]X[/COLOR]
But that's not what you want to do with audacious or any other player

Audacious has a plugin, (Audio Cd Plugin), should be enabled, ck. though - File > Preferences > Plugins

To access directly from audacious, with cd in drive just open - Components > Play CD

If wanting to ck., -  > with cd in drive open terminal and go - 
```
audacious2 -E cdda://
```

Audacious can also be set as the default autorun on audio cd insertion, to do so properly, (so aud shows cd track info instead of 'Track 1, ect.), requires a small script and .desktop
Quite easy - just ask (screen 2 ), if so what release of ubuntu are you using and post this file please. If it comes up blank just close without saving and note that.


```
gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by s1baker on 2011-07-30
Thanks mc4man.

I found where the files were under the .gvfs folder and when I piut a CD in and type audacious2 -E cdda:// , audacious will run with all of the titles properly displayed. Although, i did get this message in the terminal :
```
		CDROM sensed: ATAPI    iHAP322   9      6L1H SCSI CD-ROM

Audio CD Plugin should be updated to provide play().
Plugin Audio CD Plugin should be updated to use OutputAPI::write_audio.

```

and this command:
```
gedit ~/.local/share/applications/mimeapps.list
```

gives this:

```
[Added Associations]
application/x-wine-extension-lsp=gedit.desktop;wine-extension-ini.desktop;evince.desktop;
application/x-msdownload=wine-extension-ini.desktop;
application/x-wine-extension-vbi=openoffice.org-writer.desktop;wine-extension-wri.desktop;wine-extension-ini.desktop;
application/x-extension-bin=openoffice.org-writer.desktop;userapp-sh-TYTQMV.desktop;
application/msword=gedit.desktop;evince.desktop;
application/x-extension-BAT=openoffice.org-writer.desktop;wine-extension-slg.desktop;
application/x-wine-extension-inf=wine.desktop;openoffice.org-writer.desktop;evince.desktop;
application/x-ms-dos-executable=openoffice.org-writer.desktop;wine.desktop;
image/bmp=eog.desktop;openoffice.org-draw.desktop;
application/octet-stream=openoffice.org-writer.desktop;wine-extension-psf.desktop;evince.desktop;
application/x-wine-extension-mnu=gedit.desktop;
audio/mpeg=audacious2.desktop;
text/x-emacs-lisp=gedit.desktop;openoffice.org-writer.desktop;
video/x-flv=gedit.desktop;
text/plain=gedit.desktop;
application/x-spss-sav=openoffice.org-writer.desktop;
application/pgp-encrypted=openoffice.org-writer.desktop;
application/zip=openoffice.org-writer.desktop;
application/x-trash=openoffice.org-writer.desktop;
application/x-executable=audacious2.desktop;
application/x-shellscript=gedit.desktop;
application/x-perl=evince.desktop;
image/x-portable-graymap=openoffice.org-writer.desktop;
text/html=firefox.desktop;
```
I am using Ubuntu 10.10  32 bit

---

### Post by mc4man on 2011-07-30
Been awhile since I used 10.10, should work out.
Will use all commands, you're creating a ~/bin to place the script in., can be used later to some advantage.. 
(commands may be a bit more than needed, no worry, just 'covering bases' - the create the .desktop in home folder and then mv instead of creating in place is probably not needed, but at some point it seemed to be so might as well do.

If at any point after closing gedit the terminal prompt doesn't return to your normal, just put cursor focus back on terminal and  press Ctrl+c 

Open a terminal - 
```
mkdir -p bin && gedit bin/audcd
```
paste this into gedit, save and close gedit

```
#!/bin/bash
audacious2 -E cdda://
```

```
chmod u+x ~/bin/audcd
```
```
gedit audcd.desktop
```

paste this in, save, close gedit (feel free to change the Name= if desired, - I'm guessing the icon is named audacious instead of audacious2
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=Audacious Cd Player
Icon=audacious
Exec=audcd
MimeType=x-content/audio-cdda;
```

save  & close gedit
Below is one command, copy and paste all

```
mv ~/audcd.desktop ~/.local/share/applications/ && \
chmod u+x ~/.local/share/applications/audcd.desktop
```

Finally - 
```
gedit ~/.local/share/applications/mimeapps.list
```

You don't have this line as of posting so add to bottom, save and close gedit, terminal (d. check it didn't sneak in, if so then just  replace
```
x-content/audio-cdda=audcd.desktop;
```

Before trying you'll need to do a full restart, that will add ~/bin to your PATH so the script can be executed

After restarting put an audio cd in the drive and hold down your shift key until you get a pop up similar to my screen.
Hopefully it will be in the list, if not we can get it or you could do something else with the dropdown

Should be ok.

---

### Post by s1baker on 2011-07-31
thanks mc4man.
I did all of the listings as you posted and I now have the audacious icon on my desktop. When I put in a cd, I wait for a few seconds and the generic Ubuntu cd icon pops up on the desktop. Then when I click on the audacious icon , audacious runs, with the cd music listings displayed, with the proper titles.
I have always said that this is the best website in the World for getting help, and you are one of the reasons for this. Thanks again.

---

