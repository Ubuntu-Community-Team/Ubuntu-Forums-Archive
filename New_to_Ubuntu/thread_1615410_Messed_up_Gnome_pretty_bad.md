---
title: "Messed up Gnome pretty bad"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Uzi304 on 2010-11-06
Ok so I'm not entirely sure how it happened but my Gnome is very messed up. Everytime I boot into it, the panels are gone and the icons keep moving up and down and a dialog box flashes and the dialog box says that there was a problem loading OAFIID:GNOME_FastUserSwitchApplet or something and it asks to delete it or not. I want to delete it but the dialog box won't stay on for long enough for me to click delete and even when I do, it makes no difference. I've looked around and I've found nothing that's relevant to my situation. Any help would be greatly appreciated.

---

### Post by Tharkun on 2010-11-07
What version of Gnome are you using?

Perhaps you can reinstall Gnome using the Terminal?

---

### Post by Uzi304 on 2010-11-07
I'm using 2.32 but I just deleted the ~/.gconf folder and redid my settings without the user switter applet in my panel so it's working for now

---

### Post by Gone fishing on 2010-11-07
Try making another user account. Alt Control F1 login then ```
sudo useradd newuser
``` then ```
sudo passwd newuser
```

Restart then can you login to the newuser if you can gnome is OK and you probably just need to delete the .compiz from you home directory. You can do that from the terminal using the rm command

---

### Post by Uzi304 on 2010-11-07
Ok so the problem still occurs even when I don't use the fast user switcher applet thing. The icons just keep shifting up and down in place and the panels disappear. I created a new user and from what I saw, the problem did not occur and I deleted my .compiz folder and the problem still occurs in my normal user.

---

### Post by Uzi304 on 2010-11-07
Or if anyone doesn't have a practical solution, can anyone tell me where I can find the Gnome and Compiz files throughout myystem so I can delete them all and install them both fresh

---

### Post by Crusty Old Fart on 2010-11-07
This may be the easiest way out of the mess. Know that I'm not an expert here, just offering it as a suggestion that you may want to consider. Use at your own risk.
Ref's.: man apt-get, man dpkg

For Gnome:
```

sudo apt-get purge gdm
sudo apt-get install gdm

```For Compiz:
```

sudo apt-get purge compiz
sudo apt-get install compiz

```And just for good measure:
```

sudo apt-get install -f
sudo dpkg --configure -a

```

---

### Post by RJ12 on 2010-11-07
> **Crusty Old Fart said:**
> This may be the easiest way out of the mess. Know that I'm not an expert here, just offering it as a suggestion that you may want to consider. Use at your own risk.
Ref's.: man apt-get, man dpkg

For Gnome:
```

sudo apt-get gdm purge
sudo apt-get install gdm

```For Compiz:
```

sudo apt-get compiz purge
sudo apt-get install compiz

```And just for good measure:
```

sudo apt-get install -f
sudo dpkg --configure -a

```

Shouldn't be? 
```
sudo apt-get purge gdm
```
```
sudo apt-get purge compiz
```

If not, I think it gives an error like "Invalid Operation gdm(or compiz)"

---

### Post by JustinR on 2010-11-07
You all don't need to uninstall the programs - just the configuration files:

```

rm -r .gconf
rm -r .gconfd

```

---

### Post by Crusty Old Fart on 2010-11-07
> **RJ12 said:**
> Shouldn't be? 
```
sudo apt-get purge gdm
``````
sudo apt-get purge compiz
```If not, I think it gives an error like "Invalid Operation gdm(or compiz)"
Yup, RJ12, you're exactly right. I read the man page wrong, damnit.

Going back to correct my post now.

Thank you for spotting my errors.

Crusty

---

### Post by Crusty Old Fart on 2010-11-07
> **JustinR said:**
> You all don't need to uninstall the programs - just the configuration files:

```

rm -r .gconf
rm -r .gconfd

```

Justin, hope you don't mind me picking your brains here. I have the following questions:

[LIST=1]
[*]How did you learn where the Gnome configuration files are?
[*]I'm assuming the ones you listed are in the user's home directory (~). Is that right?
[*]Are there any "other" configuration files for Gnome, like maybe system wide ones floating around in /etc or maybe somewhere else?
[*]I assume that when apt-get purge is used, that it removes ALL configuration files for the named package, whether they exist in ~ or anywhere else in system directories. Is this assumption correct?
[/LIST]
I'd be grateful if you would answer any of these questions and skip the ones for which you don't know the answers.

Thanks in advance for educating me,

Crusty

---

### Post by Uzi304 on 2010-11-07
I've deleted the ~/.gconf and ~/.gconfd files and that didn't solve anything but I'll try the purge thing

---

