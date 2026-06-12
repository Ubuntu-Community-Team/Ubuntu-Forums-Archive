---
title: "Restarting leaves me without privileges"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Wormboy on 2009-05-03
I install Ubuntu, Everything works fine but then I turn it off and when I log back in I am without privileges, I can't even connect to the internet.
Interestingly when I open a terminal I notice that its changed from timothy@timothy-desktop to timothy@localhost.
I tried logging in as root but all I get is a blank screen with nothing but the cursor.
I am using Ubuntu 9.04 but this has happened with 8.10 only then it only happened when I restarted by pressing the reset button.
I've already had to reinstall 4 times because of this, any help would be greatly appreciated.

---

### Post by zvacet on 2009-05-03
I don´t know if this is work but try it anyway.Boot in recovery mode (you will see that option when you see grub) and type

```
nano /etc/hosts
```

and see if first two lines look like 

127.0.0.1 localhost
127.0.1.1 timothy-desktop

If not make them look like that.Save file and exit.If now everything is O.K. but you don´t have admin privileges then boot in recovery again and type 

```
adduser timothy admin
```

I think your username is timothy.If is different change it.If after all this you still have problems just ask and somebody will answer to you.

---

