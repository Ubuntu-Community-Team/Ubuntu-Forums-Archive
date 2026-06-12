---
title: "HOW DO I: remote reboot windows via samba"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Nickjpost on 2011-05-07
How can I reboot a windows pc via samba from the terminal? I'm haveing trouble finding info on this. I've found how to shutdown using the command: 
net rpc SHUTDOWN -I 10.0.0.x -U username

so could I just substitute REBOOT for SHUTDOWN? 

Thanks in advance

---

### Post by lmarmisa on 2011-05-07
Try to add the option -r to the command shutdown:

```

net rpc shutdown -r -I 10.0.0.x -U username

```

Best regards,

Luis

---

### Post by Nickjpost on 2011-05-08
> **lmarmisa said:**
> Try to add the option -r to the command shutdown:

```

net rpc shutdown -r -I 10.0.0.x -U username

```

Best regards,

Luis

Luis, thank you for your reply!

I used this command but it only shuts down the remote PC; it does not automatically boot

---

### Post by lmarmisa on 2011-05-08
The reboot command runs just fine here. I am using Ubuntu 10.10 and the remote machine runs Windows XP Pro. 

The first capture wich I attach shows the details of the command **man net** related to **shutdown -r**.

---

### Post by Nickjpost on 2011-06-12
I'm sorry I never replied, the command you gave did, in fact, reboot.

---

