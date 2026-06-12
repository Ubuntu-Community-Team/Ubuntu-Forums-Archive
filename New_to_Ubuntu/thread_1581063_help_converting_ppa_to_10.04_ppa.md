---
title: "help converting ppa to 10.04 ppa"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by DarinB on 2010-09-24
I have this ppa for gpodder 
deb [http://ppa.launchpad.net/thp/gpodder/ubuntu](http://ppa.launchpad.net/thp/gpodder/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
deb-src [http://ppa.launchpad.net/thp/gpodder/ubuntu](http://ppa.launchpad.net/thp/gpodder/ubuntu) YOUR_UBUNTU_VERSION_HERE main 

I am not able to figure out how to convert this to a 10.04 ppa for terminal?

I tried this but didn't work
sudo add-apt-repository ppa:launchpad.net/thp/gpodder/ubuntu

I tried sudo add-apt-repository ppa:/thp/gpodder

result was failed to fetch ??

---

### Post by Frogs Hair on 2010-09-24
After ppa: insert the name of the repository and not the location at launch pad .net  this line :deb [http://ppa.launchpad.net/thp/gpodder/ubuntu](http://ppa.launchpad.net/thp/gpodder/ubuntu)  needs to be added to software sources under the other software tab.

---

### Post by Frogs Hair on 2010-09-24
Try this from Ubuntu Geek.

 sudo add-apt-repository ppa:thp/gpodder

sudo apt-get update

sudo apt-get install gpodder

---

### Post by DarinB on 2010-09-24
I did what froghair wrote...got all the errors i showed above but when i decide to check gpodder it is the new version and everything works so i don't understand the errors...i did remove the entries in software sources and update error went away. no idea what happened but it seems do work...i will see after a reboot.

---

### Post by beew on 2010-09-24
Just open up Synaptic, go to Settings > Repositories and open the "Other Software" tab, then click "Add" and paste>  ppa:/thp/gpodder into the box, then close it and click "Reload" (to update your source list) and that's it.

If you still get "failed to fetch" it is probably because your internet connection is interrupted or there are  probably some connection problems on the source's end. I get it all the time with some PPAs. Just wait a bit and try again.

---

### Post by madmax75 on 2010-09-24
Besides, if you use Ubuntu Tweak (which everybody should have :)). you should just be able to tick the appropriate PPA from there.

---

### Post by DarinB on 2010-09-25
I have no idea what all the errors meant, but after the next log in.
it runs at 2.8 and works great... thomas perl: fixed a lot of bugs.

---

