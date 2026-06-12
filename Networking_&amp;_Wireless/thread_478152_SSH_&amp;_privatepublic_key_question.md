---
title: "SSH &amp; private/public key question"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by cygnus81 on 2007-06-19
Hi

I installed openssh-server on my machine, and I want to access it from outside for administration etc.

I don't think I quite understand the private/public key mechanism - I understand I need to put the public key on my machine (the server) and carry the private key with me to use it when logging in from any other computer (client). Is that right ?

If so, is there a way to secure the login procedure (and my server) but to allow me to connect from any arbitrary client without preparation (i.e carrying the private key) ?

Thanks

---

### Post by Mr. C. on 2007-06-19
See my posts starting here:

[http://ubuntuforums.org/showthread.php?t=333139&highlight=ssh+public+private+key+mrc&page=4](http://ubuntuforums.org/showthread.php?t=333139&highlight=ssh+public+private+key+mrc&page=4)

and read backwards if necessary.

MrC

---

### Post by cygnus81 on 2007-06-19
Thanks.

I have a couple of questions though:

Can ~/.ssh/authorized_keys (on the server) be a directory (with id_rsa.pub.1 id_rsa.pub.2 etc files in it) or should I concatenate id_rsa.pub's into it ?

Is there such a mechanism that allows secure login from clients without carrying a private-key around (because unlike a real-life key, its quite a hassle to carry such a thing around: usb sticks and such, remembering to erase it from the client afterwards, etc)? Or is that like having the cake and eating it too?

---

### Post by Mr. C. on 2007-06-19
The man page has that answer to your first question.  Man sshd_config shows:
>        ~/.ssh/authorized_keys
              Lists  the public keys (RSA/DSA) that can be used for logging in
              as this user.  The format of this file is described above.   The
              content of the file is not highly sensitive, but the recommended
              permissions are read/write for the user, and not  accessible  by
              others.

              If this **file**, the ~/.ssh directory, or the user's home directory
              are writable by other users, then the file could be modified  or
              replaced  by  unauthorized  users.   In this case, sshd will not
              allow it to be used unless the StrictModes option has  been  set
              to  ``no''.  The recommended permissions can be set by executing
              ``chmod go-w ~/ ~/.ssh ~/.ssh/authorized_keys''.

Regarding your second question, how the private key is accessed depends upon the client. For example, SecureCRT allows accessing the file by browsing.  You can also configure password as a fallback mechanism.

More importantly, consider when you are using an insecure system: how do you prevent a key logger from running, or other malware that reads your private keyfile as it is accessed (eg. virus checkers do just this)?

You have to assume that when using a public or insecure system, it is untrustworthy.  You shoiuld walk away from that system *assuming* everything you entered, accessed, or typed has been captured.

MrC

---

### Post by cygnus81 on 2007-06-19
Thanks for the man reference and the clarification. I'm guessing that it comes down to what you said - a public system is insecure.
Just a reflection.. So what is the point in remote administration ? Finding a secure public client sounds almost as hard as taking the train/bus/car/plain/spaceship to the physical site, isn't it ?

---

### Post by Mr. C. on 2007-06-19
> **cygnus81 said:**
> Just a reflection.. So what is the point in remote administration ? Finding a secure public client sounds almost as hard as taking the train/bus/car/plain/spaceship to the physical site, isn't it ?

They have these new-fangled personal gizmo's called laptops.

MrC

---

### Post by cygnus81 on 2007-06-20
Ouch ;)
#-o

---

### Post by Mr. C. on 2007-06-20
It was tongue-and-cheek.

Seriously, corporate users would have secured, or locked down laptops.  They connect remotely via VPN, and do not allow browsing local Windows networks, etc.

If you plan on doing any remote work, consider your own laptop.  Security is just no joke today.

MrC

---

### Post by cygnus81 on 2007-06-20
Actually I'm trying to make my home machine available for me from other places.
I am a student and I find myself copying files via FTP back and forth in order to work on the same versions while I'm home, at the campus or at my parents. So I wanted to stop all this waste of time and bytes and just make my machine a file-server only I can access.
But I understand its not really possible to be secure in public.. 

I did find this security issue pretty interesting though :-) .

---

### Post by Mr. C. on 2007-06-20
There are mechanisms that can be fairly effective on public computers to mitigate risk; its just a question of how much time, money, and energy you want to dedicate to the effort.  At some point, the economics change.

If you have reboot capabilities, you can certainly configure a live CD that is preconfigured for your needs.  Boot from the CD, and you have instant control of the PC and security.  Log in as you see fit.

Best of luck,
MrC

---

### Post by cygnus81 on 2007-06-20
Thanks.

---

