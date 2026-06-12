---
title: "Using sudo"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by MasterMind Karthik on 2010-07-11
How can I edit sudoers file so that I can include this path: /usr/local/apache/bin so that I can execute 
```
sudo apachectl start
``` without getting any error mesage like command not found?

Thanks;)

---

### Post by krtica on 2010-07-11
Try here:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

and some examples here:

[http://www.sudo.ws/sudo/sample.sudoers](http://www.sudo.ws/sudo/sample.sudoers)

---

### Post by Chame_Wizard on 2010-07-11
```
sudo su 
```
You will become *sudo* till you quit the terminal.

---

### Post by techunit on 2010-07-11
> **Chame_Wizard said:**
> ```
sudo su 
```
You will become *sudo* till you quit the terminal.
Or just ```
su
``` will work

---

### Post by Penguin Guy on 2010-07-11
> **MasterMind Karthik said:**
> How can I edit sudoers file so that I can include this path: /usr/local/apache/bin so that I can execute 
```
sudo apachectl start
``` without getting any error mesage like command not found?)
Seems an odd command to be running, Apache is usually started at boot time and shouldn't it be [FONT="Courier New"]/usr/local/bin/apache[/FONT]? Also, I would advise installing software through the repositories rather than manually.

---

### Post by marshmallow1304 on 2010-07-11
> **techunit said:**
> Or just ```
su
``` will work

Not unless the root password is enabled, which it isn't by default.

---

### Post by Rubi1200 on 2010-07-11
I believe the preferred method of simulating a root console is this:

```
sudo -i
```> The bottom line, is "sudo -i" is the proper command to run when you want a root shell that is untainted by the user's environment.[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

And see bodhi.zazen's response:

[http://ubuntuforums.org/showpost.php?p=6188872&postcount=5](http://ubuntuforums.org/showpost.php?p=6188872&postcount=5)

---

