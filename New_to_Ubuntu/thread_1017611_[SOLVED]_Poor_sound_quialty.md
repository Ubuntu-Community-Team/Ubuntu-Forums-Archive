---
title: "[SOLVED] Poor sound quialty"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by newlinuxuser2008 on 2008-12-21
I am trying to intall the realtek highdef drivers from
realtek.com for linux

and i am getting premission denied when trying to run make install

please help????

---

### Post by marshall.robert on 2008-12-21
Can I have a link to the page you are getting the drivers and instructions?

Also, I'm guessing you are not installing as root. Try installing with ```
sudo
``` infront of your commands.

---

### Post by newlinuxuser2008 on 2008-12-21
TheJoker@homecpu:~/Desktop/alsa-driver-1.0.18a-5.09$ make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/TheJoker/Desktop/alsa-driver-1.0.18a-5.09/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
install: cannot change owner and permissions of `/usr/include/sound': No such file or directory
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1
TheJoker@homecpu:~/Desktop/alsa-driver-1.0.18a-5.09$

---

### Post by newlinuxuser2008 on 2008-12-21
[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

---

### Post by marshall.robert on 2008-12-21
Run:
```
sudo make install
```
See how that goes. Should work.

---

### Post by newlinuxuser2008 on 2008-12-21
OMG
got everything working

sounds like 5.1 on HULU  -thank you so so much dude....-

---

### Post by marshall.robert on 2008-12-21
No problem :) 

Be sure to mark this thread as solved.

---

