---
title: "ubuntu server preperations"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by Pevichaey5 on 2009-12-24
hey
its been a while since i have used ubuntu, but i am changing from a windows server to a ubuntu server

is there anything in particular i need to know?

i know the server edition is text based which i am prepared for (kind of) and will be installing apache, mysql, php, quake 3, and a smtp server using these commands

sudo tasksel install lamp-server
sudo apt-get install postfix 
sudo dpkg-reconfigure postfix

however i am not sure which commands i will need in terms of updating my server, i have previously done it using nautilus

cheers

---

### Post by CharlesA on 2009-12-24
I use apt-get to do updates, I think you can do aptitude and another one.

I use these:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Pevichaey5 on 2009-12-24
just what i was after

thanks dude

---

### Post by ayenack on 2009-12-24
When you're installing from the Ubuntu Server CD you can chose to install the LAMP during install another thing you'll most likely want to install is SSH which also is an install option during install.

These are good starter points.

Setting up SSH essential reading. You'll want to use keys.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Ubuntu Server Guide.

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Securing Ubuntu Server.

[https://help.ubuntu.com/8.04/serverguide/C/security.html](https://help.ubuntu.com/8.04/serverguide/C/security.html)

---

### Post by redcarpet on 2009-12-24
FWIW

I have installed ssh on my koala server and used a product called denyhost or hostdeny (can't remember) and it didn't do what I wanted, anyway, I got rid and put in **BLOCKHOSTS** and it works really well. DENYHOSTS works like a DOORMAN at a club - if he knows you - then you can come in. BLOCKHOSTS works like a MAITRE'D in a restaurant - if he don't like you he throws you out. This was better for me as I log in with different IP's every day and it was a real ball-ache trying to administer that.

hih

---

### Post by iMisspell on 2009-12-24
If you ever need a torrent app, rTorrent works nice on a server.

Depending on how much time your gonna spend at the servers command line, this thread might be helpful.
[http://ubuntuforums.org/showthread.php?t=1301429](http://ubuntuforums.org/showthread.php?t=1301429)

Depending on your needs and desires, you can install GUI software to a server.
_[google "ubuntu+server"+gui]("http://www.google.com/intl/en/#q="ubuntu+server"+gui")_


_

---

### Post by maddog39 on 2009-12-24
You might find some of the articles over at howtoforge.com of some use also. Looks like you want to make a web/mail server of sorts based on your first post.

[http://howtoforge.com/howtos/linux/ubuntu](http://howtoforge.com/howtos/linux/ubuntu)

---

