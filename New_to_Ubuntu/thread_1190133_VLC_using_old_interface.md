---
title: "VLC using old interface"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-06-17
I'm using 9.04 and when I installed VLC, I noticed that the interface had changed from the regular Gnome one in 8.10 to an older looking interface. 

Here's a picture showing the VLC interface and what Totem looks like. Totem uses all of the regular colors that my theme uses but VLC is gray. 
[IMG]http://i93.photobucket.com/albums/l41/buck3tph0t0/VLCGUIandTotem.png[/IMG]

Is there a way to change it back so it looks normal?

---

### Post by treesurf on 2009-06-17
If you go to this link ( [http://www.videolan.org/vlc/skins.php](http://www.videolan.org/vlc/skins.php) ) you can download different skins to make VLC look however you like.

---

### Post by ricardofilipemoreira on 2009-06-17
> **Sup3r3g0 said:**
> I'm using 9.04 and when I installed VLC, I noticed that the interface had changed from the regular Gnome one in 8.10 to an older looking interface. 

Here's a picture showing the VLC interface and what Totem looks like. Totem uses all of the regular colors that my theme uses but VLC is gray. 
[IMG]http://i93.photobucket.com/albums/l41/buck3tph0t0/VLCGUIandTotem.png[/IMG]

Is there a way to change it back so it looks normal?
vlc uses QT4 and gnome uses GTK+ for the decoration. go to the gnome menu, find the item QT4 settings and change the theme there to whatever you like. if you use the gtk QT theme vlc will look like any gnome application

---

### Post by Sup3r3g0 on 2009-06-17
Thanks! I didn't know that about VLC

---

### Post by ceciliaFX on 2009-06-21
> **treesurf said:**
> If you go to this link ( [http://www.videolan.org/vlc/skins.php](http://www.videolan.org/vlc/skins.php) ) you can download different skins to make VLC look however you like.
and when I have gone there to download a skin I'm told I don't have permission to write to /share/vlc/skins2

and the system doesn't ask me for the password like it does for other processes that require 'root' access.

I'm not a typer, I'm an artist. call me crazy, I like using GUI's.

what are the magic words to copy a skin to that location?

(this, btw, is one of the few things that **REALLY** pisses me off about linux. I shouldn't have to go through hoops to do something SO simple as copy a freaking skin)

---

### Post by paulderol on 2009-06-21
i understand that this issue may grind your gears a bit, but the benefit of being able to load software written under several different platforms all within one system is quite beneficial, even if certain tweaks are more than one desired to do. Qt is a whole development scheme, as is Gtk, and they may run side by side, although they are massively different. KDE uses the former, and Gnome the latter, each being able to load the others libraries with some design flubbing by the host environment.

to use the directory you seek, open a terminal and type

```
sudo chmod 666 /share/vlc/skins2
```

it will make it possible to write to that folder without doing much else. 

it should ask you for your password when you use sudo, which is the request for root access. other programs have it as part of their natural motion, vlc apparently doesnt.

---

### Post by ceciliaFX on 2009-06-21
thanks for that info. And I get that Ubuntu is set up this way because It's a Good Thing, but it's still annoying.

I found another solution (looking at the forums on the vlc site) and i figure i might as well share it here for whomever wants it.

apparently there is another location one can use for vlc skins:

/home/cecilia/.local/share/vlc/

Obviously, your home name will not be "cecilia", but I'm sure you get the idea.

I have always set up my system to see hidden files - even windows - as I hate the whole microsoft notion that computer users are morons. even if it happens to be true in many cases. haha

so, one places the skin one wants in that directory as there's no issues with permissions, goes into the vlc prefs and where it lists the location of the skins, add that folder. save, restart vlc...you are good to go.

---

### Post by 3rdalbum on 2009-06-21
> **ceciliaFX said:**
> and when I have gone there to download a skin I'm told I don't have permission to write to /share/vlc/skins2

and the system doesn't ask me for the password like it does for other processes that require 'root' access.

(this, btw, is one of the few things that **REALLY** pisses me off about linux. I shouldn't have to go through hoops to do something SO simple as copy a freaking skin)

Think about it: If it was easy for a normal user account to copy a skin to a system-wide directory, it would also be easy for a normal user account to copy an infected file into the VLC skins, and compromise all user accounts when they try to run VLC. Nobody wants that.

In this case you've done a bit of a mini-rant without seeking out ways to make things easier for yourself! Skins for VLC can be inserted into your home directory: ~/.local/share/vlc  which does not require you to become root.

The other option, to get the theme to work for all users on the computer, is to install the "nautilus-gksu" package. After your next login, you will be able to right-click a folder or file and choose "Open as Administrator". So, go to /usr/share/vlc and right-click "skins2", and choose Open As Administrator. Copy your skin in there.

That's actually what's so good about Linux: It puts walls in the way of security threats, but for real users with privileges they become mere anthills.

---

