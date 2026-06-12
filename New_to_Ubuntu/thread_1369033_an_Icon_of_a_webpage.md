---
title: "an Icon of a webpage"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-12-31
So, my mom would like to make an icon on the taskbar that will go directly to a site. How would I go about doing it?

---

### Post by thatguruguy on 2009-12-31
Assuming that by "taskbar" you mean "Gnome panel", you can try the following:

1. Right click on an empty spot on the panel.
2. Choose "Add to Panel..." from the menu that pops up.
3. Choose "Custom Application Launcher".
4. When the "Create Launcher" window comes up, choose "Location" from the "Type:" drop-down menu.
5. Type the name of the site in the "Name" box and the url in the "Location" box.
6. Click "OK" to close the Create Launcher" window.

---

### Post by 3rdalbum on 2009-12-31
Right-click the panel and choose "Add To Panel...".

Click "Custom Application Launcher" and Add.

Under the Name, put whatever you want.

Under the Command, put the word "firefox" and then the URL of the website, for instance:

```
firefox http://www.ubuntuforums.org
```

Click on the icon and choose an appropriate icon if you want.

When you click OK, you'll have an icon on your panel that will open a web page in Firefox.

If you prefer a different browser, put its name instead of Firefox. And if you want the browser to change depending on your "default browser" settings, use "xdg-open" instead of a web browser:

```
xdg-open http://www.ubuntuforums.org
```

---

### Post by chewearn on 2009-12-31
The simplest method:
Open the website in Firefox, drag and drop from the icon next to the address bar to the panel.

---

