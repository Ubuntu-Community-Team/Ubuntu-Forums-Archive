---
title: "can not remove folder Downloads"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by levchv on 2011-08-28
Hi.
I was rename folder /home/username/Downloads but after reboot I had two folders: my new downloads folder and /Downloads.
How I can delete folder /home/username/Downloads forever?

---

### Post by kartabosh on 2011-08-28
> **levchv said:**
> Hi.
I was rename folder /home/username/Downloads but after reboot I had two folders: my new downloads folder and /Downloads.
How I can delete folder /home/username/Downloads forever?

most likely your browser or some download client is set to download in ~/Downloads

---

### Post by kyletstrand on 2011-08-28
Try ```
rm -r ~/Downloads
```

---

### Post by N00b-un-2 on 2011-08-28
delete the folder.  If for some reason you can't remove it, it may be a permissions issue.  Open a terminal and 
```
sudo rm -rf /home/username/Downloads
```

then double check your web browser, torrent app etc. and make sure none of them are defaulting to ~/Downloads.  If any of them are, the folder will be automatically created.  One other thing to check is the file
/home/username/.config/user-dirs.dir
and comment out the line
```
XDG_DOWNLOAD_DIR="$HOME/Downloads"
```
by adding a # to the front of it.
```
# XDG_DOWNLOAD_DIR="$HOME/Downloads"
```
Hope that helps.

---

### Post by levchv on 2011-08-30
It was Skype).
Thanks.

---

