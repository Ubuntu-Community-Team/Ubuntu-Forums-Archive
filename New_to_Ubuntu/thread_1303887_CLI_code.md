---
title: "CLI code"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by HHooman on 2009-10-28
Hi
I have a GUI ubuntu installed, where can i see what are the CLI codes for any changes in GUI mode ?

---

### Post by OpenGuard on 2009-10-28
GUI is **NOT** CLI .. You can't view something that might not even exist.

---

### Post by Iowan on 2009-10-28
Some information might be available via GUI or CLI (like hostname or IP address). What information/codes/changes do you seek?

---

### Post by lavinog on 2009-10-28
this might give you some information:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by HHooman on 2009-10-29
> **Iowan said:**
> Some information might be available via GUI or CLI (like hostname or IP address). What information/codes/changes do you seek?
 
i am new to linux, i need GUI to config some items , i have a remote server with only ssh account, i have installed gnome and vnc4server, i can't access it, thats because from GUI first i shoud login which is not possible and then vnc would be available, i am tring to make changes for autologin and also in vnc config i need to disable " ask for you confirmation each access to this machine "
 
appriciate your help

---

### Post by lavinog on 2009-10-29
take a look at the server guide when you have some time:
[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

you might want to enable x11forwarding in ssh and run your gui apps via ssh instead of vnc.
:looking for x11forwarding reference:
update: the documentation servers seem to be experiencing some capacity issues. Probably due to the release of karmic. I will try again later

---

### Post by nothingspecial on 2009-10-29
When I want to use a gui on a remote computer but I don`t know the command to launch it I go system > preferences > main menu and find the app in there. If you click properties then it will tell you the command to launch it.

Then ssh with the -X argument and away you go eg

```
ssh -X user@ipaddress
```

---

### Post by Bölvaður on 2009-10-29
> **lavinog said:**
> take a look at the server guide when you have some time:
[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

**you might want to enable x11forwarding in ssh** and run your gui apps via ssh instead of vnc.
:looking for x11forwarding reference:
update: the documentation servers seem to be experiencing some capacity issues. Probably due to the release of karmic. I will try again later

look at this.
vnc isnt secure so use ssh instead. There is no need for admins to use any gui so by default there isnt any. but you can have it by tunneling x to the remote host for the programs you have open.

x11forwarding



if you really want to use vnc then you can. the best way is to install it, forward the port and make some password. Now all you have to do is log in via terminal (probably some gui tool available but having a launcher with the command is so much simpler). insert the pass and you're in.

---

### Post by HHooman on 2009-10-29
> **nothingspecial said:**
> When I want to use a gui on a remote computer but I don`t know the command to launch it I go system > preferences > main menu and find the app in there. If you click properties then it will tell you the command to launch it.
 
Then ssh with the -X argument and away you go eg
 
```
ssh -X user@ipaddress
```
 
thanks for your help, that was exactly what i wanted 
but in my case i found the command and they are 
1- gksu /usr/sbin/gdmsetup
2- vino-preferences
when i run these commands from ssh terminal i get this 
(gksu:4642): Gtk-WARNING **: cannot open display:
(vino-preferences:4643): Gtk-WARNING **: cannot open display:
please help ?

---

### Post by Bölvaður on 2009-10-29
x11forwarding has already been mentioned

---

### Post by lavinog on 2009-10-29
here is some information on x11forwarding:
[https://wiki.ubuntu.com/marckaplan/ssh/X11forwarding](https://wiki.ubuntu.com/marckaplan/ssh/X11forwarding)

to edit files in the command line you can use **nano** and used **ctrl-x** to save and exit.  (Use **sudo nano** in this case)

---

