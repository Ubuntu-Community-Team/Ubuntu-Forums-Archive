---
title: "reconfiguring X"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by knightofthesun on 2010-11-03
I am not new to ubuntu, but I have no experience with display issues or Xorg.

I upgraded to 10.04 and was messing around to make the machine headless. Now the display is messed up - it begins to displays the login screen but then flashes to gray. The text in the other terminals is haywire also.

In recovery mode, graphical failsafe mode does not work either (an error about dri). sudo dpkg-reconfigure xserver-xorg does nothing. I don't even seem to have an xorg.conf file anyways.

Unfortunately, reinstalling Ubuntu is not an option.

1. This thread about reconfiguring X [[link]]("http://ubuntuforums.org/showthread.php?t=690760") says that it no longer works. Is there another thread I should look at? I'm tired of searching.

2. Or, how else can I start to figure out how to fix my problem? I don't have specific error messages to pursue, other than the dri one that I don't understand.

3. Do I need to be looking into my gpu drivers or anything like that? (Intel Corporation 82G33/G31 Express Integrated Graphics Controller)

---

### Post by bioterror on 2010-11-03
A small guidance for creating a xorg.conf.new
```

ctrl+alt+f1 (just to get us to the tty)
login (enter your credentials)
sudo service gdm stop
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo gdm start
ctrl+alt+f7 (if it doesnt work [usually does], f8 then)

```

Now you should have a xorg.conf there, but it might need some tweaking if it doesnt work out of the box.

Telling your graphics cards vendor and model could help us a little bit more.

---

### Post by knightofthesun on 2010-11-03
> **bioterror said:**
> A small guidance for creating a xorg.conf.new
```

ctrl+alt+f1 (just to get us to the tty)


```



Right, so I can drop to tty but the display is messed up there as well. It displays a sliver of the text about 500 times on the screen. I guess I was unclear.

The only way I can get to a usable terminal is if I boot into failsafe mode and cancel out (I can't use netroot - don't know the root password. does Ubuntu even have a root password?). Or over ssh.

---

### Post by bioterror on 2010-11-03
> **knightofthesun said:**
> Right, so I can drop to tty but the display is messed up there as well. It displays a sliver of the text about 500 times on the screen. I guess I was unclear.

The only way I can get to a usable terminal is if I boot into failsafe mode and cancel out (I can't use netroot - don't know the root password. does Ubuntu even have a root password?). Or over ssh.

You can "enable" root by giving this command in terminal: sudo passwd root
And put your desired password for the root account.

---

### Post by knightofthesun on 2010-11-03
> **bioterror said:**
> A small guidance for creating a xorg.conf.new
```

ctrl+alt+f1 (just to get us to the tty)
login (enter your credentials)
sudo service gdm stop
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo gdm start
ctrl+alt+f7 (if it doesnt work [usually does], f8 then)

```

Now you should have a xorg.conf there, but it might need some tweaking if it doesnt work out of the box.

Telling your graphics cards vendor and model could help us a little bit more.

Well, you're right, now I have an xorg.conf. But nothing has changed.

Also, from lspci:
VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

---

### Post by bioterror on 2010-11-04
> **knightofthesun said:**
> Well, you're right, now I have an xorg.conf. But nothing has changed.

Also, from lspci:
VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

I made some googling and if the xserver-xorg-video-intel packet does not provide working drivers, we might xserver-xorg-video-vesa use this one and hope that get working graphics.

I think those VESA drivers are worth of try, even tho there's no 3D.

---

