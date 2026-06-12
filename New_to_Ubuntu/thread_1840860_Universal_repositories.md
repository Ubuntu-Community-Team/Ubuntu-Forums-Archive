---
title: "Universal repositories"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-09-08
After a LOOOONG night, I finally managed to install Lubuntu 11.04 and the Tor Browser Bundle on a flash drive. Now, I'm trying to install Polipo.

For that, I found this page:

[https://help.ubuntu.com/community/Tor#Install_Polipo_.28an_HTTP_proxy.29](https://help.ubuntu.com/community/Tor#Install_Polipo_.28an_HTTP_proxy.29)

Now, the first line says "Simply make sure you have the Universal repositories and then:"

Now, I'm sure that's very simple for the person who wrote the tutorial, and probably for most people here, but I don't have a clue how to do it, and haven't been able to find anything about it. Can anybody please tell me how can I do that?

Thanks in advance. :)

---

### Post by evilsoup on 2011-09-08
Does Lubuntu have the Ubuntu Software Center? If it does, fire that up and go 'Edit->Software Sources' and tick the appropriate box (you may as well tick the boxes for multiverse and restricted too, though check local laws before doing so as some of the software in those may be illegal in some place).

Otherwise, use Synaptic (SYSTEM->ADMINISTRATION->Synaptic Package Manager); when that's up and running, go to 'Settings->Repositories', then the steps are the same as above.

---

### Post by Inodoro Pereyra on 2011-09-08
Thanks evilsoup for the fast reply. Either way, I just found it using a different path.

For anybody else who may have the same problem, go System tools>Update Manager>Settings, and then follow the instructions here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Thanks again. :)

---

### Post by whatthefunk on 2011-09-08
In Lubuntu:
Menu > System Tools > Synaptic Package Manager

Once you open that up, you should be able to search for and install polipo.

Or, you could open a terminal (Menu > Accessories > LXTerminal) and enter the following:
```
sudo apt-get install polipo
```

---

### Post by Inodoro Pereyra on 2011-09-08
Yeah, once I could add the repositories, I did it on the terminal. For some reason, the synaptic package manager is terribly complicated for me. 

Thank you.
Now I have to finish the install...

---

### Post by whatthefunk on 2011-09-08
> **Inodoro Pereyra said:**
> For some reason, the synaptic package manager is terribly complicated for me.

I agree.  Its really confusing.  I never use it...

---

### Post by Inodoro Pereyra on 2011-09-08
Ok, now, I'm already starting to have problems installing Polipo. Gonna start a new thread...

---

