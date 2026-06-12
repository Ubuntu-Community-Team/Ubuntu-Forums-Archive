---
title: "How do I find a manualy installed .deb file?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by 3dz on 2008-12-08
I have installed a .deb file, but I can't seem to find a start program.  I looked in synnaptic, and it says it is install.
Can anybody tell me how to start this program, and place an icon on the desktop so I can start it in the future.

---

### Post by MarblePanther on 2008-12-08
Right click on your menu and go to edit menu

setup the link to the file that is in /usr/bin

---

### Post by adult swim on 2008-12-08
try typing the first three letters of the program name in the terminal and then hit the tab key two times.  that should suggest some file names.  then try typing them one at a time and hit enter.

---

### Post by MarblePanther on 2008-12-08
look in /usr/bin for the name of the program (or variations of it)  and you may find it

then edit your menu and include it















EDIT:

since you found it in synaptic go to it again there and click on the installed files tab on the synaptic of it and find what is in usr/bin

[ATTACH]95708[/ATTACH]

---

### Post by ghantoos on 2008-12-08
You can check out the files that where installed by the .deb file. You must find there the one to run and create out of it on your desktop. Open a terminal and type:
```
dpkg --listfiles yourprogram
```The output must look like this:
```
ghantoos@blabla:~$ dpkg --listfiles twinkle
/.
/usr
/usr/bin
/usr/bin/twinkle
/usr/share
/usr/share/applications
/usr/share/applications/twinkle.desktop
/usr/share/services
/usr/share/services/sip.protocol
/usr/share/twinkle
/usr/share/twinkle/lang
...

```The executable here is /usr/bin/twinkle. Right lick on your desktop -> "Create launcher" -> enter /usr/bin/twinkle in the "Command" box.

Hope this helps,
Cheers,

---

### Post by 3dz on 2008-12-08
Wow, I didn't expect this kind of response so quickly.  Great community!
It's been so long since I've used my other computer.  I had to recharge the batteries in my mouse.  As soon as everything is charged up, I'll try some of these suggestions.
Thank you all, for great responses.

---

