---
title: "Problems with scp and... bin?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Zubeneshamali on 2009-01-11
Hi

I'm trying to download a directory from a remote computer but, something seems to be wrong...
 I type the command line

scp -r [email]remotecomp@domain.of.themachi.ne[/email]:~/thedirectory ~/

it asks for de password.. but the next line says :
Bind: Command not found
and the files starts being downloaded... so when the process is finished, and I type ls bu.. there's nothing!

I'm desperate, could you help me?

---

### Post by stevoo on 2009-01-11
the command doest look correct.
 scp [email]stevoo@***************:~/Desktop/reload.html[/email] ~/Desktop/
it works for me

R u sure you are at the correct directory you are looking at  ?
Try scping it to your desktop and see if it goes there

---

### Post by spiderbatdad on 2009-01-11
So, if I ssh into my remote machine, I log into a user account. Like so
```
ssh -X <user_name>@<ip_adress>
```Running ls -l after I am logged in, shows me a single directory "Desktop" I cd into Desktop and see some .png files I want.
I open another terminal on my local machine and run: ```
scp -r <user_name>@<ip_address>:Desktop/*.png ~/Desktop
```

---

### Post by Zubeneshamali on 2009-01-11
Now,the files are in the root directory... it worked thanks ;o)

---

