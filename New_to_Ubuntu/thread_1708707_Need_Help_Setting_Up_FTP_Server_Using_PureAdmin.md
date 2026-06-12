---
title: "Need Help Setting Up FTP Server Using PureAdmin"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by seventhsamurai on 2011-03-17
Hi Guys

Bit of a novice here. I'd really appreciate your help. I'm trying to set up an ftp server so that a guy from outside my network can log in and upload some files. I am running Ubuntu 10.10.

So following some online instructions which have confused me severely, I have installed PureAdmin and PureFTPd. I set up a user account via PureAdmin and a password. I am on an internet connection using an static IP and the computer is hooked to the connection via a router. I have ensured via the router configuration that ports 20 and 21 forward to my computer specifically.

Now, I go to a machine that is outside my network, key in my IP address, login, pass via an ftp client, but it keeps telling me that authentication has failed. I checked the log on PureAdmin and it too recognizes an attempt at an incoming connection from the correct IP address but says Authentication Failed for User.

What am I doing wrong? I would really really appreciate your help.

Thanks.

---

### Post by seventhsamurai on 2011-03-17
Seriously? Nobody has a clue?

---

### Post by Finnius on 2011-03-17
G'day,

Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

The guy uses ProFTP.
Apparently it has a GUI, so nice and easy to setup!
I haven't tried it though.

Hope it helps

---

