---
title: "Can't uninstall Flash player in synaptic"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Fika on 2010-01-05
I'm completely new to ubuntu and just started using 32 bit karmic koala 9.10

Flash player does not work on any sites. I've found some threads that say uninstall then reinstall but when I go to synaptic and mark it for complete removal I get this error:

E: flashplugin-nonfree: subprocess installed pre-removal script returned error exit status 2

I've looked all over for a solution. Any help would be greatly appreciated to get this working

Thanks

---

### Post by philinux on 2010-01-05
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/365392](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/365392)

See post #3 and others.

---

### Post by Fika on 2010-01-05
Thanks for the suggestion. I am not sure how to do this. How do I 'execute' the line?


[Diogo Custodio]("https://launchpad.net/%7Epingflood")             wrote             on 2009-05-01:                                                             [ #3]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/365392/comments/3")                                                        Here's a workaround:
 Execute this to remove all zero byte files related to Flash in /var/lib/dpkg/alternatives/:
 find /var/lib/dpkg/alternatives/*flash* -type f -size 0  | xargs sudo rm
 Then try again install/remove flashplugin.

---

### Post by Methuselah on 2010-01-05
> **Fika said:**
> Thanks for the suggestion. I am not sure how to do this. How do I 'execute' the line?


[Diogo Custodio]("https://launchpad.net/%7Epingflood")             wrote             on 2009-05-01:                                                             [ #3]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/365392/comments/3")                                                        Here's a workaround:
 Execute this to remove all zero byte files related to Flash in /var/lib/dpkg/alternatives/:
 find /var/lib/dpkg/alternatives/*flash* -type f -size 0  | xargs sudo rm
 Then try again install/remove flashplugin.

Open a terminal (Accessories->Terminal) and paste this part in it:
```

find /var/lib/dpkg/alternatives/*flash* -type f -size 0 | xargs sudo rm

```
Then hit the enter key.

By the way, the command finds all zero length files under /var/lib/dpkg/alternatives/ named <something>flash<something> (where <something> can be nothing) and deletes them.

---

### Post by howefield on 2010-01-05
> **Fika said:**
> How do I 'execute' the line?

Open a terminal (Applications > Accessories > Terminal) and copy/paste the command into it and press enter.

You may need to enter your password, you won't see it being typed, but it will be entered.

---

### Post by Fika on 2010-01-05
I typed in the command and here is what I got back:

rm: missing operand
Try `rm --help' for more information.

---

### Post by philinux on 2010-01-05
> **Fika said:**
> I typed in the command and here is what I got back:

rm: missing operand
Try `rm --help' for more information.
I would try this first.
```
find /var/lib/dpkg/alternatives/*flash* -type f -size 0 
```
See if it finds anything.


I think there may be an error in the bug report post. Should be.

```
find /var/lib/dpkg/alternatives/*flash* -type f -size 0 | xargs sudo rm -f
```

From man xargs.
> EXAMPLES
       find /tmp -name core -type f -print | xargs /bin/rm -f

       Find  files named core in or below the directory /tmp and delete them.  Note that this will work incorrectly if there are
       any filenames containing newlines or spaces.

       find /tmp -name core -type f -print0 | xargs -0 /bin/rm -f

       Find files named core in or below the directory /tmp and delete them, processing filenames in such a way that file or di&#8208;
       rectory names containing spaces or newlines are correctly handled.


---

### Post by Fika on 2010-01-05
Ok, I got flashplugin-nonfree removed completely now after that last step! Thank you. 

Now, where do I need to download flash from so it will work with karmic 9.10 32 bit? From the ubuntu software center?

---

### Post by philinux on 2010-01-05
Click the restricted formats link in my sig below.

---

### Post by Fika on 2010-01-05
Tried to install restricted formats. Here is what I got:

E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1

---

### Post by Fika on 2010-01-05
Finally got flash working properly. 

While trying to install the restricted formats package I got error messages but synaptic showed the package as installed afterwards, but still no flash functionality...

Went to ubuntu software center and flash was not showing up as installed. I installed it via the software center, restarted *ubuntu* (not just firefox) and it works now. 

Thanks for the help everyone.

---

