---
title: "problems with google earth 5 in ubuntu"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by carrierpilot1357 on 2009-04-16
ok. I installed google earth 5 onto my ubuntu 8.04 system by typing in
```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin
```
in terminal ( I got the code off the internet) and it installed fine, and then I started it, the splash screen showed, and I saw the program for one second and then it just crashed or something and closed by itself. Should I try reinstalling it? if so, how do I uninstall it?

thanks in advance, M.B

---

### Post by neofreud on 2009-04-16
you uninstall it using the package manager Synaptic. 

Sometimes when you get a quick flash and then a crash then it could be a problem with the video driver. it could be a bug?? Search to see if anyone had this similar issue and how they fixed it? 

Sorry I couldnt be of more help. Lol but I had a similar problem with a twitter client and it turns out it was a bug problem. 


Good Luck

---

### Post by billgoldberg on 2009-04-16
> **carrierpilot1357 said:**
> ok. I installed google earth 5 onto my ubuntu 8.04 system by typing in
```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin
```
in terminal ( I got the code off the internet) and it installed fine, and then I started it, the splash screen showed, and I saw the program for one second and then it just crashed or something and closed by itself. Should I try reinstalling it? if so, how do I uninstall it?

thanks in advance, M.B

I wouldn't advise using that bin file, remove it and then enter this command in a terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install googleearth

```

This will add the medibuntu repository to you system, and will allow you to use apt to install and manage it (aka you will get updates for it from the update manager).

Try it and then tell if it still fails.

(ps the medibuntu repository has lots a codecs you might want, check out the packages "win32codecs" and "non-free-codecs" in synaptic.)

--

Should it still fail, download remove your videocard driver and use envyng (google it) to install the newest driver for you video card.

Turning off desktop effects (system -> preferences -> appearance, last tab) could also help.

---

### Post by oldos2er on 2009-04-16
Chances are it installed fine, as you said. It could be a problem with your video card or drivers; Googleearth requires 3d hardware acceleration. What make/model is your video card?

---

### Post by Therion on 2009-04-16
Open a Terminal and Copy and Paste the following:
```
cd googleearth
mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8
```
And try running the application again.

---

### Post by carrierpilot1357 on 2009-04-16
I have nvidia geforce 5 with 256 vram and 3d acceleration. google earth works fine in windows though.

---

### Post by carrierpilot1357 on 2009-04-17
for:billgoldberg 
ok, I used the code you gave me, but it still crashed. it even crashed after I disabled advanced desktop effects.

---

### Post by carrierpilot1357 on 2009-04-17
for therion: I tried that but it said that there is no such directory.

---

### Post by YuccaNel on 2009-04-18
My first post and am a new Ubuntu user :) 

I post here coz the same happened to me.  As for this being my first post I can say I am hooked on Ubuntu. I tried some other distros but had issues ranging from wifi (even previous 8.10) and some issue with programs I needed. The bets 9.04 installed fine runs smoothly, boots fast and is the first distro that gave me no issues. WD all and ty.:D

---

