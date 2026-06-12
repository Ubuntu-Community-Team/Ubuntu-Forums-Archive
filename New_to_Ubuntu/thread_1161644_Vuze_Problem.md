---
title: "Vuze Problem"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-16
I installed vuze from both Add/Remove and from synaptic but its not starting up , How can i make it work, I downloaded the latest version from its home page but could not know how to install it

---

### Post by taurus on 2009-05-16
Did you install Sun java from either Add/Remove or Synaptic first?

---

### Post by ravi_buz on 2009-05-16
Sorry didnt check,now working,
One more thing i have 3.1 installed from synaptic and downloaded 4 from home page but dont know how to install ,So can i do it i hae extacted it but there is no install file or make file in it

---

### Post by taurus on 2009-05-16
When you download it from their website, you would get the one with .deb extension.  Just double-click the filename to install it.  Probably best to remove the older version from your machine first before you install the newer version.

---

### Post by ravi_buz on 2009-05-16
Nope i could see onlt tar.bz2 files

---

### Post by taurus on 2009-05-17
All you have to do is to unpack it and run it.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvjf Vuze_Installer.tar.bz2
cd vuze
./azureus
```

---

### Post by ravi_buz on 2009-05-17
thanks vuze starts but how to install

---

### Post by taurus on 2009-05-17
What do you mean install?  There is nothing to install.  If you want to run the version that you've downloaded, that is how you would run it, changing to it and run it from a terminal.  Otherwise, you can create a launcher on the top panel so when you click on the icon, you would run it if you don't feel like typing all that in a terminal.

---

### Post by doas777 on 2009-05-17
no idea if this is your problem, but if you install vuze/azureus via the repositories (add/remove, synaptic, or apt-get) then you cannot use azureus' built in updater. you just have to wait until the repos are updated or, you can uninstall it via add/remove, and install the deb/tarball version from their website.

---

### Post by Jazzy_Jeff on 2009-05-17
I am using the same version from the website. I just unpacked it to my home directory and then right click on Applications then Edit menus. I created my own launcher from there. Just choose where you want to put the launcher.

---

### Post by ravi_buz on 2009-05-17
can u guys explain me how to do it,I hate using command linue

---

### Post by Jazzy_Jeff on 2009-05-17
> **ravi_buz said:**
> can u guys explain me how to do it,I hate using command linue

What command line? Ok, download the package and double click on it. Extract it where you want it. I put mine in the Home folder. Next right click on Applications at the top and select Edit Menus. I clicked on Internet down the first list. Then I clicked on New Item. Under type just select Application. Under Name whatever you want. I chose Vuze to make it simple. Under Command just browse to where you put the folder (example, /home/jeff/vuze/vuze ). Click ok and you should be done. You should have the launcher in your list.

---

