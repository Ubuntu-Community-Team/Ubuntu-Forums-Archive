---
title: "Key-based SSH login only works in Unity but not in Fluxbox"
date: 2015-09-18
forum: Networking &amp; Wireless
---

### Post by spupy on 2015-09-18
I'm inside the company's internal network and use SSH to login into a couple of test servers. The login is key-based and passwordless, but I cannot modify the server-side SSH configuration. Passwordless login works great in Unity under Ubuntu 14.04.  

I installed Fluxbox, which is my preferred WM. In Fluxbox I can't login the same way. The error message is "Permission denied (publickey)." SSH's verbose settings shows that it's looking for a private key under "~/.ssh/id_rsa" and couple of others, then fails. The reason it fails is that the key is named 'Firstname_Lastname' instead of 'id_rsa'. If I explicitly specify the key to use or rename the file to 'id_rsa' I can login, but it asks for the key's passphrase.  

So basically the question is, why does this work under Unity but not under Fluxbox? What is the Unity session starting that makes the key-based passwordless login work? In a more angry tone, why FFS does SSH's correct operation depend on some program from the graphical environment? 

Thanks in advance for any tips and help.

---

### Post by Lars Noodén on 2015-09-18
Well, the way Unity does it is a bit abnormal.  You'll run into problems when you have more than 6 keys:
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/1195911](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/1195911)

It's been a long while since I've used Fluxbox, I used to use it, but you might try the normal way of loading keys with the agent using [ssh-add](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-add.1.html).  

```

ssh-add /path/to/some/key_rsa

```

You have to have an agent running for that to work but then it is only necessary to enter the passphrase once and thereafter you can reuse the same key until you log out of Fluxbox.  Fluxbox seems to start with an agent so that should work.

---

