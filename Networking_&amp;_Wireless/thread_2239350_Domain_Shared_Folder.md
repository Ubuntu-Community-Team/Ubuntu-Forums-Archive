---
title: "Domain Shared Folder"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by mahmoud_moosa2 on 2014-08-13
Hello everybody,

i am working in computer department and there is windows domain and active directory.

i am using ubuntu 12.04 32-bit and  windows 7 professionl 32-bit.
both are joined to the domain successfully, my plan is to created a folder in ubuntu and want to share it with windows users.
i used samba GUI and comfigured the required fileds.

after all here is my problem comes up,

as it's shwoing in the screenshot, it won't create the sharing i don't why?

any idea please?

thank you and i apprecieate any reply and help.

respectfully,

ubuntu

---

### Post by texpat on 2014-08-13
As it says in the error message, it seems you don't have permission to create a share in the directory in question. Try creating a folder in your home directory and share that.

---

### Post by mahmoud_moosa2 on 2014-08-13
Hello and welcome,

i will give it a try and let you know.


respectfully

ubuntu

---

### Post by mahmoud_moosa2 on 2014-08-13
> **texpat said:**
> As it says in the error message, it seems you don't have permission to create a share in the directory in question. Try creating a folder in your home directory and share that.

Hello,

i tried in my home directory and the same permission message.

question please, how do i add my domain account into ubuntu sudoers.

what i did, while i joined o the domain, i edit the /ets/sudoers and still no effect.

---

