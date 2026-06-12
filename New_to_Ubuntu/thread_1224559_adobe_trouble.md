---
title: "adobe trouble"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by [WaZ]Pac-Man on 2009-07-27
im trying to install adobe ive tried to run an installer as follows 





----------- Install Action Summary -----------

Adobe Flash Player 10 will be installed in the following directory:

Mozilla installation directory  = /home/_____/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


i then try to remove xpti by doing the find

sudo find / -name xpti.dat

that returns

/home/sniper/.mozilla/firefox/7x3trtgz.default/xpti.dat
/usr/lib/xulrunner-1.9b5/components/xpti.dat

so i run this


sudo rm home/sniper/.mozilla/firefox/7x3trgz.default/xpti.dat


which returns

rm: cannot remove `home/sniper/.mozilla/firefox/7x3trgz.default/xpti.dat': No such file or directory

any ideas on how to get rid of it?

thanks!

ohh and when i do that flash hasnt installed because i cant view vids on youtube

thanks again haha

---

### Post by Michael.Godawski on 2009-07-27
Have you tried to navigate into the director with 
```
cd /home/sniper/.mozilla/firefox/7x3trtgz.default/
```
and then removing the xpti.dat file with 
```

rm -i xpti.dat
```

---

### Post by [WaZ]Pac-Man on 2009-07-28
ok i did that but again it shows up to delete it

ive also deleted it through the gui

yet i cant get adobe to work 

im trying to view vids on youtube but it wont work

so now im lost

---

### Post by sandeepraj on 2009-07-28
see if adobe is installed from synaptic package manager 
search adobe-flashplugin in synaptic package manager and install form der if not installed

---

### Post by [WaZ]Pac-Man on 2009-07-28
ive done that too and it didnt work
it says its installed but for some reason it wont play the vids still

sorry about my delay in responces im in recovery week from a surgery

but yah like i said that didnt work either

ive even gone to the adobe site and downloaded all of the versions and none of them work either

i even uninstalled firefox to see if i could do it that way and it still dodnt work

---

