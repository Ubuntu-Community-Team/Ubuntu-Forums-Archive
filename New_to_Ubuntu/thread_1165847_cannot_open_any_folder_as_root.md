---
title: "cannot open any folder as root"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by faraz_k86 on 2009-05-21
i have to install a phoenetic keyboard.. for thgat i need root access. im used to nautilus but im stuck with dolphin now.. i cant use kdesudo dolphin in terminal cause it give me the following error:

> cannot start process cannot talk to klauncher. the name org.kde.klauncher was not provided by any .services files

any suggestions??

thx

---

### Post by iaculallad on 2009-05-21
I don't know if this can be the known Bug of KDE. Try using the workaround command below:

```
kdesu dbus-launch dolphin
```

HTH.

---

### Post by faraz_k86 on 2009-05-21
k so sftear seraching google i found that this is a normal error and can be fixed by running "kdeinit" in terminal....but sadly that does not fix my problem.

any other ideas.

---

### Post by faraz_k86 on 2009-05-21
> **iaculallad said:**
> I don't know if this can be the known Bug of KDE. Try using the workaround command below:

```
kdesu dbus-launch dolphin
```

HTH.


Thanks but i get the following lines after i enter your command:

> lims@lims-desktop:~$ kdesudo dbus-launch dolphin
"/usr/bin/dolphin(7181)" Error in thread 3052996288 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(7181)" Error in thread 3052996288 : "QLocalSocket::connectToServer: Invalid name"
dolphin(7181) <unnamed>::GlobalModelContainer::init: Failed to connect to Nepomuk server via local socket "/root/.kde/share/apps/nepomuk/socket"
"/usr/bin/dolphin(7181)" Error in thread 3052996288 : "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"


---

### Post by faraz_k86 on 2009-05-21
so far ive had only problems with kubuntu...is it just me or does kubuntu suck like this for everyone.

why cant it be more like ubuntu :)

---

