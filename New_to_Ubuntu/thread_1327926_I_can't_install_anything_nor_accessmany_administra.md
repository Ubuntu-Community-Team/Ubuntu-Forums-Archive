---
title: "I can't install anything nor accessmany administrator options"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by mappo123 on 2009-11-15
hey,

I just intalled the latest Ubuntu OS on my laptop as dual boot. but I am having problems installing anything as well as accessing some of the options in system/administrator. I get this error:

failed to run computer-janitor-gtk as user root
unable to copy the user's Xauthorization file.

Whenever i try and install something i.e. wine... this is what i get:

mappo@poohbear:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
mappo@poohbear:~$ 

I've done the previous steps properly and that works fine, until i get here.

And when I try to install a program through the Ubuntu software centre, i push install button, but nothing happens... :S hopefully you guys can help 

Thanks in advance.

---

### Post by ArinSky on 2009-11-15
have you tried working out of a superuser terminal?

---

### Post by mappo123 on 2009-11-15
no and i'm not sure what you mean by that...? i'm new to ubuntu

---

### Post by ArinSky on 2009-11-15
gksu gnome-terminal... similar to using sudo. Probably not the problem but also best to rule it out. 

It almost seems like you're missing something... try repairing your installation through the boot cd?

What else have you installed or tried to install? was there anything that worked at all?

---

### Post by Locke_99GS on 2009-11-16
```

sudo apt-get -f install
sudo apt-get update
sudo apt-get install wine

```

---

