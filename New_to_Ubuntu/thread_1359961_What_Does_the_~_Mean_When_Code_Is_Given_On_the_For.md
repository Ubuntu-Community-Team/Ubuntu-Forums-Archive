---
title: "What Does the ~ Mean When Code Is Given On the Forum?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by mulluysavage on 2009-12-20
My Guess is that the ~ means whatever directory the file is in. So I have to poke around and find where these files are and then put that where the ~ is?

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf

---

### Post by Barrucadu on 2009-12-20
~ refers to your home folder.

---

### Post by cartisdm on 2009-12-20
like said above, it's your home directory.  Example

$ mkdir ~/pulse-backup 

would mean

$ mkdir home/USERNAME/pulse-backup

---

### Post by bodhi.zazen on 2009-12-20
Not only that, but you can specify other people's $HOME as well

~user_2 is short for /home/user_2

works with tab completion as well :twisted:

---

