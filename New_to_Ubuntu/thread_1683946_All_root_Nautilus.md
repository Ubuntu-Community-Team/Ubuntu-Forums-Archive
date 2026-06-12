---
title: "All root Nautilus"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Frankiewizard on 2011-02-08
When I click on Places-Home folder Nautilus starts on root. When it comes to files on the desk top every thing opens fine.

Cheers...............

---

### Post by kellemes on 2011-02-08
Thanks for sharing :confused:

Anyway, lots of reasons not to do this..

Edit: Scrap that.. I misunderstood the question.

---

### Post by philinux on 2011-02-08
> **kellemes said:**
> Thanks for sharing :confused:

I think the OP means instead of opening his home folder it opens /. Not sure though.

---

### Post by Frankiewizard on 2011-02-08
Why is it opening on 'root'? thats the question.

---

### Post by sydbat on 2011-02-08
> **Frankiewizard said:**
> Why is it opening on 'root'? thats the question.Can you provide a screenshot or two?

---

### Post by philinux on 2011-02-08
> **Frankiewizard said:**
> Why is it opening on 'root'? thats the question.

Open a terminal and post back what this command shows. Use copy and then paste it into the terminal.

```
echo $HOME
```

---

### Post by wojox on 2011-02-08
And this as well:

```
cat .config/user-dirs.dirs
```

---

### Post by Frankiewizard on 2011-02-08
/home/frankiewizard
frankiewizard@frankiewizard-Qosmio-G20:~$ 


I think thats it
Cheers..............

---

### Post by Frankiewizard on 2011-02-08
> **wojox said:**
> And this as well:

```
cat .config/user-dirs.dirs
```

This what I got..........


 This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
frankiewizard@frankiewizard-Qosmio-G20:~$

---

### Post by sydbat on 2011-02-08
> **Frankiewizard said:**
> /home/frankiewizard
frankiewizard@frankiewizard-Qosmio-G20:~$ 


I think thats it
Cheers..............

> **Frankiewizard said:**
> This what I got..........


 This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
frankiewizard@frankiewizard-Qosmio-G20:~$That all looks right.

Stupid question time...are you sure that when you click "Home Folder" that you are going into "root" (aka /)? This is why I asked for a screen shot, so we can take a look at what you are seeing.

---

### Post by philinux on 2011-02-08
assuming that initially things were working ok. What if anything have you been attempting to change or modify the instal in any way?

---

### Post by Frankiewizard on 2011-02-08
> **sydbat said:**
> That all looks right.

Stupid question time...are you sure that when you click "Home Folder" that you are going into "root" (aka /)? This is why I asked for a screen shot, so we can take a look at what you are seeing.

I understand. Here is the screen shot. Many thanks.

---

### Post by wojox on 2011-02-08
That's weird. Have you tried:

```
sudo chown your_username -R $HOME
```

---

### Post by vanadium on 2011-02-09
That is a dangerous command if you just try it as a shot in the dark.

Can you post the output of
```

echo $USER
ls -l /home
ls -ln /home

```
before proceeding.

---

### Post by Frankiewizard on 2011-02-09
> **wojox said:**
> That's weird. Have you tried:

```
sudo chown your_username -R $HOME
```


After typing this I get

frankiewizard@frankiewizard-Qosmio-G20:~$ sudo chown frankiewizard -R $HOME
chown: cannot access `/home/frankiewizard/.gvfs': Permission denied

---

### Post by Frankiewizard on 2011-02-09
> **vanadium said:**
> That is a dangerous command if you just try it as a shot in the dark.

Can you post the output of
```

echo $USER
ls -l /home
ls -ln /home

```
before proceeding.

The result is frankiewizard@frankiewizard-Qosmio-G20:~$ echo $USER ls -l /home ls -ln /home
frankiewizard ls -l /home ls -ln /home
frankiewizard@frankiewizard-Qosmio-G20:~$

---

### Post by Frankiewizard on 2011-02-09
> **Frankiewizard said:**
> The result is frankiewizard@frankiewizard-Qosmio-G20:~$ echo $USER ls -l /home ls -ln /home
frankiewizard ls -l /home ls -ln /home
frankiewizard@frankiewizard-Qosmio-G20:~$

I think this is the answer I should have given you.........

frankiewizard@frankiewizard-Qosmio-G20:~$ ls -l /home
total 20
drwxr-xr-x 50 frankiewizard frankiewizard  4096 2011-02-09 12:27 frankiewizard
drwx------  2 root          root          16384 2011-02-05 00:18 lost+found
frankiewizard@frankiewizard-Qosmio-G20:~$ ls -ln /home
total 20
drwxr-xr-x 50 1000 1000  4096 2011-02-09 12:27 frankiewizard
drwx------  2    0    0 16384 2011-02-05 00:18 lost+found
frankiewizard@frankiewizard-Qosmio-G20:~$

---

### Post by vanadium on 2011-02-09
This looks normal and OK, but I still do not have the output of "echo $USER". I was wondering if in one or another way you could have managed to change your user name to "root" without changing anything else of your account. This might be possible, especially since the root account on ubuntu is not active.

---

### Post by Frankiewizard on 2011-02-09
> **vanadium said:**
> This looks normal and OK, but I still do not have the output of "echo $USER". I was wondering if in one or another way you could have managed to change your user name to "root" without changing anything else of your account. This might be possible, especially since the root account on ubuntu is not active.


frankiewizard@frankiewizard-Qosmio-G20:~$ echo $USER
frankiewizard
frankiewizard@frankiewizard-Qosmio-G20:~$ ls -l /home
total 20
drwxr-xr-x 50 frankiewizard frankiewizard  4096 2011-02-09 14:08 frankiewizard
drwx------  2 root          root          16384 2011-02-05 00:18 lost+found
frankiewizard@frankiewizard-Qosmio-G20:~$ ls -ln /home
total 20
drwxr-xr-x 50 1000 1000  4096 2011-02-09 14:08 frankiewizard
drwx------  2    0    0 16384 2011-02-05 00:18 lost+found
frankiewizard@frankiewizard-Qosmio-G20:~$ 

This time it looks a bit different I hope I typed the code in correctly the first time.
Cheers...............

---

### Post by vanadium on 2011-02-09
All normal, so the question remains why nautilus would use "root" as the label. It looks as if this is not causing any issue except for an aesthetically one, so I suggest you live with it, unless someone finds where the culprit is.

---

### Post by Frankiewizard on 2011-02-09
> **vanadium said:**
> All normal, so the question remains why nautilus would use "root" as the label. It looks as if this is not causing any issue except for an aesthetically one, so I suggest you live with it, unless someone finds where the culprit is.

Well any way thanks for all your help I think that I will wait untill the next LTS come out 11.04.
Cheers.......................

---

