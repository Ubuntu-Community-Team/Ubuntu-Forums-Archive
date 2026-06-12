---
title: "Network Share Issue"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by sideffects on 2009-05-16
I dualboot Ubuntu and Windows Vista, and today I booted up Vista to use Visio. I then shut down and loaded Ubuntu and logged in. I have a few shared network folders and it seems that everytime i reboot my computer the share option that reads "Allow other people to Write in this folder" is unchecked. So, everytime I boot up Ubuntu I have to recheck that box. Does anybody know what is going on here?

---

### Post by mprince on 2009-05-16
If you don't mind editing your smb.conf file... you can define shares there and it will stay writable.

Open a terminal and type:

```
sudo gedit /etc/samba/smb.conf
```

Put the following at the bottom of the file (In the Share Definitions part). Replace everything that is in bold with the name of your share & appropriate path.

*note* you may not need the green options

```
[**ShareName**]
path = **/path/to/your/share**
available = yes
writeable = yes
browseable = yes
guest ok = yes
[COLOR="SeaGreen"]inherit permissions = yes
create mask = 0777
directory mask = 0777[/COLOR]
```

Then save it.

Then restart samba with this command in terminal:
```
sudo /etc/init.d/samba restart
```

---

### Post by sideffects on 2009-05-17
thanks, although, I haven't rebooted yet to test it yet. So, why doesn't it save my shares by default?

---

### Post by sideffects on 2009-05-17
UPDATE: It still didn't save the "Let other users write in this folder"

---

### Post by doas777 on 2009-05-17
did you add the share defn to your smb.conf as mprince suggested? it won't check the checkbox, but it will allow users to write to the share.

I usually define my samba configuration with the configuration file, as I've had trouble with the gui user-space folder sharing. it only works while the user is logged in, and does mysterious things at strange times.

---

### Post by mprince on 2009-05-17
[QUOTE=sideffects]So, why doesn't it save my shares by default?[/QUOTE]

I'm not sure. I've never gotten good results using the GUI to define shares, but this seems to force it.

Any share you define this way (without using the GUI) doesn't have a little shared emblem, but your can add that yourself by right-clicking on the folder and click *Properties>Emblems* tab and give it one.

---

### Post by sideffects on 2009-05-17
> **doas777 said:**
> did you add the share defn to your smb.conf as mprince suggested? it won't check the checkbox, but it will allow users to write to the share.

I usually define my samba configuration with the configuration file, as I've had trouble with the gui user-space folder sharing. it only works while the user is logged in, and does mysterious things at strange times.

yes I added it. Sorry, I just assumed that it would check the checkbox.

---

