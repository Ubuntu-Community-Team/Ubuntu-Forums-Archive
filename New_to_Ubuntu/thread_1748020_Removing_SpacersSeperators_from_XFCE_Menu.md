---
title: "Removing Spacers/Seperators from XFCE Menu"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Chrissd on 2011-05-03
Hi,

Can anyone tell me how to remove these spacers seen at the top left seen in this screen shot? There's two of them I'd like to remove at the top.

Thanks

[img]http://img685.imageshack.us/img685/8271/screenshot030511120642.png[/img]

---

### Post by EGamerHDK on 2011-05-03
Are you talking about this? The extra line in the menu?
[IMG]http://img88.imageshack.us/img88/1589/screenshot1bm.png[/IMG]

---

### Post by Chrissd on 2011-05-03
Hi

Yes, that's the one (well, both those lines I'd like to remove). :)

---

### Post by deathadder on 2011-05-03
[http://wiki.xfce.org/howto/customize-menu](http://wiki.xfce.org/howto/customize-menu)

You may be able to use Alacarte depending on your version of XFCE (you need 4.8)...

---

### Post by Chrissd on 2011-05-03
Hi!
Wow that's one of the most confusing howto's I've read for a while.

For anyone else looking to adjust this, the way I did it (maybe the 'wrong way' but it worked) you need to firstly backup the file with this command
```

sudo cp /etc/xdg/menus/xfce-applications.menu /etc/xdg/menus/xfce-applications.menu.backup

```

Then edit it:
```

sudo nano /etc/xdg/menus/xfce-applications.menu

```

Where you see <Separator/> just delete it (#'s don't work as a comment).

When you have adjusted the file as you wanted, you exit it with this command
```
ctrl + x
```

Then press 'y' to save it and press enter to over write the existing file.

The changes should be instant!

If things go really wrong, you can quickly revert back to default by inserting this command in a terminal:
```

sudo mv /etc/xdg/menus/xfce-applications.menu.backup /etc/xdg/menus/xfce-applications.menu

```

Thanks guys!

---

### Post by deathadder on 2011-05-03
> **Chrissd said:**
> Hi!
Wow that's one of the most confusing howto's I've read for a while.

Yeah, XFCE has been lacking in the menu editing department for a while now. Should be easier now as of 4.8 with the new menu library which means you can use 3rd party apps to do it.

---

