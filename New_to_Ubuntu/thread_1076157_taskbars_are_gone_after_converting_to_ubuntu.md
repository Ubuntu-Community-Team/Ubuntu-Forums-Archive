---
title: "taskbars are gone after converting to ubuntu"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by gaffurabi on 2009-02-21
i have converted to ubuntu from xubuntu using synaptic. when ubuntu login screen first appeared it asked me if i want to login using xfce-4 script and i said "yes" (was a mistake to do, apparently). now the taskbars wont load :(

any help?

---

### Post by adult swim on 2009-02-21
see if you can log out by hitting ctrl+alt+backspace
when you log back in, click on the options button and then go to sessions and select gnome.

---

### Post by gaffurabi on 2009-02-23
unfortunately didnt work out :(

---

### Post by gaffurabi on 2009-02-23
any other suggestions?

---

### Post by kansasnoob on 2009-02-23
The only thing I can think of is press Alt > F2 which will bring this up:

[ATTACH]104388[/ATTACH]

Notice that I've clicked on "show list of apps" and highlighted "Terminal". If you then click on "Run" it will open the terminal. Then in terminal run this command:

```
sudo apt-get install --reinstall ubuntu-desktop
```

Now, I think that should also install gdm and unless you've removed the xubuntu desktop entirely you'll be asked if you want to use gdm or xdm. Choose gdm.

But if you want to be sure run:

```
sudo apt-get install gdm
```

And finally run:

```
sudo apt-get -f install
```

Which should resolve any unmet dependencies.

Then hit Ctrl > Alt > Backspace and be sure to select Gnome from "Sessions".

If you decide to go pure Gnome run the "remove Xubuntu" command shown here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by gaffurabi on 2009-02-23
thanks a lot! that worked :D

---

