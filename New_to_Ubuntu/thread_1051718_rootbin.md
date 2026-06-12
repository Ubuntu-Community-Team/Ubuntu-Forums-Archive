---
title: "/root/bin"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Avalanche21 on 2009-01-27
Hi, noob here...If I have a README that is telling me to copy a script to /root/bin, how do I do that?

Av

---

### Post by iaculallad on 2009-01-27
> **Avalanche21 said:**
> Hi, noob here...If I have a README that is telling me to copy a script to /root/bin, how do I do that?

Av

The path would probably be: /usr/bin and not /root/bin. To copy a script on your /usr/bin directory, use the command below:

```
sudo cp /location/of/script/scriptname.sh /usr/bin
```

and input your password.

And just make sure that the script has it's executable bit turned on.

```
sudo chmod u+x /usr/bin/scriptname.sh
```

---

