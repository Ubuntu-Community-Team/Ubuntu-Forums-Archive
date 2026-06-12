---
title: "Celestia gnome addon help"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by SunnyGliese on 2010-12-30
Hello from a newbie.  I need some help from any celestia users please. I'm running ubuntu lucid gnome & would like to add my saved Celestia addons to the directory usr/share/celestia but i dont have permission. been warned indirectly not to log in as root otherwise I'd try that. I can access root from terminal window but dont know where to go from there?  I thought perhaps I could alter config file to point to addon folder but no idea how.  any help would be much apprectd.

---

### Post by XeonBloomfield on 2010-12-30
Create folder in your "Home Folder" called "celestia".

Paste there everything what you want to copy.

Next run "Terminal". 
Applications > Accessories > Terminal.

Type these commands:
```
cd celestia
sudo cp * /usr/share/celestia/
```

This will copy everything from folder "celestia" to "/usr/share/celestia".

---

### Post by The Cog on 2010-12-30
When you want write permissions outside of your home folder, prefix the command with **sudo** (as XeonBloomfield suggests) or prefix GUI commands with **gksudo** as with **gksudo nautilus** (be very careful with it). 
Further reading: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SunnyGliese on 2010-12-30
thanks Xeon! & if I want to add to a specific directory inside celestia I'll just add more subdirectories to that line.  very easy.

---

