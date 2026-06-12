---
title: "Setting up Eubuntu Server as an Internet Server"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by gperk on 2007-10-30
Hi,

I am intending to use edubuntu as a Internet (proxy?) server for a school, to start there will be around 12 computers connected (mainly W2000 and XP), no thin clients. I just installed the latest server version, 7.10.
I mainly want to create a web filter to protect against the students accessing adult content.

I would also like to set up user names and passwords for all the students so they have to log on before they can access the Internet. 

Can anyone tell me how to do this or where I can find instructions?

Also, something went wrong during installation with installing all the software, After installing, it would only boot to the command line (bash?). I used aptitude to install the listed "not yet installed software" which made sense to install. The things which did not work were moodle (which I suspect is not important) and ./pool/main/f/foomatic-db/foomatic-db-20070919-Oubuntu3_all.deb. Error was something about the checksum. This is not an issue right now (as far as I know) and I think this has to do with printing but I don't know how to correct it.
Edubuntu now boots to the GUI. 

Thanks very much for any help you can offer on these questions.
Greg
__________________

---

### Post by vol_freak on 2007-11-21
gperk, I'm looking at doing something similar. Did you ever get this setup. I was considering using squid and dansguardian but I'm still thinking through the process of having users login to be able to access the internet.

---

### Post by Blutack on 2007-11-21
Erm, you probably don't want edubuntu for what you are trying to do.  It includes a lot of packages which aren't neccessary for a server, so you won't get maximum performance.  You basically want Dansguardian, and something called a Captive Portal (which forces students to a login before allowing them anywhere else on the net).  I found one here
[http://nocat.net/](http://nocat.net/) and another (better looking one) here [http://dev.wifidog.org/](http://dev.wifidog.org/)
it is originally for WIFI hotspots but should work fine for you.  I'd recommend wifidog.
As much as I love ubuntu, you might want to look at a distro such as smoothwall, which is specifically tuned for this sort of thing and integrates dansguardian and captive portal (as an addon).  Good luck!

---

### Post by gperk on 2007-11-21
Hi, 
Thanks very much for the replies, and no, I never did get it working. 
Also thanks for the tips, I will pass them on to the one who has taken on the job now. 
Greg

---

