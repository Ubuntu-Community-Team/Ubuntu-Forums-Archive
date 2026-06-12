---
title: "How to start at boot a program for an user, without GDM and XORG?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-14
Hello,

I have a runing box, headless, and would like to start skype monitorless, headless. 

xfvb-skype is my command to start

Any ideas? 

thanks

---

### Post by shairozan on 2009-12-14
Hey there, 

When the system boots, it goes through a series of applications and starts them. The only way it knows to do this is to run through a series of files that correspond to layers in startup. 

If you look at the /etc folder you'll see some files called rc0.d -rc.local. 

These tell the system what to start and how to do it, but the only one you'll want to mess with is rc.local. What you'll want to do is enter any commands you would like into this file (before the exit 0) and save it. 

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

xfvb-skype

exit 0
```

for example. It's not the cleanest way to do it, but I haven't had any issues with it to date.

---

### Post by LowSky on 2009-12-14
skype is a GUI based program based on Qt, so running it without X11 is going to be impossible.

---

### Post by frenchn00b on 2009-12-14
> **LowSky said:**
> skype is a GUI based program based on Qt, so running it without X11 is going to be impossible.

fake X11 works fantastic. You should try.

 

cat /usr/bin/skypenox 
```
#!/bin/sh


killall -e skype
 
killall -e skype Xvfb 

 Xvfb :6 & 


while [ 1 ] ; do 

 DISPLAY=:6 ; export DISPLAY ; skype 



killall -e skype  

sleep 1s
beep



done 

```

---

### Post by frenchn00b on 2009-12-14
> **shairozan said:**
> Hey there, 

When the system boots, it goes through a series of applications and starts them. The only way it knows to do this is to run through a series of files that correspond to layers in startup. 

If you look at the /etc folder you'll see some files called rc0.d -rc.local. 

These tell the system what to start and how to do it, but the only one you'll want to mess with is rc.local. What you'll want to do is enter any commands you would like into this file (before the exit 0) and save it. 

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

xfvb-skype

exit 0
```

for example. It's not the cleanest way to do it, but I haven't had any issues with it to date.

will it run as root?
rc0.d -rc.local. 


I tried /etc/rc2.d/S99startskypenox
chmod +x /etc/rc2.d/S99startskypenox
 but it starts it as root, and root is not secured at all to do internet.

---

