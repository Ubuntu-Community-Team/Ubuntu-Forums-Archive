---
title: "Firefox and Flash"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by jworrin on 2009-05-25
First off, I am not sure if this is really the place for this question, but hopefully it is.  Also, I figured this question would already have been answered, but I have search on this forum and others and not really found any good info.  

Ok, on to my problem.  I just installed ubuntu, and I can not get flash working correctly.  Some web sites that use flash work just fine, youtube for instance, then others don't, myspace's music player, ninjakiwi...  I tried to upgrade to flash 10 by downloading the flash10.deb package and installing it, but when I type about:plugins into firefox, it says that I am still using flash 9.0 r999.  I have tried a number of things, sudo apt-get remove --purge flashplugin-nonfree and then sudo dpkg -i install_flash_player_10_linux_deb.  This and others did not work.  My brothers laptop that I put Ubuntu on is doing the exact same thing.  

Any help would be greatly appreciated.

-- Joshua

---

### Post by whoop on 2009-05-25
Flash has always been a bit buggy for me. Restarting firefox always fixes it. It still sucks. Are you running 64bit?

---

### Post by clhsharky on 2009-05-25
Try installing VLC and VLC-Mozilla plugin and unistall Totem-Mozilla plugin.
VLC can play all most any format.
BTW what version of Ubuntu are you using.

---

### Post by Bradtek on 2009-05-25
Have you read / followed this 
Complete Streaming, Multimedia & Video How-to 

[http://ubuntuforums.org/showthread.php?t=661833&highlight=streaming](http://ubuntuforums.org/showthread.php?t=661833&highlight=streaming)

---

### Post by drs305 on 2009-05-25
If this is a 64-bit system, try downloading the Flash 10 alpha tar.gz file directly from Adobe. Make sure you have removed all flash packages.
Download the file:
```

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

```

Extract the libflashplayer.so file and copy it to ~/.mozilla/plugins (Make the folder if it doesn't exist). Restart Firefox. Some users also copy it to /usr/lib/mozilla/plugins although I haven't found that necessary.

That may be all you have to do.

---

### Post by presence1960 on 2009-05-25
For a really simple Flash install for 64 bit go here to Ubuntu Forums x86-64 Users section : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by asmoore82 on 2009-05-25
Flash 9.0.999 is the Gnash Project's Free Software replacement for Adobe's nonfree Flash plugin

I'm quite impressed with how far it has come, works great with youtube as you said ...
to change to the official non-free flash package(after installing it of course) you have to use Debian's "Alternatives" system:

```
sudo update-alternatives --config xulrunner-flashplugin
sudo update-alternatives --config xulrunner-addons-flashplugin
```

for a complete list of which components have alternatives, see the names of shortcuts under "/etc/alternatives"

you can see what's available and what's selected with this(no sudo required):
```
update-alternatives --display *<functionality_name>*
```
for example, another popular one with many alternatives is java plugins:
```
update-alternatives --display xulrunner-1.9-javaplugin.so
```

---

### Post by lovinglinux on 2009-05-25
I don't want to be rude, but c'mon people. I know everyone is trying to help, but VLC has nothing to do with flash plugin, the OP doesn't mention 64bit, he already installed the flash deb file, and what is all about those complicated commands?

The OP clearly has a conflict between two flash plugins, which needs to be removed.

Run this command, restart Firefox and check if it works.

```
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

Alternatively, you could install ubuntu-restricted-extras

[Here](http://ubuntuforums.org/showthread.php?t=1029148) you find a similar thread about this issue.

---

### Post by presence1960 on 2009-05-25
> **lovinglinux said:**
> I don't want to be rude, but c'mon people. I know everyone is trying to help, but VLC has nothing to do with flash plugin, the OP doesn't mention 64bit, he already installed the flash deb file, and what is all about those complicated commands?

The OP clearly has a conflict between two flash plugins, which needs to be removed.

Run this command, restart Firefox and check if it works.

```
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

Alternatively, you could install ubuntu-restricted-extras

[Here](http://ubuntuforums.org/showthread.php?t=1029148) you find a similar thread about this issue.

when someone neglects to say whether they are running 32 or 64 bit should I assume 32 bit? c'mon?

---

### Post by clhsharky on 2009-05-25
Your right about flash, but the music player he was referring to isn't flash. You need a player plugged into Firefox like Totem. VLC or Mplayer. Totem cant play all that VLC can, and VLC works fine on that site.

---

### Post by james_mcl on 2009-07-11
I've just fixed a problem where some Flash stuff (Myspace) didn't work, and some (Youtube) did.

Could I suggest, for the reasons detailed in my post at [http://ubuntuforums.org/showpost.php?p=7600753&postcount=2](http://ubuntuforums.org/showpost.php?p=7600753&postcount=2), closing your browser, deleting ~/.macromedia, then trying again?

HTH,

James.

---

