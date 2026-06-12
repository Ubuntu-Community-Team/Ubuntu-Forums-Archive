---
title: "How do I update the machine name?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by AnimalMagic on 2009-03-18
In 8.10, how do I change the machine name? I have cloned a machine, but cannot find where to give it a different name...

---

### Post by taurus on 2009-03-18
You need to edit both /etc/hostname & /etc/hosts.  Make sure you use the same name in both or you won't be able to use sudo anymore.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/hostname /etc/hosts
```

---

### Post by AnimalMagic on 2009-03-18
Thanks,

Seems a bit retro to have removed it from a GUI edit... But now I know... :-)

---

### Post by dmaxel on 2009-03-30
OK, I found the places, and its easy to change hostname, but what about the hosts file? there are three different places where ubuntu shows up (machine default name). Which do I change there?

What I mean is which of these do i change, when the machine name is currently ubuntu?
```
127.0.0.1       localhost
127.0.0.1       ubuntu.ubuntu-domain    ubuntu
```

---

### Post by asmoore82 on 2009-03-30
> **taurus said:**
> You need to edit both /etc/hostname & /etc/hosts.  Make sure you use the same name in both or you won't be able to use sudo anymore.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/hostname /etc/hosts
```

[SIZE="5"][COLOR="Red"]***Yikes!!***[/COLOR][/SIZE]

you will most likely want to change your hostname through the GUI tools -
it would be under Network preferences -
**especially** if you have multiple location profiles

the NetworkManager Daemon will not honor or preserve manual changes!
(this is the big difference between modern "Desktop" and "Server"
Linuxes - the NetworkMaganer should never be installed on "Servers")

---

### Post by dmaxel on 2009-03-30
> **asmoore82 said:**
> [SIZE=5][COLOR=Red]***Yikes!!***[/COLOR][/SIZE]

you will most likely want to change your hostname through the GUI tools -
it would be under Network preferences -
**especially** if you have multiple location profiles

the NetworkManager Daemon will not honor or preserve manual changes!
(this is the big difference between modern "Desktop" and "Server"
Linuxes - the NetworkMaganer should never be installed on "Servers")
Where would I find this? I'm using Ubuntu 8.10.

---

### Post by Halfling Rogue on 2009-04-23
It's found under your Administrative tools, in Networks. Just browse through the tabs and you should find a field that will let you change your host name. Keep in mind that you'll need to reboot right after you do, because you can't launch any applications once it's changed. :)

---

### Post by dmaxel on 2009-04-27
> **Halfling Rogue said:**
> It's found under your Administrative tools, in Networks. Just browse through the tabs and you should find a field that will let you change your host name. Keep in mind that you'll need to reboot right after you do, because you can't launch any applications once it's changed. :)Sorry, but I don't see this in 8.10. There is only Network Tools in the Administration menu, but that's it. And in Preferences it's only Network Connections, which doesn't change the machine name either.

---

### Post by Iowan on 2009-04-27
There's still the tried/true method **Taurus** mentioned (although I'd probably use **nano**) ;)

---

### Post by llamabr on 2009-04-27
Yes, it would be much simpler just to edit the files yourself.

```
sudo /etc/hostname 
```

and then

```
sudo nano /etc/hosts
```

Make sure the name you change to is the same.

---

### Post by Halfling Rogue on 2009-05-01
> **dmaxel said:**
> Sorry, but I don't see this in 8.10. There is only Network Tools in the Administration menu, but that's it. And in Preferences it's only Network Connections, which doesn't change the machine name either.

That's odd. I've got an updated version of 8.04 and it's in my Administration under Network. Maybe you need to add it to your menu? I can also get to it by left-clicking on my internet icon on the taskbar and clicking 'Manual Configuration', then going to the General tab.

---

