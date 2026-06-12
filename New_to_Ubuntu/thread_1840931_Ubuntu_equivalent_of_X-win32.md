---
title: "Ubuntu equivalent of X-win32?"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by banff2010 on 2011-09-08
Is there a package equivalent to [X-win 32]("http://www.starnet.com/products/xwin32/") I used this when it was X-win32.8 on my PC. I could run numerically intensive computations on another machine (server) and my PC act like a GUI terminal for that server? Am I making myself clear?

I did use 
```
ssh -X num.fake.com -l dumbdumb 
``` it just open up a terminal, but when I activated the program on that it did not open up new GUI windows on my ubuntu 10.04 laptop. I must be missing some more commands.

Thanks,

---

### Post by apollothethird on 2011-09-08
> **banff2010 said:**
> Is there a package equivalent to [X-win 32]("http://www.starnet.com/products/xwin32/") I used this when it was X-win32.8 on my PC. I could run numerically intensive computations on another machine (server) and my PC act like a GUI terminal for that server? Am I making myself clear?

I did use 
```
ssh -X num.fake.com -l dumbdumb 
``` it just open up a terminal, but when I activated the program on that it did not open up new GUI windows on my ubuntu 10.04 laptop. I must be missing some more commands.

Thanks,

I'm not familiar with X-win32 but I'm sure it's probably a crude rendition for X which is a Unix/Linux standard.  Since you're in the Ubuntu forum you most likely have the Ubuntu desktop with the standard X.

To connect to another machine and run the X session on your local desktop just run:

To run an X session from a remote machine on your local machine (in this example, Libreoffice) just type:
```

ssh -X username@hostname.com
libreoffice

```

In Ubuntu remote X session isn't disabled by default so you probably won't have to make any changes on the host machine.  Enabling it on the host machine is just as simple.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by banff2010 on 2011-09-08
Thanks James. Silly me, I did not need anything after my ssh command. The problem was with the server installation of R.

---

