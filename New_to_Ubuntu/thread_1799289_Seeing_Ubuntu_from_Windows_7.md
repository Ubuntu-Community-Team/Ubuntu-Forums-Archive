---
title: "Seeing Ubuntu from Windows 7"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by Randy Flagg on 2011-07-07
Hey all, I trying get my ubuntu machine to come up in my windows 7 network list.  I have added a share and changed the workgroup in smb.conf but no luck.

I can connect to the ubuntu box by doing start and the computer name but it asks me for a user name and passwork.

I would like this computer and its share to come up with access without putting user or pass.

Any ideas?

---

### Post by terrykiwi83 on 2011-07-07
Am pretty sure in windows you can right click on the share and MAP it at login, as well as having it remember the password? (correct me if am wrong haven't used windows for some time).

Also post the output of your smb.conf fle

---

### Post by DutchLoki on 2011-07-07
You can either configure samba for this or just map an network drive. I would just map a network drive for this.

[http://www.watchingthenet.com/automatically-connect-to-folder-shares-during-startup-in-windows.html](http://www.watchingthenet.com/automatically-connect-to-folder-shares-during-startup-in-windows.html)

---

### Post by Randy Flagg on 2011-07-07
I got it to work perfectly on xubuntu 10.04 machine but The unbuntu 11.04 machine still doesn't come up in my list of computers. 

I think it might be something to do with the netbios name field. I put it under share in the xubuntu smb.conf,  but for some reason I have it under global four ubuntu

---

### Post by DutchLoki on 2011-07-08
can you ping the ubuntu machine from the other machines? 
does the ubuntu machine get an ip adres?

---

### Post by Morbius1 on 2011-07-08
> I think it might be something to do with the netbios name field. I put  it under share in the xubuntu smb.conf,  but for some reason I have it  under global four ubuntuIt should be under the [global] section. 

The top 5 reasons for not being able to see a Linux Samba share - in no particular order:

(1) The name of your machine is too long.
I'm guessing you already know it has to be 15 characters or less in length or else you wouldn't have a "netbios name" in your smb.conf.

(2) nmbd isn't running.
TO check it:
```
sudo service nmbd status
```To Start it:
```
sudo service nmbd start
```(3) Samba's not running:
Same commands as above but with smbd instead of nmbd

(4) Firewall on Ubuntu is getting in the way.
Disable it and see if you can connect.

(5) The entire path to the shared resource has to allow remote access.

Let's say you have a guest share on the ubuntu box at /home/randy/Documents.

/home/randy/Documents needs to be drwxrwxrwx
/home/randy needs to be drwxr-xr-x
/home needs to be drwxr-xr-x

---

### Post by Randy Flagg on 2011-07-08
> **Morbius1 said:**
> 
(1) The name of your machine is too long.
I'm guessing you already know it has to be 15 characters or less in length or else you wouldn't have a "netbios name" in your smb.conf.


well ^^^^^^ that could be an issue.

That works but a heads up to anybody else trying this Windows wouldn't put the ubuntu machine name in its list of computer until I did a start button \\ubunutumachine and put it my username and password.  This seems to make it permanent.

---

