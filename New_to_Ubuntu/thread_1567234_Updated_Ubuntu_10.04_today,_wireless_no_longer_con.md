---
title: "Updated Ubuntu 10.04 today, wireless no longer connects"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Brinstar on 2010-09-03
'cat /var/lib/NetworkManager/NetworkManager.state'

shows that NetworkManager is set to True.

what could have caused this?

---

### Post by Tracy177 on 2010-09-03
> **Brinstar said:**
> 'cat /var/lib/NetworkManager/NetworkManager.state'

shows that NetworkManager is set to True.

what could have caused this?


very very very many things :)

check up dmseg 

and lspci lsub 

u could lose firmware 

etc 

i had issues with network manager i use wicd and it work without problem

---

### Post by Chris1274 on 2010-09-03
What version did you update from? And what's your hardware?

---

### Post by Brinstar on 2010-09-03
> **Chris1274 said:**
> What version did you update from? And what's your hardware?

thanks for the replies, its been a while since i had problems with ubuntu :confused:

i updated from the same version, 10.04, just did the usual update from the update manager GUI and my hardware is a Sony Vaio NR31J with an Intel 3945bg.

the wireless was definitely working before i updated.

---

### Post by Brinstar on 2010-09-03
just checked dmesg, something stands out immediately

```

[   33.510759] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   33.577028] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   33.634562] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   33.699397] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   33.763808] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   33.829039] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   33.901927] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   33.957716] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.032608] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.099225] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.158118] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.217038] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.285031] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.360037] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.413498] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.491145] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.540048] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.604232] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.668817] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.691157] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.713862] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.736455] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.759195] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.781867] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.804515] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   34.827252] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF

```

---

### Post by Chris1274 on 2010-09-03
If you Google that message you'll find a bunch of other people having the same issue. Looks like there was a bug report filed too.

Someone suggested adding
```
noapic
```
to the kernel command line in /etc/default/grub, although I can't vouch for this fix.

---

### Post by Brinstar on 2010-09-03
actually i restarted the laptop and the problem has now gone (for the time being ;))

ubuntu being temperamental as always :)

---

### Post by silverglade00 on 2010-09-03
> **Brinstar said:**
> actually i restarted the laptop and the problem has now gone (for the time being ;))

ubuntu being temperamental as always :)

I have been seeing a lot of posts lately where the solution has been to reboot the computer. Maybe Canonical is trying to make the Ubuntu experience more familiar for those who are just coming from Windows. ;)

---

### Post by Brinstar on 2010-09-04
> **silverglade00 said:**
> I have been seeing a lot of posts lately where the solution has been to reboot the computer. Maybe Canonical is trying to make the Ubuntu experience more familiar for those who are just coming from Windows. ;)

true, but i have yet to experience the wonderful viruses i often seemed to get on windows. still, there's always hope.

---

### Post by juil on 2010-09-04
I don't know if you've tried this to troubleshoot:
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

---

### Post by Brinstar on 2010-09-04
> **juil said:**
> I don't know if you've tried this to troubleshoot:
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

thanks, will keep that in mind.

---

