---
title: "My Wireless Won't work on Ubuntu"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by OverFjell on 2007-10-02
I recently got Ubuntu, but I can't seem to connect to the internet with it, I'm using a "linksys WRT54GS" model, and was wondering if anyone had the same problem as me, and if they could help with the solution, any help would be greatly appreciated.

---

### Post by renzokuken on 2007-10-02
is that the router? i use that perfectly at home.

the problem will be with your wireless chipset in your pc/laptop.

run ```
lspci -v
```  and see if you can find out what wireless card/chipset you have

---

### Post by OverFjell on 2007-10-02
I'm pretty bad with computers, so I'm trying to learn, but I tried running "lspci -v" and my PC (Currently running on Windows, because of the lack of internets on Ubuntu) said it cannot find "lspci"

---

### Post by renzokuken on 2007-10-02
that command only works in linux,

you should be able to find out your wireless chipset in windows through Device Manager

Right click My Computer -> Properties -> Hardware -> Device Manager

---

### Post by MongooseCage on 2008-05-02
> **renzokuken said:**
> is that the router? i use that perfectly at home.

the problem will be with your wireless chipset in your pc/laptop.

run ```
lspci -v
```  and see if you can find out what wireless card/chipset you have


Dude, I ran your code because my wifi doesnt work as well. I know mine is the ipw3945 but it doesnt work at all.

So this is what i got:
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945BG Network Connection
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at edf00000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```

What do I do? I think this is the breaking edge of my problem so really please help me!! I would be extremely grateful if you can tell me whats the issue with "access denied" and this entire mess!

---

### Post by renzokuken on 2008-05-02
hi mongoose, it may be that you are using the wrong driver......have a look here for how to switch from the old troublesome ipw3945 to the newer better iwl3945

[http://ubuntuforums.org/showthread.php?t=636177](http://ubuntuforums.org/showthread.php?t=636177)

basically, add ipw3945 to your blacklist file and iwl395 to your modules file, reboot and see if it works

this is another goo place to look too [http://ph.ubuntuforums.com/showthread.php?t=759759](http://ph.ubuntuforums.com/showthread.php?t=759759)

---

### Post by MongooseCage on 2008-05-02
> **renzokuken said:**
> hi mongoose, it may be that you are using the wrong driver......have a look here for how to switch from the old troublesome ipw3945 to the newer better iwl3945

[http://ubuntuforums.org/showthread.php?t=636177](http://ubuntuforums.org/showthread.php?t=636177)

basically, add ipw3945 to your blacklist file and iwl395 to your modules file, reboot and see if it works

this is another goo place to look too [http://ph.ubuntuforums.com/showthread.php?t=759759](http://ph.ubuntuforums.com/showthread.php?t=759759)

So wait, i tried searching ipw3945 on my computer and I don't seem to be able to find it. I did though went to [http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download")

This package is supposed to give me all the right modules for the drivers. But i ran into this problem of

```
  mongoose@The-Heron:~/Desktop/compat-wireless-2008-05-02$ sudo make load
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1 
```

Then I was suggested to
```
 $ sudo /etc/init.d/networking stop 
```

On the same post i was told if that didnt work I was to put cfg80211 module into the black list. So I seem to have found some from trackerd using 'cfg80211' as the search term in the 'file system':
```

cfg80211.ko
cfg80211.h
cfg80211.h

```
 
So which of them do I suppose I put into that 'blacklist' file?

---

### Post by MongooseCage on 2008-05-02
i mean 'So which of them do you suppose I put into that 'blacklist' file?

---

### Post by renzokuken on 2008-05-02
first off a bit of an explanation. ipw3945, iwl3925, cfg80211 are what are known as kernel **modules**. to blacklist a module, simply open up the blacklist file in a text editor i.e.

```
gksudo gedit /etc/modules.d/blacklist
```

and add the module name to the end of the file (i.e. literally write **cfg80211** on a new line at the bottom of the file. save and close.

similarly to enable a module, write the modules name at the end of the modules file

```
gksudo gedit /etc/modules
```

reboot for the settings to take effect.

so don't do the cfg80211 thing (that just installs modules that are already available in ubuntu so i wouldnt bother), open up your blacklist file and put **ipw3945** at the end, save and close, then open up your modules file and put **iwl3945** at the end, save and close.

reboot.

this will stop ipw3945 from being loaded and load the newer iwl3945 instead

good luck

---

### Post by MongooseCage on 2008-05-02
> **renzokuken said:**
> first off a bit of an explanation. ipw3945, iwl3925, cfg80211 are what are known as kernel **modules**. to blacklist a module, simply open up the blacklist file in a text editor i.e.

```
gksudo gedit /etc/modules.d/blacklist
```

and add the module name to the end of the file (i.e. literally write **cfg80211** on a new line at the bottom of the file. save and close.

similarly to enable a module, write the modules name at the end of the modules file

```
gksudo gedit /etc/modules
```

reboot for the settings to take effect.




so don't do the cfg80211 thing (that just installs modules that are already available in ubuntu so i wouldnt bother), open up your blacklist file and put **ipw3945** at the end, save and close, then open up your modules file and put **iwl3945** at the end, save and close.

reboot.

this will stop ipw3945 from being loaded and load the newer iwl3945 instead

good luck

Ok i tried that, it yet doesnt work, I think now I know what I am doing. But honestly, I tried searching if there were ipw3945 drivers using trackerd. I could find none suprisingly, I dont have the drivers, I do have the iwl3945 drivers that I had installed from the link successfully. So I think the question is, how do I get them to run? Because my hardware is recognized, I realized that there was no ipw3945 module, and now I have iwl3945. I am supposed to be set. There must be something stupid I am doing...

---

