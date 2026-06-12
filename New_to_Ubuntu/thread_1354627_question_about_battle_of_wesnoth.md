---
title: "question about battle of wesnoth"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by Volcom350Z on 2009-12-14
I have ubuntu 8.04 which comes with battle of wesnoth 1.4.5 , I am trying to download 1.6.5 version of battle of wesnoth, does anyone have that version, and know the process of how to download/update this game. I tried to download the game of the website, but I think I didnt make it work properly.

---

### Post by talsemgeest on 2009-12-14
> **Volcom350Z said:**
> I have ubuntu 8.04 which comes with battle of wesnoth 1.4.5 , I am trying to download 1.6.5 version of battle of wesnoth, does anyone have that version, and know the process of how to download/update this game. I tried to download the game of the website, but I think I didnt make it work properly.
Download the tar.gz file, then extract it. Open up a terminal, run this: ```
sudo apt-get install libboost-iostreams1.38-dev libboost-regex1.38-dev liblua5.1-0-dev libfontconfig1-dev libpango1.0-dev libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev libsdl-ttf2.0-dev zlib1g-dev libdbus-1-dev cmake libfribidi-dev
``` to install the requirements for the game. Then cd into the extracted directory, something like ```
cd ~/Downloads/wesnoth1.4.5
``` substituting in the directory of your extracted files.
Now type ```
mkdir build
cd build
cmake ..
```
Wait for the process to finish, before typing ```
make
sudo make install
```

---

### Post by Volcom350Z on 2009-12-14
sweet im dling the file ill let you know if it works.

---

### Post by talsemgeest on 2009-12-14
> **Volcom350Z said:**
> sweet im dling the file ill let you know if it works.
I hope it works for you. I made that list of dependencies with the developers (svn) version, so hopefully it will work with the release.

---

### Post by Volcom350Z on 2009-12-14
yeah that would be amazing I will have the answer in 20 mins for you!!

---

### Post by talsemgeest on 2009-12-14
Sorry, there is one that I forgot. I didn't add it to the list because I already had it installed when I built wesnoth. In addition to the packages in my first post, you should also install```
sudo apt-get install build-essential
```

---

### Post by Volcom350Z on 2009-12-14
could not get lock /var/lib/dpkg/lock open 11 resources unavailable


this is what it says when i try the first command

---

### Post by northern lights on 2009-12-14
Close update- and package-manager, do not run any other aptitude/apt-get/dpkg jobs while installing those packages.

---

### Post by Volcom350Z on 2009-12-14
hmmm nothing was on though at the time I was trying it.

---

### Post by talsemgeest on 2009-12-14
> **Volcom350Z said:**
> hmmm nothing was on though at the time I was trying it.
Try rebooting then try it again.

---

