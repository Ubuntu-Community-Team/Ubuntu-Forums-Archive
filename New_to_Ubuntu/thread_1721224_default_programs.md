---
title: "default programs ?"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-04
how do i set a default program for a file ?
eg open .mp3 with vlc instead of rythmbox
eg open .torrent with deluge instead of transmission
 ?

---

### Post by ~Plue on 2011-04-04
right click the .mp3/.torrent >> open with other application >> select your preferred app and check "remember this application for '*' files"

---

### Post by neil_1 on 2011-04-04
dosnt happen,it dosnt remember :(

---

### Post by IWantFroyo on 2011-04-04
You could delete Rhythmbox and Transmission. 
I think it is:
```
sudo apt-get install --purge rhythmbox transmission
```
I could be wrong.

---

### Post by ~Plue on 2011-04-04
> **neil_1 said:**
> dosnt happen,it dosnt remember :(
run [FONT=monospace]
[/FONT]rm -R ~/.local/share/applications/* 
rm -R ~/.gnome/share/apps/*

and see if the 'open with' dialog works again

if it still doesn't remember, press alt+F2 and enter
```

gedit .local/share/applications/defaults.list

```and add/edit the following lines[FONT=monospace]
[/FONT]```

audio/x-mp3=vlc.desktop
application/x-bittorrent=deluge.desktop

```

---

### Post by neil_1 on 2011-04-04
> **IWantFroyo said:**
> You could delete Rhythmbox and Transmission. 
I think it is:
```
sudo apt-get install --purge rhythmbox transmission
```I could be wrong.
i dont want to delete them ,  i just want to make files open with diff apps .
> **~Plue said:**
> run [FONT=monospace]
[/FONT]rm -R ~/.local/share/applications/* 
rm -R ~/.gnome/share/apps/*

and see if the 'open with' dialog works again

if it still doesn't remember, press alt+F2 and enter
```

gedit .local/share/applications/defaults.list

```and add/edit the following lines[FONT=monospace]
[/FONT]```

audio/x-mp3=vlc.desktop
application/x-bittorrent=deluge.desktop

```
the open dialogue shows but it dosnt remember the defaults i give it
.local/share/applications/defaults.list  dosnt exist,should i make one ?

---

### Post by ~Plue on 2011-04-04
> **neil_1 said:**
> 
.local/share/applications/defaults.list  dosnt exist,should i make one ?
sure, but first, see if there's a mimeapps.list in the same directory. if it is there, then edit that file instead.

---

### Post by PunkLV on 2011-04-04
There is a simple way. It is a nautilus setting after all.
Rightclick file - Properties - 'Open with' tab - choose one/add - done.

This method works exactly for a specific file extention, meaning if you set .jpg to open in GIMP, then the rest image files will be opened by gnome default EOG application still. Same for .avi .mkv .mp3.

---

### Post by neil_1 on 2011-04-05
thanks ~plue ,it worked :D
@punklv,thats what i tried , it dint save the setting though :/

---

