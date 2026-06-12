---
title: "Open window as root in nautilus"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by adrek on 2009-09-20
Hi Guys,

I was wondering if there is  anything that would let me right click in a window in nautilus and let me open it as root. 

I have tried nautilus-gksu and it works but its not exactly what im looking for. I'm looking for something thats more like the mint interface that could 

A) allow you to click anywhere in the window to open the current folder as root not just a selected item

B) open the root window with a different background color or something that would allow me to distinguish between the root window and the regular user window.

thanks.

---

### Post by SteveDee on 2009-09-29
Not sure if this helps, but you could create a Nautilus script to open the selected folder as root in a new Nautilus window. You can set the preferences in the new window to look different from normal user access (e.g. maybe put the Permissions column next to the file/folder name column).

To get you going I've created the attached script. Put this in your {Home}/.gnome2/nautilus-scripts folder. Right click on this file and go Properties > Permissions and set "Allow executing file as program".

Now when you use Nautilus you should be able to right click a folder, select "scripts" then "AsRoot.sh" and open nautilus as root.

You have to enter your password with this script, which I think a sensible precaution. But you can modify to overcome this if you are really keen.

---

### Post by Arup on 2009-09-29
sudo apt-get install nautilus-gksu 

You will get a tab to open as admin.

---

### Post by kerry_s on 2009-09-29
i agree nautilus script it.

root-open:
[B]#!/bin/sh
gksudo gnome-open $NAUTILUS_SCRIPT_CURRENT_URI
[/B]
root-edit:
[B]#!/bin/sh
gksudo gedit "$@"
[/B]

you can also use just 1, i prefer to seperate:
[B]#!/bin/sh
gksudo gnome-open "$@"[/B]

---

### Post by kerry_s on 2009-09-29
i condensed it to 1 script:

```
#!/bin/sh

if [ -d "$@" ]; then
  gksudo gnome-open $NAUTILUS_SCRIPT_CURRENT_URI
 else
  gksudo gedit "$@"
fi

```

---

