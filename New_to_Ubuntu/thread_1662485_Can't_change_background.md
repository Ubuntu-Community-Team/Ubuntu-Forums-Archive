---
title: "Can't change background"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by bros on 2011-01-08
[SIZE=3]I have Ubuntu 10.10 Desktop Edition on my HP Mini 210-1100. By using the application ***Ubuntu Tweak*** I tried several times to change my background, the pics are  in *File System*>*usr*>*share>backgrounds*. Right now I'm trying to add new wallpapers in the *backgrounds* folder but every time I got this message:[/SIZE]

[CENTER][SIZE=3][I][COLOR=Red][B]Error while moving "1280_nfl_wallpaper.jpg".
There was an error moving the file into /usr/share/backgrounds.
Error moving file: Permission denied[/B][/COLOR][/I][/SIZE]

[LEFT][SIZE=2][COLOR=Black][SIZE=3]Than I went to *backgrounds folder*>*properties*>*permissions *I got this message on the bottom of the window:[/SIZE]

[/COLOR][/SIZE][CENTER]

[SIZE=3][B]You are not the owner, so you cannot change these permissions.

[/B][/SIZE]
[LEFT][SIZE=3]Please help me! Thank you^^[/SIZE]
[SIZE=3]Bros[/SIZE]
[/LEFT]


[/CENTER]
[/LEFT]
[/CENTER]

---

### Post by josepaul on 2011-01-08
Open up terminal (*Applications>accessories>Terminal*) then try 

```
sudo ubuntu-tweak
```

and then try to change the background.

---

### Post by bros on 2011-01-08
> **josepaul said:**
> Open up terminal (*Applications>accessories>Terminal*) then try 

```
sudo ubuntu-tweak
```and then try to change the background.

[SIZE=3]I can only use the pics that are already in that folder but not others...[/SIZE]

---

### Post by josepaul on 2011-01-08
> **bros said:**
> [SIZE=3]I can only use the pics that are already in that folder but not others...[/SIZE]

ok, so you're trying to copy these images to this folder right?

usr/share/backgrounds

Just use sudo when you're copying. Your problem is that when you try that command, it has insufficient rights to copy a file to a folder like that. So when you use sudo, you give it enough rights. 

E.g. I have a background I wanna copy in this folder /home/username/Pictures called xyz.jpg

So I open up terminal and type in ```
sudo cp /home/username/Pictures/xyz.jpg /usr/share/backgrounds/xyz.jpg
```

---

### Post by bros on 2011-01-08
> **josepaul said:**
> ok, so you're trying to copy these images to this folder right?

usr/share/backgrounds

Just use sudo when you're copying. Your problem is that when you try that command, it has insufficient rights to copy a file to a folder like that. So when you use sudo, you give it enough rights. 

E.g. I have a background I wanna copy in this folder /home/username/Pictures called xyz.jpg

So I open up terminal and type in ```
sudo cp /home/username/Pictures/xyz.jpg /usr/share/backgrounds/xyz.jpg
```

[SIZE=3]Yes, I'm trying to copy new pics in that folder but I can't. I tried to use sudo cp but this directory doesn't work...[/SIZE]

---

### Post by josepaul on 2011-01-08
> **bros said:**
> [SIZE=3]Yes, I'm trying to copy new pics in that folder but I can't. I tried to use sudo cp but this directory doesn't work...[/SIZE]

Where is this picture that you wanna copy? e.g. where's "1280_nfl_wallpaper.jpg"

---

### Post by bros on 2011-01-08
> **josepaul said:**
> Where is this picture that you wanna copy? e.g. where's "1280_nfl_wallpaper.jpg"
[SIZE=3]
/home/bros/Pictures/Bros Pics/Backgrounds/1280_nfl_wallpaper.jpg[/SIZE]

---

### Post by josepaul on 2011-01-08
> **bros said:**
> [SIZE=3]
/home/bros/Pictures/Bros Pics/Backgrounds/1280_nfl_wallpaper.jpg[/SIZE]

post output when you type in this:

```
sudo cp "/home/bros/Pictures/Bros Pics/Backgrounds/1280_nfl_wallpaper.jpg" "/usr/share/backgrounds/1280_nfl_wallpaper.jpg"
```

---

### Post by bros on 2011-01-08
PERFECT! Thank you very much for your help!^^

---

