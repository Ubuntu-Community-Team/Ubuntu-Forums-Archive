---
title: "How to work terminal downloads"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Tmoney1309 on 2009-01-27
I just downloaded this code to get Freewins for my computer...

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O /tmp/freewins.zip [http://smspillaz.googlepages.com/freewins-0.3-0.6.zip](http://smspillaz.googlepages.com/freewins-0.3-0.6.zip)
mkdir -p  ~/compiz/ && cd ~/compiz
unzip /tmp/freewins.zip
cd ~/compiz/freewins-0.3-0.6
make clean
make
make install
 
and I downloaded and installed something that was 120MB and now i cant find it. Can anybody help me and tell me where to look after I have downloaded a file...where can i find it?

---

### Post by zabien1970 on 2009-01-27
Have you tried, in terminal, whereis freewins

---

### Post by Tmoney1309 on 2009-01-27
doesn't exist it says..."freewins:"

---

### Post by neu2buntu on 2009-01-27
try clicking on >places >computer >file system and then search , type in the name of the file u downloaded , hit return .. then if the package shows up ,right click it and choose >properties , this will show u the location

---

### Post by handydan918 on 2009-01-27
The stuff you posted indicates it was saved to /tmp/

hope you haven't rebooted since then....

---

### Post by neu2buntu on 2009-01-27
if it just says freewins: this means its in your home directory

---

### Post by Tmoney1309 on 2009-01-27
okay i found it, now it is on my desktop. I cant get it to work though...any ideas? When i open it it just shows me the files inside

---

### Post by SOULRiDER on 2009-01-27
I believe everything should be in ~/compiz/freewins

---

### Post by neu2buntu on 2009-01-27
that script should have installed freewins for you , i would fire up compiz and see if the files have been added... not sure if u already had compiz, try ```
compiz
``` in the terminal or ```
ccsm
``` if you have the manager already


you will need the compiz manager to control these effects type in terminal ```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by handydan918 on 2009-01-27
What do ya suppose this means?

```
unzip /tmp/freewins.zip
```
Paying special attention to the /tmp part...

---

