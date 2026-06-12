---
title: "Install FreeRadius"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by azelus on 2007-04-23
Guys,

anyone can help me to install freeradius with eap tls support?? I Have an error while install freeradius from repo and configure it.

Here my error : 

rlm_eap: Failed to link EAP-Type/tls: rlm_eap_tls.so: cannot open shared object file: No such file or directory
radiusd.conf[1]: eap: Module instantiation failed.
radiusd.conf[1893] Unknown module "eap".
radiusd.conf[1840] Failed to parse authenticate section.

Someone can help me??

Thanks

---

### Post by Starseed on 2007-04-24
I'm having the same problems. I also tried uninstalling and then installing from source but it says that I don't have Perl installed when I install from source.... even though I do.

---

### Post by azelus on 2007-04-25
So, did you know other program like freeradius that can install at ubuntu? Because I need radius server for authenticate my wireless access point.

---

### Post by karla on 2007-05-14
Azelus, I have the same problem ... Did you find a work around?
/Karla

---

### Post by silly.agent on 2007-06-05
hi azelus, starseed & karla,

looks like freeradius does not include the rlm_eap_tls.so library, because of licensing problems :( so there is no TLS support out of the box

see [http://www.mythi.cx/blog/debian_and_openssl.html]("http://www.mythi.cx/blog/debian_and_openssl.html")

the only workaround is to compile from source.
all the best.

sa

---

### Post by silly.agent on 2007-06-05
download latest source from freeradius.org

```

tar zxvf freeradius-1.1.x.tar.gz
cd freeradius-1.1.x/

dpkg-buildpackage -rfakeroot 
# might prompt you to install missing dependencies
# if so apt-get install pkg1 pkg2 ...
# compilation will take some time, just relax ;-)

dpkg -i freeradius_1.1.3-0_i386.deb

```

you should have now a working freeradius server with tls support
enjoy :D

sa

---

