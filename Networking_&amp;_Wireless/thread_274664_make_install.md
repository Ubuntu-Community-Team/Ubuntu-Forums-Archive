---
title: "make install"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by ckonrad on 2006-10-10
i am trying to install ndiswrapper because i realized that what i downloaded from synaptic really wasn't the most recent version.

I tried sudo apt-get install ndiswrapper and sudo aptitude install ndiswrapper, and those commands did not work, it just said that there was no ndiswrapper package available.

So i just went to the ndiswrapper site at sourceforge and downloaded it and now i am trying to build it. After extracking the tar i go to the ndiswrapper directory and follow the directions to 'make' and 'make install' as root and my terminal tells me that -bash: make: command not found

why would it do that?

---

### Post by pay on 2006-10-10
You need to install make. sudo aptitude install make would install it but I would use ```
sudo aptitude install build-essential
```

---

### Post by TheWizzard on 2006-10-10
but why do you need the most recent version?
it will automatically appear on your pc once the ubuntu team has tested it and integrated it with the other ubuntu packages. 
if you want a latest version of your software, use a bleeding-edge distro. if you want a stable box (with pretty recent versions), use ubuntu

---

