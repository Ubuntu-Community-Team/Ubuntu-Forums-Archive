---
title: "Synaptic"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by basilwatson on 2009-05-28
I dont know if this has been posted before , I was downloading Second-life and it was corrupted, 

So I gave up, but know when I try to install via synaptic the programe gives me this error message 

E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

but i cant, as soo as I click ok the programe crashes! 

so I tried 

 dpkg --configure -a
dpkg: status database area is locked by another process
s-desktop s # dpkg --configure -a

how can I sort this mess out 

kind Regards 

Stephen 

BTW  I am using Ubuntu 8.1

---

### Post by Sef on 2009-05-28
>   dpkg --configure -a```


Don't forget to use sudo.  


```sudo dpkg --configure -aPost more if it don't work.

---

### Post by basilwatson on 2009-05-28
> **Sef said:**
> Post more if it don't work.

tried that , says i cant find package , Ive tried apt-get clean ( etc ) 

same error message 

Thanks for your help 

Stephen

rchive for it.
s-desktop s # sudo dpkg --configure -a 
s-desktop s # synaptic
s-desktop s # apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
s-desktop s #

---

### Post by sandyd on 2009-05-28
```

dpkg --remove --force-remove-reinstreq secondlife-install

```

this will happen when you are installing files from a DEB instead of from the repositories.

i believe that apt-get should add a suggestion for that code that i just posted above. took me a long time to find it when one of my debs went bad.

---

### Post by basilwatson on 2009-05-28
> **carlee said:**
> ```

dpkg --remove --force-remove-reinstreq secondlife-install

```

this will happen when you are installing files from a DEB instead of from the repositories.

i believe that apt-get should add a suggestion for that code that i just posted above. took me a long time to find it when one of my debs went bad.

That did the trick ! Thank youu very much !!!

Stephen

---

