---
title: "installing deluge"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by aliasghar1451 on 2010-02-28
hi i needed help regarding deluge i searched the web for a deb of the latest version of deluge but i didnt find it so i download the source file from there site but its not working i did what it told me in the read me file everything when well but when i try to open deluge it just doesnt start plz can anyone help me 
i m using ubuntu 8.04

---

### Post by cenzorrll on 2010-02-28
all you should need to do is enter this into your terminal:

```
sudo apt-get install deluge-torrent
```

---

### Post by chewearn on 2010-02-28
If you want updated deluge package, the ppa is:
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by themusicalduck on 2010-02-28
Or just go to Applications > Add/Remove and search for deluge.

---

### Post by aliasghar1451 on 2010-02-28
> **cenzorrll said:**
> all you should need to do is enter this into your terminal:

```
sudo apt-get install deluge-torrent
```

i did it but still it isnt opening on the bottom toolmar a atab comes saying opening deluge and then it disappears

---

### Post by aliasghar1451 on 2010-02-28
> **chewearn said:**
> If you want updated deluge package, the ppa is:
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

and i m sorry but i m a bit new with this what do i do with this ppa

---

### Post by chewearn on 2010-02-28
PPA is third party software repositories, apart from the official Canonical Ubuntu's.  A software repository is where all the software are hosted online.

In this instance, the Deluge Team owns this PPA, so you are getting the latest stable version.

The instruction to add the PPA and install the application is explained in the page linked.

---

### Post by themusicalduck on 2010-02-28
> **aliasghar1451 said:**
> i did it but still it isnt opening on the bottom toolmar a atab comes saying opening deluge and then it disappears

I'm not sure what you mean by this. Is there a shortcut to deluge in Applications > Internet?

edit: I understand now, the toolbar at the bottom when you click to open. So it's probably installed.

Try typing ```
deluge
``` into a terminal and see if anything comes up or if there are any error messages in the terminal window.

Also, just in case. When you open deluge does an icon that looks like a water drop appear in the notifications area on the top toolbar?

---

### Post by aliasghar1451 on 2010-02-28
> **themusicalduck said:**
> I'm not sure what you mean by this. Is there a shortcut to deluge in Applications > Internet?

edit: I understand now, the toolbar at the bottom when you click to open. So it's probably installed.

Try typing ```
deluge
``` into a terminal and see if anything comes up or if there are any error messages in the terminal window.

Also, just in case. When you open deluge does an icon that looks like a water drop appear in the notifications area on the top toolbar?

when i type deluge in the terminal it says
```

Traceback (most recent call last):
  File "/usr/bin/deluge", line 46, in <module>
    import deluge._dbus as dbus
ImportError: No module named _dbus

```
so what can be the problem ??
and yes the water drop icon it appears with the tab (when i try to open it) and in my menu
but no not in the notification area (if notification area mean where time, date and all is)

---

### Post by themusicalduck on 2010-02-28
Try this in a terminal ```
sudo apt-get install python-dbus
```

---

### Post by aliasghar1451 on 2010-03-01
it sayed that this package is already installed 
and yes i forgot to tell after installing the sourcefile i deleted the folder and when i try to empty the trash a file namedeluge-1.2.1-py2.5.egg give some error and i m not able to delet it from the trash.

---

### Post by themusicalduck on 2010-03-02
So did you download the source and install from that, before installing it from the software centre?

You might need to uninstall every instance of deluge before it will work. First off, try this command ```
sudo apt-get purge deluge-torrent
```

Then reinstall it again from the software centre. See if it works after. If not, then run that code again to remove it once more.

Then run this command instead ```
sudo rm -r /usr/lib/python2.5/site-packages/deluge*
``` copy and paste the whole line directly, it's best not to type it in because you might delete something unintentionally.

This command is from [http://dev.deluge-torrent.org/wiki/Installing/Source#RemovingFromSystem](http://dev.deluge-torrent.org/wiki/Installing/Source#RemovingFromSystem)

After that command has been run, try installing it again from the repository and see if it helps.

---

### Post by aliasghar1451 on 2010-03-04
thanks themusicalduck it worked but i still have a little problem i cant delete the deluge-1.2.1-py2.5.egg file form my trash it say u dont have permission

---

### Post by nothingspecial on 2010-03-04
```
gksudo nautilus
```

press H

go .local > share > Trash and delete the file

Then immediately close the window before you delete or modify something you shouldn`t

---

