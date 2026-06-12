---
title: "getting ppa for gpodder"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by DarinB on 2010-03-14
I am now using karmic, i went to gpodder for ubuntu to upgrade my gpodder. but am having difficulty understanding the instructions on how to add the ppa with the new karmic cli method. 
the instructions say 
 Step 2: Open a terminal and enter:

sudo add-apt-repository ppa:user/ppa-name

Replace ppa:user/ppa-name 

I can't tell what part do i copy from the karmic ppa below on the page.

---

### Post by Rocket2DMn on 2010-03-14
Do you have a link to the PPA you are trying to use?

---

### Post by zeroseven0183 on 2010-03-14
Checking the gpodder for Karmic in [https://launchpad.net/~thp/+archive/gpodder]("https://launchpad.net/%7Ethp/+archive/gpodder"), I think what should be typed in the terminal is
```
sudo add-apt-repository ppa:thp/gpodder
```

else, add
```
deb [http://ppa.launchpad.net/thp/gpodder/ubuntu](http://ppa.launchpad.net/thp/gpodder/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/thp/gpodder/ubuntu](http://ppa.launchpad.net/thp/gpodder/ubuntu) karmic main
```to your sources.list

---

### Post by DarinB on 2010-03-14
thanks I think i can now figure out what is the /user/ppa-name for the future thank you very much. 
I added it the old fashion way with software sources and the key. 
i will have to find something i need to try the new ppa karmic method. 
i guess the point of the new cli method is to not have to hunt for the key...

---

### Post by zeroseven0183 on 2010-03-15
> **DarinB said:**
> i guess the point of the new cli method is to not have to hunt for the key...

Yes, it made things easier.
...Our pleasure helping you. ;)

---

