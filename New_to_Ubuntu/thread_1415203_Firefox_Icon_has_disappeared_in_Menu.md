---
title: "Firefox Icon has disappeared in Menu"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by prenoob on 2010-02-24
After updating Firefox to 3.5.8 (I think), I have lost the FF icon from the Accessories>Internet Menu.  Instead, there is a grey coloured folder icon against the Firefox Browser menu item.  Can any of you kind people help me to get it back, I wonder?

Yours hopefully,

Trev

---

### Post by Apollo87 on 2010-02-24
Is it just the menu item thats gone? Can you still launch it from a terminal?

If you can still launch it you should check out this page:
[http://www.doyouubuntu.com/wordpress/?p=27&lang=en](http://www.doyouubuntu.com/wordpress/?p=27&lang=en)

Its a nice little howto to manually create a shortcut in the menus.

---

### Post by prenoob on 2010-02-24
> **Apollo87 said:**
> Is it just the menu item thats gone? Can you still launch it from a terminal?

If you can still launch it you should check out this page:
[http://www.doyouubuntu.com/wordpress/?p=27&lang=en](http://www.doyouubuntu.com/wordpress/?p=27&lang=en)

Its a nice little howto to manually create a shortcut in the menus.
The ***icon*** beside the menu has gone.  I can still launch from the item itself.  Your suggestion did not work at all and I see it was posted on 27 May 2007.

Trev

---

### Post by Apollo87 on 2010-02-24
Ah, well, the firefox menu icon is located at /usr/share/applications/firefox.desktop

If you open that up and scroll down you'll find an entry called "Icon=" where you enter a path to the desired icon. I removed that from my file and it put a grey icon next to the menu item so yours must be empty or pointing to a non-existent file.

My suggestion would just be to download a new icon and point it to that.

---

### Post by bodhi.zazen on 2010-02-24
System -> Preferences -> Main Menu

Select firefox -> click the properties button -> 

In teh next box, click the icon in the upper left -> navigate to the firefox icon

Default location /usr/share/pixmaps/firefox-3.5.png

If it is not there, open a terminal

```
sudo updatedb
locate firefox-3.5.png
locate firefox | grep .png
```

---

### Post by prenoob on 2010-02-25
Many thanks.  I tried bodhi.zazen's suggestion first - worked perfectly and I'm marking this thread "solved".  Excellent help from the Community.

Trev

---

