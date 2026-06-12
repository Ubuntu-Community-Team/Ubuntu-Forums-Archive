---
title: "PuTTY into Solaris, can't initialize Xserver"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by dreamer_nights on 2007-09-23
Hello,

I can PuTTY into my school's UNIX server just fine, but whenever I try and initialize a program it gives me this:

>  cannot connect to Xserver ''
// X server is not running
// Cannot initialize device driver.
// ERROR -- Unhandled exception caught:
Connection to hardware type X11dd failed

Any ideas? I've got the X11 forwarding checkbox ticked, runnung Windows XP with XMing in the background (don't really know if I've got XMing set up correctly...)

Thanks

---

### Post by magaltavor on 2008-05-20
if you have ubuntu installed it would more easy than this 

ssh -l USER -X -v IPADDRESS

i am sure everything will work Okay 

Cheers

---

### Post by eekrazyk on 2008-07-14
> **magaltavor said:**
> if you have ubuntu installed it would more easy than this 

ssh -l USER -X -v IPADDRESS

i am sure everything will work Okay 

Cheers

I'm having the same problem as the OP, only I'm running different apps.

I'm running Kubuntu 8.04 and ssh'ing to a Unix box.  I'm trying to run a design app, but I'm receiving the same type of error:

```

// cannot connect to Xserver '10.33.49.239:0'
// X server is not running
// Cannot initialize device driver.
//  Error: Connection to hardware type X11dd failed (from: Core/VDD/vdd 08)

```

I've tried running ssh with both the -X and the -Y options, but it still doesn't work.

Anyone have any ideas?

---

### Post by magaltavor on 2008-07-15
okay you just try the following : 
use rlogin to access the server :

rlogin server-ip  (if you don't have rlogin just : sudo apt-get install rlogin )
 do the folloeing on the server side :

export DISPLAY=workstationIP:0.0

on your workstation now do the following command : xhost +

now try to execute the application .

(commands are case sensitive )

beware if there is any problem then in your Xserver as the error is telling that mean that your server has been stopped .

Cheers

---

### Post by eekrazyk on 2008-07-15
still doesn't work

```

> xhost +
xhost:  unable to open display "10.33.49.239:0.0"

```
```

// cannot connect to Xserver '10.33.49.239:0.0'
// X server is not running
// Cannot initialize device driver.
//  Error: Connection to hardware type X11dd failed (from: Core/VDD/vdd 08)

```

:(

---

### Post by magaltavor on 2008-07-15
mean you have a problem in your server can you send specs please os distro and which Xserver installed .


Thanks

---

### Post by eekrazyk on 2008-07-15
I'm running Kubuntu 8.04.  I'm not sure what version of X it uses...

uname -a on the Sun box gives me the following:

SunOS 5.8 Generic_117350-18 sun4u sparc SUNW,Sun-Fire-V240 Solaris


It's probably worth stating that we have a Linux cluster we use to run other tools and apps.  Those run over ssh without a problem.

---

### Post by magaltavor on 2008-07-16
your issue , is a problem form your sparc machine that have install3ed on it solaris 8 can you check if you can come up a CDE session on the solaris machine. 

Regards

---

