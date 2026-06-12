---
title: "Network share mount"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by mbstrlbstr on 2009-12-08
My goal is to mount a shared folder as a drive, so ultimately I can access it in a virtual machine and us MS Access on it.

I followed the steps found here:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

and got to the step where I input 
```
sudo mount -a
```

and the terminal just hangs, until I get the 
```
mount error(110): Connection timed out
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Any suggestions, or another way to accomplish my final goal?

---

### Post by bodhi.zazen on 2009-12-08
The list of potential problems is long and you have not provided any meaning details other then to say it is not working.

What type of networking are you using ? NAT, Host only, Bridged ?

Can you ping between the two machines ?

Any firewalls ?

How did you configure your share exactly ?

What did you use in your fstab ?

---

### Post by mbstrlbstr on 2009-12-08
Yeah I had it set up as NAT. Just delved a little deeper into the Vbox settings and realized it should be bridged mode. Works now! Thanks for the reply.

---

