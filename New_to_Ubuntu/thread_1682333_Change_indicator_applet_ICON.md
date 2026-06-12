---
title: "Change indicator applet ICON"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by maciej234 on 2011-02-05
I'd like to change an applications's indicator applet icon.  Pithos - the pandora app.  How can I change this app icon in the top system panel and any app in the for the future?  I can't seem to locate the folder that has the current icon so I can replace it with a new one. It was really easy to change the icon on the AWN dock, right click and customize icon.

---

### Post by cwsnyder on 2011-02-05
Go to Administration >> Main Menu, open the menu and scroll down through the menu heirarchy to get to the application you wish to change in the main menu.

If it is not in the menu, but is on the panel, right click on the icon and choose 'properties'.

---

### Post by maciej234 on 2011-02-05
I solved this.  I am using the faena dark icons.  The app had a icon in the "faenza" icon folder not the faenza dark folder.  

I used this command to find the icon:

sudo find /usr/share -type f -name "system-shutdown.png"

system shutdown.png = pithos.png


/usr/share/icons/Faenza/apps/22/pithos.png

---

