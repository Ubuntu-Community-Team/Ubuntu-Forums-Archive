---
title: "KISMET show error?"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by thiensa on 2008-03-31
when i run KISMET, have a error display

kismet: Depends: libgmp3c2 but it is not installable
          Depends: wireshark-common but it is not going to be installed
E: Broken packages


is this meaning? help me !

---

### Post by ngoctuss on 2008-03-31
i'm too, i don't know how to run kismet in ubuntu? every show we?

---

### Post by ngoctuss on 2008-03-31
help our please!

---

### Post by ngoctuss on 2008-03-31
**RUN KISMET **
Server options:  none
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
FATAL:  Unable to set up pidfile /var/run//kismet_server.pid, couldn't open for writing: Permission denied[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...

i don't know what error is?

---

### Post by CityofAsh on 2008-06-12
you need to run kismet as root

try 
```
sudo kismet
```

---

### Post by openflame06 on 2008-06-21
The pid error you had may not always go away when running as root (i.e. sudo command).

For some reason kismet has problems with user permissions - to prevent errors such as PID open, FATAL could not dump file etc this is how to do it.

Find kismet.conf usually located in /usr/local/etc/kismet.conf or /etc/kismet/kismet.conf. There is a line 

# User to setid to (should be your normal user)
suiduser=youruserhere


Use kate to open the file and edit it. This can be done by navigating to the directory then running kate file.conf Example here:


beau@beau-laptop:/$ cd /usr/local/etc
beau@beau-laptop:/usr/local/etc$ ls
ap_manuf      kismet.conf   kismet_drone.conf
client_manuf  kismet.conf~  kismet_ui.conf
beau@beau-laptop:/usr/local/etc$ sudo kate kismet.conf

Change the bit that says your user here, to your current username you use to logon. This line was shown above. In the code just used I have used ls to demonstrate how you can be sure kismet.conf is in the directory you are in.

Once you have changed the user, save the file and try to run kismet.

If you have PID problems, or unable to dump messages make sure you are in the users home directory - because its a directory that user CAN write to.

Note as well, if you installed kismet from the repos - you are missing a vital component libpcap (packet capture library) without this kismet will run, but it is pretty much useless.

Aptitude wont install libpcap when you install kismet, because ultimately, it is not a dependency for kismet.

To install libpcap run:
sudo aptitude install libpcap-dev

thiensa - if you did compile from source you must have forgot to make the dependencies when compiling, because that is what the error is about. Make sure you do these steps if compiling from source:
./configure
make
make dep
sudo make install

Also -seeing that those are MP3 libraries i would assume that either the package you have was setup for text to speech conversion or something beyond what you probably want out of kismet. But i may be wrong.

That should get you out of trouble :-) I hope. If i can think of other stuff i'll edit this post

---

