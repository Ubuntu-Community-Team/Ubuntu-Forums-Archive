---
title: "can't update"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by eleaz14 on 2011-05-29
Hello

I just downloaded someting a few days ago. It was a .tar package. Then i tried to untar it so it could get installed. When i did untar it, it said:

 Configuring installation....

And it got stuck. Now i can't install anything in Ubuntu because it forces me to end this installation, but when i tried to continue with it, the command line gets stuck again. And i can't update Ubuntu either becuase it forces me always to continue with my previous installation wich i didn't end. I ven tried erasing the .tar that got me into this, but even after i erased it, the problem is still there

Thanks

---

### Post by wildmanne39 on 2011-05-29
> **eleaz14 said:**
> Hello

I just downloaded someting a few days ago. It was a .tar package. Then i tried to untar it so it could get installed. When i did untar it, it said:

 Configuring installation....

And it got stuck. Now i can't install anything in Ubuntu because it forces me to end this installation, but when i tried to continue with it, the command line gets stuck again. And i can't update Ubuntu either becuase it forces me always to continue with my previous installation wich i didn't end. I ven tried erasing the .tar that got me into this, but even after i erased it, the problem is still there

Thanks
Hi, try
```
sudo apt-get --purge remove packagename
```
```
sudo apt-get update
```

---

