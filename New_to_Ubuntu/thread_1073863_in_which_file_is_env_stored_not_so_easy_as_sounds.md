---
title: "in which file is env stored? not so easy as sounds"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by MichaelWyckmans on 2009-02-18
ok - i am a recent newbie to linux, please spare me - but this i get when input 'env' in shell:

mw@wm-laptop:~$ env
ORBIT_SOCKETDIR=/tmp/orbit-mw
GPG_AGENT_INFO=/tmp/seahorse-nnRkdI/S.gpg-agent:6249:1
SHELL=/bin/bash
TERM=xterm
XDG_SESSION_COOKIE=ad7e6d1a497a847bd939ba1a490c7a99-1234990142.335046-849274327
GTK_RC_FILES=/etc/gtk/gtkrc:/home/mw/.gtkrc-1.2-gnome2
WINDOWID=67117031
USER=mw
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
LIBGL_DRIVERS_PATH=/usr/lib/dri:/usr/lib32/dri
LD_LIBRARY_PATH=:/usr/lib32
GNOME_KEYRING_SOCKET=/tmp/keyring-s66ytk/socket
SSH_AUTH_SOCK=/tmp/keyring-s66ytk/ssh
SESSION_MANAGER=local/wm-laptop:/tmp/.ICE-unix/6167
USERNAME=mw
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib:/usr/lib32:/opt/real/RealPlayer
DESKTOP_SESSION=gnome
GDM_XSERVER_LOCATION=local
PWD=/home/mw
LANG=en_GB.UTF-8

GNOME_KEYRING_PID=6157
GDM_LANG=en_GB.UTF-8
KDEDIRS=/usr/share/debian-edu-artwork/kde-profile:
GDMSESSION=gnome
HISTCONTROL=ignoreboth
SHLVL=2
HOME=/home/mw
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=mw
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-NvY2fL3VLr,guid=a8d696de6c53d4d5445a2947499c7440
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/mw/.Xauthority
_=/usr/bin/env


my question? where are all those variables stored? it seems to me it is disparate.
for example: i ran a program called regexxer (supposed to scan files for strings) for [/opt/real/RealPlayer] (without bracelets) and it gave nothing... what am i missing here? i can understand how this could be a strange/stupid question for more experienced users - but even a link to an article where these things are explained would be very much appreciated.

thankx

MW

---

### Post by raffaele181188 on 2009-02-18
"env" is a command that outputs all your system variables. Those variables are _NOT_ stored in any file, they belong to your environment (better, to your shell). If you like you can google for what a "shell" is. Briefly, a "shell" *surrounds* your kernel (which you can think of as a collection of drivers) and allows you to communicate with your hardware. Shells can associate values to keys, and retrieve them by their name. This is the use of a variable

The program regexxer is a gui for search/replace operations, and is intended for experienced users, since it uses Per regular expression. I think you don't need that program, maybe you misunderstood its objective

---

### Post by zabien1970 on 2009-02-18
Try
```
man env
```
man being the manual pages for commands

---

### Post by MichaelWyckmans on 2009-02-18
so there is not fysical file where those variables are stored? the system (kernel) just takes them

i used the program to find the file (which is non-existant if i believe you) containing a random string from env, but the result was, ofcourse, 0/0

---

### Post by raffaele181188 on 2009-02-18
Yes, you will never find a file containing your variables. They are stored in your shell (not in your kernel). The shell is a program, althought a particular one. And has variables (which is a facility feature). Try google "shell" "csh" "bash" ;-)

Luck

---

### Post by snova on 2009-02-18
Environment variables have no central file where they are stored- I'm not even entirely sure the *kernel* cares about them. They are propogated from parent process to child process as new programs are run, in a tree-like fashion.

There are a few files that are run which contain initial values for certain variables, but I can only say so with certainty for shells.

---

### Post by JKyleOKC on 2009-02-18
> **raffaele181188 said:**
> Yes, you will never find a file containing your variables. They are stored in your shell (not in your kernel). The shell is a program, althought a particular one. And has variables (which is a facility feature). Try google "shell" "csh" "bash" ;-)

Luck
While it's true that no single file contains all the env variables, they are all to be found in one file or another. For instance, your home directory contains a hidden file named .bashrc that contains several of the env variables. Other variables are in other files, mainly located in the /etc directory and its subdirectories. All of the programs that set these variables are run automatically behind the scenes as part of your login actions, thus creating the set of variables that the env command displays.

---

### Post by freedom on 2009-03-05
EVERY variable is stored somewhere and set from some program or script
NONE of them appears magically out of nowhere.
For example, most common thing is to change system locales. 
You can do that by editing values for LANGUAGES and LANG variables in /etc/default/locale
(this is system-wide settings) or you can add variables in .profile file in every user home dir.

---

