---
title: "Where could that sneaky theme be hiding?"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by jermza on 2011-02-11
Apologies if this is a silly question, but I installed a theme (by double-clicking on one its files), didn't like it, and am now trying to remove it.  I've looked in home > .themes, but it's not there (yet still appears in the Appearance menu).

Where else might it be?

---

### Post by Perfect Storm on 2011-02-11
1. How did you installed the theme?

2. Which kind of theme? Icon theme? GTK2 theme? AWN theme?

---

### Post by jermza on 2011-02-11
> **Artificial Intelligence said:**
> 1. How did you installed the theme?

2. Which kind of theme? Icon theme? GTK2 theme? AWN theme?
Ubuntu theme.

I downloaded a GTK2 theme from gnome-look.  I double-clicked on a .sh file, which installed the theme so that it appeared in the Appearance menu (alongside Clearlooks etc).

I can't seem to find it in the .themes folder, so I'm not sure where it installed to.

---

### Post by Perfect Storm on 2011-02-11
If you used a script to install it, it properly installed it systemwide instead of locally.

It may that the script is build to also uninstall the theme, so you may ttry run the script again and see if you get an option to remove the theme.


Otherwise you can remove the theme by;
```
cd /usr/share/themes
sudo rm -rf <theme folder>
```
Just be careful with the second command, it will remove whatever you inserted completely.

---

### Post by jermza on 2011-02-11
> **Artificial Intelligence said:**
> If you used a script to install it, it properly installed it systemwide instead of locally.

It may that the script is build to also uninstall the theme, so you may ttry run the script again and see if you get an option to remove the theme.


Otherwise you can remove the theme by;
```
cd /usr/share/themes
sudo rm -rf <theme folder>
```Just be careful with the second command, it will remove whatever you inserted completely.
This is the theme (and instructions): [http://gnome-look.org/content/show.php/Divergence+IV+-+%22A+New+Hope%22?content=133892](http://gnome-look.org/content/show.php/Divergence+IV+-+%22A+New+Hope%22?content=133892)

I don't know what the theme folder is, so I can't insert it into your suggested code.  I just know what it is called in the Appearance menu ("A New Hope").

---

### Post by Perfect Storm on 2011-02-11
Okay, from the readme file it says **/usr/share/themes/A-New-Hope**

So you need to delete a folder called **A-New-Hope**

---

### Post by jermza on 2011-02-11
> **Artificial Intelligence said:**
> Okay, from the readme file it says **/usr/share/themes/A-New-Hope**

So you need to delete a folder called **A-New-Hope**
Thanks.

However, when I inserted your code into Terminal, I got this:

bash: syntax error near unexpected token `newline'

What is that?

---

### Post by Perfect Storm on 2011-02-11
Can you please give the whole in/output.

---

### Post by jermza on 2011-02-11
> **Artificial Intelligence said:**
> Can you please give the whole in/output.
Oh, I shouldn't have included "<" and ">".  It ran the command without error, but nothing happened.  The theme is still there and so is the folder.

Must I log out and log back in?

---

### Post by Perfect Storm on 2011-02-11
```
cd /usr/share/themes
sudo rm -rf A-New-Hope
```

---

### Post by jermza on 2011-02-11
> **Artificial Intelligence said:**
> ```
cd /usr/share/themes
sudo rm -rf A-New-Hope
```
Perfect.  Thanks.

---

