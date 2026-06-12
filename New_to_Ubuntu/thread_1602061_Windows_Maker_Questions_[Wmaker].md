---
title: "Windows Maker Questions [Wmaker]"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by hovrashko on 2010-10-20
Hello!
 I'm building ubuntu 10.04 from CLI (from the scratch), because i need only essential and efficient distrib, so i decide to go with Windows Maker as GUI, the whole install took about 80 mb, and Firefox for some reason 330 mb, so i having trouble to** get WMaker to autostart, and also auto-login**. So i have read thread about renaming gdm configs to WMaker but i dont have a **gdm**, and i cant effort to have it on that tiny system.  Any help would be appreciated: 
AUTOSTART and AUTO-LOGIN with WINDOWS MAKER,:confused:

Regards,
   Eric

---

### Post by cariboo on 2010-10-20
I used to use gdm when I was running wmaker, but as you say it's a bit on the heavy side. I haven't tried it, but have a look at nodm, it's in the repositories. There is also wdm, also in the repositories.

---

### Post by mcduck on 2010-10-21
One more alternative is to simply configure X to start when you log in to a certain TTY.

For example I have my lightweight Openbox system set up to load X & Openbox when I log in to TTY1. The other TTY's still work as usual, and it really makes no difference to me if I type my user name & password in a pretty GDM window or into the terminal, so I saw no need to running a DM at all. :)

(btw, it's Window Maker, let's leave "Windows" to Microsoft... ;))

---

### Post by hovrashko on 2010-10-28
[SIZE=2]hello, thank for your replays,
   i have figured how to make it work with Blackbox and put the script in /etc/X11/xinit/xinitrc before the gui scrip with "&" to run it in the background, if anybody need details, i can share =)[/SIZE]

---

### Post by ArgusVision on 2010-10-28
This may sound like an odd request, but go ahead and share the details so anyone searching that get's this post later might benefit from a more detailed solution.

---

### Post by bioterror on 2010-10-28
Okay, WMaker (WindowMaker. Yes, we're not making any MS OS's in here!) is my true love of the WM's.

Easiest way is to install Lubuntu or something else with all the needed packages and then install wmaker. LXDM is easy to configure.

If you want to perform some commands when the desktop appears(like nm-applet & gnome-power-manager) you can edit ~/GNUstep/Library/WindowMaker/autostart and add these commands there like this

```

nm-applet &
gnome-power-manager &

```

This makes your wmaker installation suitable for laptop use, you can have a systemtray for the wmaker with wmsystemtray dockapp, which can be found from [http://www.dockapps.org/file.php/id/355]("http://www.dockapps.org/file.php/id/355")

But I would use Lubuntu as base and then build these things, becouse you get a working pcmanfm and lots of other goodies and you can concentrate on wmaker.

If you have anything else in your mind, dont hesitate to ask.

---

### Post by hovrashko on 2010-10-28
[SIZE=2][/SIZE]  [FONT=&quot][SIZE=4]my solution: [/SIZE]
 
 [/FONT]
  *[FONT=&quot]-  sudo apt-get install xinit[/FONT]*
  *[FONT=&quot]- sudo apt-get install xterm[/FONT]*
  *[FONT=&quot]- sudo apt-get install blackbox[/FONT]*
  [I][FONT=&quot]
[/FONT][/I]
*[FONT=&quot]Autologin blackbox[/FONT]*
  *[FONT=&quot]- Edit /etc/rc.local[/FONT]*
  *[FONT=&quot]- Add line “su – yourusername –c startx “  before exit 0[/FONT]*
  [I][FONT=&quot]
[/FONT][/I]
*[FONT=&quot]Startup script[/FONT]*
  *[FONT=&quot]- Edit /etc/X11/xinit/xinitrc before ./xssesion[/FONT]*
  *[FONT=&quot]- Add line “. /myscript &” & - run in background[/FONT]*

[SIZE=3]Make sure to chmod +x yourscript.sh

done. =)
[/SIZE]  [SIZE=3] [/SIZE]

---

### Post by mcduck on 2010-10-28
Here's how I do it:

I just added the following lines to the end of ~/.profile:
```

if [ $(tty) == "/dev/tty1" ]; then
  startx
fi

```

Of course you need to have your WM of choice and all the required stuff for it installed. You *won't* need a DM, though.

edit: I seem to have completely forgotten about the autologin requirement. If you want that, this isn't for you. But still a nice way to handle automatic X without running a DM.

---

### Post by hovrashko on 2010-10-28
> **mcduck said:**
> Here's how I do it:

I just added the following lines to the end of ~/.profile:
```

if [ $(tty) == "/dev/tty1" ]; then
  startx
fi

```Of course you need to have your WM of choice and all the required stuff for it installed. You *won't* need a DM, though.

edit: I seem to have completely forgotten about the autologin requirement. If you want that, this isn't for you. But still a nice way to handle automatic X without running a DM.
  i'd like to try that but where do i find ./profile?

---

### Post by mcduck on 2010-10-28
> **hovrashko said:**
> i'd like to try that but where do i find ./profile?

It's a hidden file in your home directory. "~" is same as your home dir.

---

### Post by hovrashko on 2010-10-29
> **mcduck said:**
> It's a hidden file in your home directory. "~" is same as your home dir.
  ah, thanks =) i didn't pay attention i knew it in home folder but for some reason i was looking for folder ./profile with cd +tab instead of file .profile,  that is why.

---

