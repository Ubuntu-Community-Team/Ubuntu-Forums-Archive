---
title: "networking from the command line"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Loonux on 2007-04-22
Due to this problem with feisty ([http://ubuntuforums.org/showthread.php?t=414723](http://ubuntuforums.org/showthread.php?t=414723)) I need to get my laptop working internet access from the command line.
Ive managed to connect to my Wireless lan using wpa_supplicant, its connected well and i can ping the router. I cannot, however, download anything via apt-get. I just get 'could not resolve ....' errors. liewise if i try to ping google.com or bbc.co.uk it gives me the same message about unknown host.

Im assuming this is a DNS issue? thing is, i dont know how or where to set the DNS for the machine, which should just be my router (10.0.0.222).

Can anyone offer me a helping hand here please?
Cant even get to the joy of an installation until i crack this. lol

thanks

---

### Post by heimo on 2007-04-22
edit /etc/resolv.conf, add a line like this (and remove if there are others beginning with "nameserver":
```
nameserver 10.0.0.222
```

---

### Post by Jussi Kukkonen on 2007-04-22
The obvious *System -> Administration -> network* works too.

---

### Post by heimo on 2007-04-22
> **Jussi Kukkonen said:**
> The obvious *System -> Administration -> network* works too.

Which is fine, but not a command line. :)

---

### Post by Loonux on 2007-04-22
> **heimo said:**
> edit /etc/resolv.conf, add a line like this (and remove if there are others beginning with "nameserver":
```
nameserver 10.0.0.222
```

Thanks. there is no resolve.conf in /etc/
should i just create a new file with that one line?

---

### Post by heimo on 2007-04-22
Yeah, you can create it and it should start working immediately.

---

### Post by chili555 on 2007-04-22
> Thanks. there is no resolve.conf in /etc/

Nope. You cannot create a file /etc/resolve.conf and have this work, ever. The relevant file is **/etc/resolv.conf** without the e.

Usually, when you get an empty file or new file when editing, it's because you have mis-typed or mis-spelled something; a common error.

I have done it myself...twice....today!

---

### Post by heimo on 2007-04-22
Good call. Using tab completion minimizes risk of mistyping filenames.

---

### Post by Loonux on 2007-04-22
I have a directory called resolveconf, but there is no resolv.conf file at all!
inside resolvconf there is another dir called update-libc.d

this is from the 7.04 livecd btw

---

### Post by heimo on 2007-04-22
And the file where nameservers go, is in the /etc directory. /etc/resolv.conf. This should make it:
```
sudo sh -c "echo nameserver 10.0.0.222 >> /etc/resolv.conf"
```

---

### Post by Loonux on 2007-04-22
OK, progress!
I created resolv.conf using the above command (thanks btw!). I can now ping the router and if i do

ping google.com

it resolves the name to an IP, but i still get destination host unreachable.
also if i do 

apt-get update

i get messages saying "couldnt connect to archive.ubuntu.com" and same for all the other ubuntu sources.
What have i not done here? lol.

Thanks

---

### Post by heimo on 2007-04-22
Does your ```
route -n
``` show default route to your gateway?

This adds your router as default gateway, using first ethernet interface:
```
sudo route add default gw 10.0.0.222 eth0
```

---

### Post by Loonux on 2007-04-22
lol. Im SURE i added that in and double checked it already!

BUT, having confirmed it wasnt there then added it in, its now working.

Thanks for you help mate.
FGLRX drivers downloading as we speak! :)

---

