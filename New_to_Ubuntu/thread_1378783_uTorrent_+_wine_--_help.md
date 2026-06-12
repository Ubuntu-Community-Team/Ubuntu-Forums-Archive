---
title: "uTorrent + wine -- help??"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by enjoytrees on 2010-01-11
So I went ahead and installed Wine, no problems there, then tried to download uTorrent 1.8.5 from the uTorrent website. Tried to run the program, produced an error message LOOSELY along the lines of: "uTorrent is still running. Close other instances of uTorrent".

Help :(

---

### Post by Nicolas.Perrault on 2010-01-11
Hehe, I'm not particularly experienced with Ubuntu, might even say I'm a newbie. But wouldn't be simpler to use Ktorrent or Transition, two bittorrent clients for KDE and GNOME.? :)

---

### Post by Gen2ly on 2010-01-11
> **enjoytrees said:**
> So I went ahead and installed Wine, no problems there, then tried to download uTorrent 1.8.5 from the uTorrent website. Tried to run the program, produced an error message LOOSELY along the lines of: "uTorrent is still running. Close other instances of uTorrent".

Help :(

Try this from the terminal enjoytrees:

```
ps aux | grep wine
```

and look for 'wine... utorrent'.  If any instances of utorrent/wine are running you'll have to close them first.  You can kill the processes by 'kill PID'.  The PID is what is listed in the second column.

Like the nick, btw ;).

---

### Post by enjoytrees on 2010-01-11
> **Gen2ly said:**
> Try this from the terminal enjoytrees:

```
ps aux | grep wine
```and look for 'wine... utorrent'.  If any instances of utorrent/wine are running you'll have to close them first.  You can kill the processes by 'kill PID'.  The PID is what is listed in the second column.

Like the nick, btw ;).

hehehe thanks :).

Tried "ps aux | grep wine", and it produced the following:

jackson   2032  0.0  0.0   4780  2156 ?        Ss   20:25   0:00 /usr/bin/../lib32/../bin/wineserver
jackson   2037  0.0  0.0 3695412 3276 ?        Sl   20:25   0:00 C:\windows\system32\winedevice.exe MountMgr                                                                              
jackson   2204  0.0  0.0   7336   876 pts/0    R+   20:35   0:00 grep --color=auto wine

It doesn't look like it's open?

---

### Post by daimaru on 2010-01-11
I use utorrent too. since i think its still way better that deluge and all the other stuff. The bug with it already running is since 1.84 or something you have to edit your utorrent shortcut ( -- right click utorrent icon select properties -- ) and add /NOINSTALL to the end of the program properties .

---

### Post by enjoytrees on 2010-01-11
Add /NOINSTALL where? It doesn't seem to have a really good place to add that in its properties. 

At this point I just want to uninstall it all. I tried uninstalling uTorrent, and then Wine, but every time I do that it leaves a folder behind in my Applications menu, with a lone uTorrent icon inside of it.

It looks like this: Applications > Wine (Folder Icon instead of 'Wine' icon) > uTorrent.

I don't want junk files, so please help.

---

### Post by Extract_Here on 2010-01-11
why not just install qbittorrent w/ the synaptic package manager and use it that way you dont have to bother with wine.

---

### Post by lovinglinux on 2010-01-11
Have you tried a native BitTorrent client like Transmission, Deluge or Ktorrent? 

I don't see a good reason to run a closed source Windows application under Wine when you can have excellent open source and native applications for the same task. Deluge and Ktorrent are better than uTorrent IMO.

If you have any difficulties, see [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by enjoytrees on 2010-01-11
Well, I figured out how to remove that stray uTorrent icon from the otherwise empty Wine folder. For those who are curious/have the same problem, do this:

go home> 'your name' directory and then press CTRL + H (show hidden files). 

Click .local > share > applications and then delete the "wine" folder. Worked for me :)

Now, can anyone suggest any native Torrent applications that are a) light, b) awesome, and/or c) heroic? :)

---

### Post by dream_coder on 2010-01-12
Deluge - Grab Latest Version

---

