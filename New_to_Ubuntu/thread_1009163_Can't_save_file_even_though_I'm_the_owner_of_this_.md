---
title: "Can't save file even though I'm the owner of this laptop..."
date: 2008-12-12
forum: New to Ubuntu
---

### Post by FountainDew on 2008-12-12
Hi, I'm trying to get my wireless working on Ubuntu but its being a pain. I'm trying to blacklist "ath_pci" in favor of madwifi-tools. But when I save the blacklist file under modprobe.d/blacklist, it says "you are not the owner." What gives?

---

### Post by perspectoff on 2008-12-12
I can already tell you are using somebody's over-complicated instructions for installing an Atheros wireless card.

Installing an Atheros card is extremely easy.

See the instructions at UbuntuGuide ([http://ubuntuguide.org](http://ubuntuguide.org))

or Kubuntuguide (http:// kubuntuguide.org).

---

### Post by gettinoriginal on 2008-12-12
you may own the laptop LOL, but sudo owns the system.  you may have to save the blacklist as root.

---

### Post by Flynn555 on 2008-12-12
just save it to your desktop and then in open terminal and type 
```
sudo nautilus
```

then you can just drag and save it where ever you want....


edit:  you could just 

save it to your desktop then open terminal and type
```
 sudo cp ~/Desktop/yourfile.ext /path/where/you/want/to/save/yourfile.ext 
```

---

### Post by Paqman on 2008-12-12
Files outside of your /home directory aren't owned by you, they're owned by "root". This is a security feature.

You can gain root privileges temporarily using the command sudo (for the CLI) or gksu (for graphical apps). So to edit a file outside of /home you could launch it with:
```

gksu gedit /path/to/file

```

Or you could just install nautilus-gksu, which will let you do this from a right-click.

---

### Post by FountainDew on 2008-12-12
Thanks for all the replies, I got it to work! But still, I don't get who this "sudo" being is, why is he or she so all-powerful?

> **perspectoff said:**
> I can already tell you are using somebody's over-complicated instructions for installing an Atheros wireless card.

Installing an Atheros card is extremely easy.

See the instructions at UbuntuGuide ([http://ubuntuguide.org](http://ubuntuguide.org))

or Kubuntuguide (http:// kubuntuguide.org).

You guessed correct, and thank you for this link! Its much simpler than combing thread-after-thread for more info. Unfortunately it did not work for me, although on my first ubuntu install it did work. So I'm re-installing Ubuntu 8.10 for the third time and re-trying this guide!

---

### Post by oldos2er on 2008-12-12
"sudo nautilus"

 Please use "gksu nautilus" instead.

---

### Post by Duck2006 on 2008-12-12
[http://www.psychocats.net/ubuntu/security#sudomoreinfo](http://www.psychocats.net/ubuntu/security#sudomoreinfo)

---

### Post by Paqman on 2008-12-12
> **FountainDew said:**
> Thanks for all the replies, I got it to work! But still, I don't get who this "sudo" being is, why is he or she so all-powerful?


Sudo means: **S**uper **U**ser **DO**

Normally system files are owned by the system, not the users. That stops anything the users (or malware pretending to be a user) from affecting the system. It's one of the main things that makes Linux so resistant to viruses and the like.

Sudo temporarily turns you into a super user, with enough rights to change the system files. That's why you get asked for your password: it's very important that the system authenticates you as a real human user and not a virus before it lets you change system files.

---

