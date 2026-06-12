---
title: "How to use Ubuntu Software Center in 9.10"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by sngehl01 on 2009-11-02
Ok, I'm new to Ubuntu, I'm trying to download the Adobe Flash Plugin. I see a box with a yellow arrow on it. I click it, it goes to where I think I should be downloading it... but I don't see an install button. Any help?

Thanks

---

### Post by Earl_Maroon on 2009-11-02
It's probably because Flash isn't on a free license.

I don't know the Software Centre - it was about the first thing I uninstalled when I installed Karmic - but you can install Flash (and some other useful extras) using this command entered from a terminal (Applications>Accessories>Terminal) ```
sudo apt-get install ubuntu-restricted-extras
```
You'll then need to enter your password. After that it will install automatically.

---

### Post by sngehl01 on 2009-11-02
sweet i'll do that, thanks!

so you uninstalled the software center?

where can i learn more about using the terminal, and how it works?

thanks!

---

### Post by camaron1 on 2009-11-02
> **Earl_Maroon said:**
> It's probably because Flash isn't on a free license.

I don't know the Software Centre - it was about the first thing I uninstalled when I installed Karmic - but you can install Flash (and some other useful extras) using this command entered from a terminal (Applications>Accessories>Terminal) ```
sudo apt-get install ubuntu-restricted-extras
```
You'll then need to enter your password. After that it will install automatically.

Just for your information sngehl01 you might want to install the above with synaptic (System>administration>synaptic package manager) so you know what you are installing (flash plugin, mp3 and dvd codecs, etc)

---

### Post by todak on 2009-11-02
You probably do not have the **Multiverse** or **restricted** repositories enabled. Got to **System> Administration> Software Sources** and tick the boxes next to the the lines that have **(restricted)** and **(multiverse)** appended to them. The reload the repository info. Software Sources will ask you to do this. Then Open Software Center and you will be able to install.

---

### Post by sngehl01 on 2009-11-02
> **camaron1 said:**
> Just for your information sngehl01 you might want to install the above with synaptic (System>administration>synaptic package manager) so you know what you are installing (flash plugin, mp3 and dvd codecs, etc)

I already started it with terminal, but I'll start using synaptic from now on!

thanks

---

### Post by sngehl01 on 2009-11-02
> **todak said:**
> You probably do not have the **Multiverse** or **restricted** repositories enabled. Got to **System> Administration> Software Sources** and tick the boxes next to the the lines that have **(restricted)** and **(multiverse)** appended to them. The reload the repository info. Software Sources will ask you to do this. Then Open Software Center and you will be able to install.

they were ticked (checked), so I didn't have to enable them. I don't know why I couldn't find the install button. When I clicked file i couldn't click install there either.

---

