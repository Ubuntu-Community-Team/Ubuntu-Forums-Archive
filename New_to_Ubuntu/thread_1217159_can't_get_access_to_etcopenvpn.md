---
title: "can't get access to /etc/openvpn"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Moe Z on 2009-07-19
Hi all,
        I want to copy some configuration files to /etc/openvpn. but i can't get access although i use sudo command. how can i do it? do i need to enable root account ?

---

### Post by hetx on 2009-07-19
sudo mv /path/file /etc/openvpn/

says no permission?

---

### Post by Moe Z on 2009-07-19
no, it's sudo cp /etc/openvpn /home/desktop
and it says file ignored or something.. like that :(
pls help and thx in advance :)

---

### Post by jerome1232 on 2009-07-19
You shouldn't need sudo to copy a file to your home directory, and that should be

```
cp /etc/openvpn ~/Desktop
```

If the above fails, what does this next command return (exact wording please, just copy the output from terminal and paste it in your post)

```
ls -l /etc/openvpn
```

---

### Post by The Cog on 2009-07-19
If you're trying to copy a file to the openvpn folder, the command would be:
**sudo cp filename /etc/openvpn**
If that doesn't work, please paste the exact command and response here so we can see what's going on.

---

### Post by Moe Z on 2009-07-19
total 8
lrwxrwxrwx 1 root root   17 2009-07-11 00:51 openvpn.conf -> skygate01.us.conf
-rwxr-xr-x 1 root root 1352 2009-07-11 00:33 update-resolv-conf
-rw-r--r-- 1 root root 1352 2009-07-11 00:33 update-resolv-conf~

here's output of ls -l /etc/openvpn

---

### Post by jerome1232 on 2009-07-19
So are you actually trying to copy files to /etc/openvpn or from /etc/openvpn.

remember cp works like this

cp **target** **destination**

if your trying to copy files out of /etc/openvpn then your need to make the command recursive by adding the -r option otherwise it will just refuse to copy the directory.

ie

cp **-r** /etc/openvpn ~/Desktop

---

### Post by Moe Z on 2009-07-19
sorry, i mis-posted. what i want is i want to copy some files to /etc/openvpn folder. the destination is /etc/openvpn
and my command is sudo cp filename /etc/openvpn

---

### Post by Moe Z on 2009-07-19
sudo cp config /etc/openvpn
cp: omitting directory `config'

it's the output when i copy files to openvpn folder :)

---

### Post by The Cog on 2009-07-19
So your source, config, is a directory and not a file. You probably want to copy a file in the config directory (or maybe several files?), not the config directory itself. Assuming it's one file you want to copy, use
**sudo cp config/filename /etc/openvpn**

Also, you can use **gksu nautilus** to get a graphical file manager with root permissions. Be careful with it as a mistake could trash your system.

---

### Post by Moe Z on 2009-07-19
d u mean i've to copy all files in that directory one-by-one? ok, i'll do it

---

### Post by Moe Z on 2009-07-19
yeah, it did... man thx to you, cog!

---

### Post by The Cog on 2009-07-19
Ah. For all the files, 
**sudo cp config/* /etc/openvpn**
would have done the trick. Too late though. Oh well.

---

