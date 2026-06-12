---
title: "Icon question"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by ADDuhh on 2010-09-20
I have an Icon question. After a clean install upgrade of Lucid from Ibex Wine was a shambles. Aggravating this was a run of Computer Janitor, which only removed files many  programs needed. One of the ways Ive coped was to start many  programs on the new windows location by right click and “open with Wine program loader”.  After second reinstall everything works ok and 'BONUS' I get a nice new icon for an old windows program. I like the icon, I use the program a lot, so I want to create a launcher in the Main Menu. My question 'finally' is  “How do I find or extract the custom icon to the launcher?”

---

### Post by jtarin on 2010-09-20
Do you know the name of the icon and extension? You can use the command...for example. ```
locate iconname.png
``` 
If you have never used locate you will first have to update your database with the command ```
updatedb
```it will take sometime to run thefirst time, when done use the "locate" command.

---

### Post by ADDuhh on 2010-09-25
Thanks for the reply
unfortunately I don't know the name. I have tried the search feature with the app name and "wine" but no luck. Since this is a unique icon that only appeared after I used the "open with wine" I assumed that the system created it it might have a known location. The application is a old password vault and I don't think anyone would have created the icon.

---

### Post by beew on 2010-09-25
> **ADDuhh said:**
>  After second reinstall everything works ok and 'BONUS' I get a nice new icon for an old windows program. I like the icon, I use the program a lot, so I want to create a launcher in the Main Menu. My question 'finally' is  &#8220;How do I find or extract the custom icon to the launcher?&#8221;

Since it is from a windows program it is probably in a subfolder of ~/.local/share/ , maybe ~/.local/share/your_program's_name or ~/.local/share/icons.

To use it for making a launcher from the main menu you will have to copy it to /usr/local/share/icons (or something like that, the point is you have to be able to choose it from the main menu's launcher creation box)

**Edited:** Since it is from a windows program chances are it is an .ico file, you have to convert it to a .png file. Simply open it and save as .png.

---

