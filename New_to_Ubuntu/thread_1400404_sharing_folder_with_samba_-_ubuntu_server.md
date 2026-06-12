---
title: "sharing folder with samba - ubuntu server"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-02-06
Hi, How do I share a folder with samba on ubuntu server? I have samba server installed. I just don't know what command or config file I need to change to share the folder without a GUI. Thanks

---

### Post by _uli on 2010-02-08
If you're now familiar with the config files, i recommend installing webmin.
Webmin is a management software that provides a web based GUI and allows you to manage your computer as well as your services with a web browser.

[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

I did my first samba setup with webmin and it turned out fine.

Do note that if you're not behind a firewall the webmin page will be accessible from the web. So check that your firewall settings and password are up to the standards.

---

### Post by bnhrobotics on 2010-02-08
Thanks for the tip. I am looking for a way to do it from the command line or which configuration files I need to edit.

---

### Post by _uli on 2010-02-08
The samba settings are in /etc/samba/smb.conf 

A basic share is done by adding the following to the end of the file.

```

[share]
        public = yes
        browsable = yes
        path = /media/share

```You have to reload samba after making the changes:

```
sudo /etc/init.d/samba restart
```You can read more about the basic options from here:
[https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Configuration%20-%20Manual](https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Configuration%20-%20Manual)

---

