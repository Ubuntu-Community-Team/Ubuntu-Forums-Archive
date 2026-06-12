---
title: "Unable to ssh from mac os x to Ubuntu 6.06"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Herbert.Korte on 2006-08-03
I am able to ssh from Ubuntu 6.06 to mac os x but not conversely. I get the following error message:
ssh: connect to host 192.168.... port 22: Connection refused.
Both machines are part of a lan behind a fire wall. Moreover, I would like to be able to print directly from the mac. However, the printer has a parallel port and is hooked up to the PC containing Ubuntu 6.06. It would be nice if I could get the mac to see the printer. I really would appreciate some help with this. Thanks

Cheers Herbert

---

### Post by ylixir on 2006-08-03
> sudo apt-get install ssh

easier than you thought eh?

which begs the question...why isn't ssh installed by default?

---

### Post by Bicx on 2006-08-04
Seriously, why is it not installed by default? I just installed the Ubuntu Server 6.06 and SSH was not fully installed, which prevented me from being able to use ssh to log in from another box.

---

### Post by ylixir on 2006-08-05
yeah, it's a little bizarre.  it's the only distro i think i've ever seen that doesn't install it by default.  i can see having it turned off by default for security reasons or something, but why would you not even have it installed?  it's not like it's a huge chunk of hard drive space or anything.

---

### Post by ranf on 2006-08-06
Ubuntu has a "No open ports" policy for the default desktop installation.

---

### Post by ylixir on 2006-08-07
aah.  that's a good reason then ;-)

---

### Post by Herbert.Korte on 2006-08-07
Thanks, that helped. Herbert

---

