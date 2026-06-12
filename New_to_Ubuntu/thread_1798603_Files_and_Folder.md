---
title: "Files and Folder"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by arno48 on 2011-07-06
Hi,
 My files are hierarchically ordered in a long chain of folders, for instance the folders could be
 Educational/Math/Secondary School/Logarithm/SeconLesson  : each folder included in the previous one as a Matrioska (or a Russian dolly).
 My problem is the following:
 When I have opened a folder (for instance Logarithm), how can I return to a superior level (for instance Math)?
 Now I close the all and start opening from the beginning (for instance Educational)

---

### Post by maizuddin35 on 2011-07-06
I don't actually understand what do you really want ? do you want to do it in the terminal?

---

### Post by smurphy_it on 2011-07-06
In Thunar ensure that the views for "Main Toolbar" and/or "Location Bar" are enabled (under the view menu).

If main toolbar, you'll have a back button.  If Location bar, you can click the name of the folder.

In a cli / terminal, type:  cd ..

---

### Post by aeiah on 2011-07-06
in thunar / nautilus, the backspace key will also take you back a step. but i think most people use the gui buttons...

---

### Post by dcsoldschool53 on 2011-07-06
> **arno48 said:**
> Hi,
 My files are hierarchically ordered in a long chain of folders, for instance the folders could be
 Educational/Math/Secondary School/Logarithm/SeconLesson  : each folder included in the previous one as a Matrioska (or a Russian dolly).
 My problem is the following:
 When I have opened a folder (for instance Logarithm), how can I return to a superior level (for instance Math)?
 Now I close the all and start opening from the beginning (for instance Educational)

In the terminal```
Educational/Math/Secondary School/Logarithm/SeconLesson
```let say that you are in SeconLesson folder, and you want to get to the Secondary\ School directory. By the way, when you have two words separated by a space, you need to use \ behind the first word to show separation or use the quotation mark like this Math/"Secondary School"/Logarithm. Type this in the terminal```
cd ~/Educational/Math/Secondary\ School
```That is if, Educational is the first directory in your/home folder/usename.

You do it the same way using math```
cd ~/Educational/Math
```

---

### Post by dcsoldschool53 on 2011-07-06
In nautilus you have a roll of buttons at the top. If you are in SeconLesson folder, you will see a button for Education, a button for Math, a button for Secondary School, etc. Just click on the Math button once or twice. Give it a minute to reload. You do not have to close it.

---

### Post by arno48 on 2011-07-06
> **smurphy_it said:**
> In Thunar ensure that the views for "Main Toolbar" and/or "Location Bar" are enabled (under the view menu).

If main toolbar, you'll have a back button.  If Location bar, you can click the name of the folder.

In a cli / terminal, type:  cd ..

  	 	 	 	 	 	  Thanks, I enabled Main Toolbar, Location Bar and Lateral Folder List and all my problems were overcome).
 By the way could you please let me know the English name of the tool positioned between The main Toolbar and The Location Bar in the View menu

---

### Post by smurphy_it on 2011-07-06
```
By the way could you please let me know the English name of the tool positioned between The main Toolbar and The Location Bar in the View menu
```

Answer = Side Pane

---

### Post by arno48 on 2011-07-06
> **smurphy_it said:**
> ```
By the way could you please let me know the English name of the tool positioned between The main Toolbar and The Location Bar in the View menu
```Answer = Side Pane

Thanks for all

---

