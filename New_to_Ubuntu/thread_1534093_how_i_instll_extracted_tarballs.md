---
title: "how i instll extracted tarballs??"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by cyanide0007 on 2010-07-19
i've downloaded XBMC-9.11.tar.gz file yesterday and i extracted it in to my desktop.
i read all details given under READ ME file and i tried to install XBMC-9.11,but it not getting installed.What have to do now.Plz help me????
tell me all steps to be followed in detail, since  am very new to LINUX don't know to many COMMANDS


plz#-o

---

### Post by JustinR on 2010-07-19
Hi, this will install XBMC easier than it would with a tarball:

**Applications > Accessories > Terminal**
```

sudo apt-get install python-software-properties pkg-config
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone
sudo apt-get update

```

If you use VDPAU (If you dont' know what this is just skip it)
```

sudo apt-get install libvdpau1 nvidia-185-libvdpau

```

Have fun.

ps. This was straight from there download site ([www.XBMC.org/downloads](www.XBMC.org/downloads)) then click Linux.

---

### Post by Legendary_Bibo on 2010-07-19
Here I turned what JustinR posted into a script to do the process for you.

After downloading it, right click on it and go properties then click on the permissions tab and there should be a checkbox that says "allow executing of this file" click it and close the properties window. Now double click on the shell script (xbmc.sh) and when the box comes up click on "run in terminal". You'll have to enter your password and it should run.

---

### Post by JustinR on 2010-07-19
> **Legendary_Bibo said:**
> Here I turned what JustinR posted into a script to do the process for you.

After downloading it, right click on it and go properties then click on the permissions tab and there should be a checkbox that says "allow executing of this file" click it and close the properties window. Now double click on the shell script (xbmc.sh) and when the box comes up click on "run in terminal". You'll have to enter your password and it should run.

After you've done all that it would have been easier just to run the commands them selves!:lolflag:

---

### Post by Legendary_Bibo on 2010-07-19
> **JustinR said:**
> After you've done all that it would have been easier just to run the commands them selves!:lolflag:
Some people prefer clicking stuff. :D Besides he'd have to individually copy and paste or type in each command. I like making shell scripts.

I wonder though, if I set a shell script to execute and then attach it for someone to use will it still be set to execute? :-k

---

### Post by Paqman on 2010-07-19
> **JustinR said:**
> /code]

If you use VDPAU (If you dont' know what this is just skip it)
```

sudo apt-get install libvdpau1 nvidia-185-libvdpau

```


Just to expand a little, if you want smooth playback of HD video, you'll want this. 

After installing the above packages (you might want to use nvidia-current instead of nvidia-185-libvdpau) you'll need to go into XBMC's settings and swithc the video rendering from "auto" to "vdpau".

---

### Post by Paqman on 2010-07-19
Dp

---

