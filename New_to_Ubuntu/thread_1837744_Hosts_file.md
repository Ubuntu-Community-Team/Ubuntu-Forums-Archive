---
title: "Hosts file"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by Old-un on 2011-09-02
Looking for a tutorial which shows how i might use the Hosts file to prevent undesireable sites from being loaded into the browser.

---

### Post by agillator on 2011-09-02
The format of the hosts file is simple: IP address | tab | url. So what you want to do is redirect the 'bad' site to somewhere else. For example you might use 127.0.0.1 /some/bad/site. With that entry, if a url of /some/bad/site were asked for, it would actually go to the localhost (127.0.0.1).

---

### Post by Old-un on 2011-09-02
When i open up a terminal and type: sudo gedit /etc/hosts i am then required to enter my password but when i do the output is: Sorry try again?

Is this because i entered my user password and not the root password? If so how do i set up a root password?

---

### Post by Wim Sturkenboom on 2011-09-02
> **Old-un said:**
> Is this because i entered my user password and not the root password? If so how do i set up a root password?
No, it's not. sudo asks for *_your_* password.

Try in a terminal with *_sudo nano /etc/hosts_* or *_sudo vi /etc/hosts_*. nano is considered the easier editor for beginners ;)

---

### Post by bodhi.zazen on 2011-09-02
Take a look at this script :

[http://bodhizazen.net/Tutorials/adblock](http://bodhizazen.net/Tutorials/adblock)

---

### Post by Old-un on 2011-09-02
Job done folks! Thanks for the help

---

