---
title: "ssh private key, from putty to ubuntu"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by bp1509 on 2008-08-17
d

---

### Post by aminalid on 2008-10-09
I have the same problem, but i cant even find the id_rsa file.

i installed both openssh-server and openssh-client
```

$sudo apt-get install openssh-server
$sudo apt-get install openssh-client

```

I have a private/public key pair from putty too, which is working from putty on windows and putty on linux but not using
```

ssh username@host

```
it always prompts for password (not the pass phrase)

I also cant login using "Connect to server..." from Ubuntu GUI, it asks for rpassword too.

How should i use the private key form putty, please help.

---

### Post by aminalid on 2008-10-10
Ok i solved this using a hint from this post [http://ubuntuforums.org/showthread.php?t=471485]("http://ubuntuforums.org/showthread.php?t=471485")

The steps are:
1.Use an utility for Putty that is called PuttyGen ([http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html")) to convert the key to the open SSH format.

2. Create a file named id_rsa under ~/.ssh/ and paste the key text generated from PuttyGen there

3. Now SSH should ask for the pass phrase of the private key.

---

