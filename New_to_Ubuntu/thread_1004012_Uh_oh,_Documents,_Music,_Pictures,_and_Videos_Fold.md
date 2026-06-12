---
title: "Uh oh, Documents, Music, Pictures, and Videos Folder disappeared from Places menu."
date: 2008-12-06
forum: New to Ubuntu
---

### Post by k3lt01 on 2008-12-06
Well the title says it all.

My Documents, Music, Pictures, and Videos folders have disappeared from my Places menu. Can I get them back? Does anyone know?

Thanks in advance.
Michael.

---

### Post by gettinoriginal on 2008-12-06
What does your home folder show, are they still there ??  If so, I would try a reboot.

---

### Post by k3lt01 on 2008-12-06
> **gettinoriginal said:**
> What does your home folder show, are they still there ??  If so, I would try a reboot.They are in my /home folder just not showing on my Places menu. I have rebooted numerous times.

---

### Post by T2manner on 2008-12-06
Your Places menu is simply your bookmarked folders.
if you go into nautilus you can drag folders over to the far left area, which is your Bookmars, and they should appear in your Places menu.

---

### Post by k3lt01 on 2008-12-06
> **T2manner said:**
> Your Places menu is simply your bookmarked folders.
if you go into nautilus you can drag folders over to the far left area, which is your Bookmars, and they should appear in your Places menu.

Have already done that, it doesn't replace them how they were originally. It's shown in the screenshot.

---

### Post by scorp123 on 2008-12-06
> **gettinoriginal said:**
> If so, I would try a reboot. This isn't Windows. A reboot _does not_ help in most cases, as the offending settings will just be there again. "Reboot and everything will be fine" is Windows-thinking and you better get rid of that, OK? ):P

---

### Post by gettinoriginal on 2008-12-06
At the top of your places browser window > Bookmarks > "highlight the folder you want to add" and click add bookmark.

---

### Post by gettinoriginal on 2008-12-06
> **scorp123 said:**
> This isn't Windows. A reboot _does not_ help in most cases, as the offending settings will just be there again. "Reboot and everything will be fine" is Windows-thinking and you better get rid of that, OK? ):P

yup, I agree, my fault is that I "tinker" with my system a lot and break it ](*,) so rebooting makes it fix itself sometimes.  But you are right, and I should not assume that the person has broken something :roll:

---

### Post by k3lt01 on 2008-12-06
> **gettinoriginal said:**
> At the top of your places browser window > Bookmarks > "highlight the folder you want to add" and click add bookmark. I have done that already, I even posted a screenshot of the outcome. They don't return to the place they were originally.

I have just check another profile I have on this machine as a "base" profile and the folders are in their correct spot in that profile. So I am assuming it is a simple settings file somewhere that needs fixing.

---

### Post by dracayr on 2008-12-06
```
gedit ~/.config/user-dirs.dirs
```

this is how it should look:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

if it's different, change it

dracayr

---

### Post by k3lt01 on 2008-12-06
> **dracayr said:**
> If it's different, change itThanks for that, this is the type of thing I am looking for. Unfortunately my file seems to be correct.
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by scorp123 on 2008-12-06
> **gettinoriginal said:**
> I should not assume that the person has broken something  Why not? It's just that rebooting won't help ;)

---

### Post by k3lt01 on 2008-12-06
Well my system had a major crash. I have only just got the laptop restarted an hour and a half later. I don't know what happened but I will check the logs. When I finally got it restarted the offending folders were back in their correct place in the Places menu.

---

### Post by scorp123 on 2008-12-07
> **k3lt01 said:**
> When I finally got it restarted the offending folders were back in their correct place in the Places menu. You probably lost your settings (minor filesystem corruption due to the crash) and Ubuntu recreated the default settings upon your login.

If this should happen again and you absolutely cannot find a way to correct it: You could open a new account (just as you did) and then copy those new default settings over to your previous account ... It's not really a nice way of fixing things but could be used as a last resort  ...

---

