---
title: "Waiting for wireless key.."
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Majorix on 2007-07-16
My wireless usually doesn't connect.

I investigated how the computer tries to connect to the network a bit. When I hover over the network icon with my mouse when the computer is trying to connect to the wireless, it usually says "waiting for the wireless key".

I believe this network key the computer is waiting for is the one that it asks me to enter for the keyring.

How can I fix this? Is there for example a way to set the computer so that it will automatically fetch the key without asking me? Donno if that will be the fix but I could only think of that...

Thanks a lot beforehand.

---

### Post by ubuntu.daemon on 2007-07-16
so is it your keyring-manager doesnt come up?  or do you just want a prog so that you dont hae to enter the keyring password every time you log in??  I believe its called Pam-keyring...

---

### Post by Majorix on 2007-07-16
No no the keyring-manager comes up and asks for the key, thats fine. But I believe that the computer won't recognize that I actually entered the key for it.

Pam-keyring you say? Ok I will look that up and post back with info. Thanks.

---

### Post by Majorix on 2007-07-16
Yes it seems to work I guess. I can't be sure because I only tried twice.

Anyways, for people having the same trouble, do this:
```
sudo apt-get install libpam-keyring
```

Thanks a lot :)

---

### Post by Majorix on 2007-07-16
Nope, forget what I said. After 3rd reboot it doesn't seem to work.

Can anyone help?

---

### Post by Majorix on 2007-07-16
Ok I have done the installation of the libpam-keyring in a wrong way. Following a blog, I came across this:
> 1) sudo gedit /etc/pam.d/gdm
2) Append the line: @include common-pamkeyring

After I try that it doesn't ask me about the key anymore. And it also doesn't say "waiting for the network key" or whatever it was saying. BUT! It doesn't connect to the network either. Now it says "attempting to join the network" but can't join.

Any ideas?

---

### Post by usama_ah on 2008-04-20
I just wanted to add that I was having this same problem. I did what Majorix posted and now I'm stuck at the "attempting to join" part as well.

---

