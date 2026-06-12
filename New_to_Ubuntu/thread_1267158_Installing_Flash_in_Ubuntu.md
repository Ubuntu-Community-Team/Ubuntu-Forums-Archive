---
title: "Installing Flash in Ubuntu"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by davo11 on 2009-09-15
hi
I just re-installed Ubuntu and thought 'first thing is to install flash' so I type in > $sudo apt-get install flashplugin-nonfree and it says it can't find the file. Then I try it again and it says flashplugin-nonfree is already newest version, but flash isn't working! Any help would be greatly appreciated.
thanks in advance

---

### Post by camargo70 on 2009-09-15
Now, if you try with [http://www.adobe.com](http://www.adobe.com) directly get flash for ubuntu (.deb) ?

---

### Post by davo11 on 2009-09-15
oh sorry forgot to mention i tried that and it said dependency (libnspcr or something) could not be sorted

---

### Post by sunchiqua on 2009-09-15
```
sudo apt-get install ubuntu-restricted-extras

```

---

### Post by Darkwing-Duck on 2009-09-15
Using the non-free version of Flash requires you to enable the Restricted Repositories. Once it is enabled then you will be able to install via apt-get.
 
Go to System > Administraion > Software Sources Under the tab Ubuntu Software there will be check boxes. Make sure you select the Multiverse (as the flashplugin-nonfree is in the Multiverse Repositories ([http://packages.ubuntu.com/jaunty/flashplugin-nonfree](http://packages.ubuntu.com/jaunty/flashplugin-nonfree)))
 
Once that is done go back to the terminal and type
 
```
sudo apt-get update
```
 
```
sudo apt-get install flashplugin-nonfree
```
 
If you want more information on packages you can use the search function at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 
If you want more information on Repositories then visit [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
 
Hope this helps!

---

### Post by thiebaude on 2009-09-15
enable 3rd patry repositories

---

