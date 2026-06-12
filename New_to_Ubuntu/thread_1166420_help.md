---
title: "help"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by cowboy7305 on 2009-05-21
I have just moved back to ubuntu 8.10 and iam trying to load frostwire 
i have downloaded it to my desktop ,when i try to load it 
it comes up with a message telling me only one management tool is allowed to run at the same time
i dont have any other tools runing
any help please

---

### Post by uupreti on 2009-05-21
Same thing happened to me last time when I opened Add/Remove programs and Synaptic program but I never noticed though both were running. So I am just wondering may be you have something similar programming running in background and you never aware of that.

Try **ps aux | more** and see if there is any..

---

### Post by Zzl1xndd on 2009-05-21
uupreti, is correct you more then likely have synaptic or ***/remove open. If they are you will not be able to install the .deb

---

### Post by cowboy7305 on 2009-05-21
ok when i open thhe synaptic i get this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
when i run this in terrminal i get i need to be a super user 
dpkg --configure -a
i have no idea what is wrong

---

### Post by Toshubu on 2009-05-21
> **cowboy7305 said:**
> ok when i open thhe synaptic i get this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
when i run this in terrminal i get i need to be a super user 
dpkg --configure -a
i have no idea what is wrong

So type:  sudo dpkg --configure -a    
...(it will ask for the password; surely you've used sudo before??)....

---

### Post by cowboy7305 on 2009-05-21
not very much iam 75 and dont know that much about this
and i did use that and i get cannot be found

---

### Post by Toshubu on 2009-05-21
> **cowboy7305 said:**
> not very much iam 75 and dont know that much about this
and i did use that and i get cannot be found

Well, cowboy...You got just a couple of years on me...And I'm kinda new to Ubuntu...But, if it were me...I think I'd reboot.(hopefully that should kill whatever package mgmt tool must be running already)...then move whatever you have from frostwire to the trash...then try installing Limewire (basic)...with Synaptic...it's available there, I believe...  But, again, that's what I'd do...Maybe somebody out there with more dpkg experience might have a better idea..

---

