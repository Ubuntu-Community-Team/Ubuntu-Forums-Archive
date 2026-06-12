---
title: "Starting and stoping apache and mysql?"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Jragon on 2010-12-24
Hello,

I need some help. I reasantly insalled lampp, i had installed it manulay befor. And i dont know how to stop apache i think its:
sudo /etc/init.d/apache2 stopBut i dont know how to stop it from starting up everytime i reboot. I want lampp to start instead:
/opt/lampp/lampp start

Thanks

Jragon

---

### Post by Jragon on 2010-12-24
Anyone?

---

### Post by |Eric| on 2010-12-24
you have diffrent options most services have entries in /etc/rc.d
but just in case you can try with the --help option on their respective services 
apache is httpd and mysql is mysqld 
or you can just kill it :P  like killall  httpd and killallmysqld  but thats a bit harsh 

anyway heres what i found in the apache docs
```
apachectl -k stop   
``` 
here is what i found in mysql doc 
```
mysqladmin shutdown
```

---

### Post by |Eric| on 2010-12-24
also note if you dont want to sart the servers automaticaly you may need to remove the entries in /etc/rc.d

---

### Post by sandyd on 2010-12-24
> **Jragon said:**
> Hello,

I need some help. I reasantly insalled lampp, i had installed it manulay befor. And i dont know how to stop apache i think its:
sudo /etc/init.d/apache2 stopBut i dont know how to stop it from starting up everytime i reboot. I want lampp to start instead:
/opt/lampp/lampp start

Thanks

Jragon
```

sudo update-rc.d -f [name_of_init.d_entry] remove

```

[name_of_init.d_entry] refers to the name that its shown as in /etc/init.d

i.e.
```
sudo update-rc.d -f apache2 remove
```

---

### Post by Jragon on 2010-12-30
Ok, so how do i make LAMPP start automaticly?

---

### Post by Jragon on 2010-12-30
Also there is rc0.rd, rc1.rd, ect up to rc5.rd, there all the same.

---

### Post by stmiller on 2010-12-30
> **|Eric| said:**
> also note if you dont want to sart the servers automaticaly you may need to remove the entries in /etc/rc.d

Eek no!

```
sudo apt-get install sysv-rc-conf
```

```
sudo sysv-rc-conf
```

There you can press the space bar to disable services from each run level.

[http://scottlinux.com/?p=470](http://scottlinux.com/?p=470)

Cheers,

---

### Post by Jragon on 2011-01-04
How do I get LAMPP to auto start? And I cant seem to stop mysql from auto starting.

---

### Post by Jragon on 2011-01-16
Anybody?

---

