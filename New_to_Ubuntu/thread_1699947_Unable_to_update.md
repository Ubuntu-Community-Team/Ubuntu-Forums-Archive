---
title: "Unable to update"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by llmunro on 2011-03-04
Hi all!

I keeping getting nagged by the update manager.  There are seven updates available and they look to me like kernel updates.

So, the questions are:

Do I really want or need to update the kernel?

and 

When I've tried to install these updates, I get a message that they cannot be installed because the action would require installation of sources that haven't been authenticated.  If I would want to install the updates, how would I make the sources authenticated?

Any thoughts appreciated, as always.

Best,
Lisa

---

### Post by turtle153 on 2011-03-04
You should install kernel updates as they contain security and big fixed, however, you shouldn't get asked about authentication. Is this with Update Manager? If so, what sub-heading (repository) does the kernel update come under?

---

### Post by Sef on 2011-03-04
> When I've tried to install these updates, I get a message that they cannot be installed because the action would require installation of sources that haven't been authenticated. If I would want to install the updates, how would I make the sources authenticated?


Change the source. Application > Ubuntu Software Center > Edit > Software Sources > Ubuntu Software (default tab) > Download from .... > Other > click on 'Select Best Server'

---

### Post by maqtanim on 2011-03-04
> **Sef said:**
> Change the source. Application > Ubuntu Software Center > Edit > Software Sources > Ubuntu Software (default tab) > Download from .... > Other > click on 'Select Best Server'
Or 

Application > Ubuntu Software Center > Edit > Software Sources  > Ubuntu Software (default tab) > Download from .... > Main Server

---

### Post by llmunro on 2011-03-05
Sorry for the delayed response, but I just tried to update again on my laptop, changing the location of the download server to 'Main' and then back to 'United States." 

Still no luck.  The list of updates is growing.  I've attached a screenshot if its any help at all.

Anything else I should try?

Thanks.
Lisa

---

### Post by jbiggs12 on 2011-03-05
You could try going into a terminal and typing
```
sudo apt-get update && sudo apt-get upgrade
```Usually that gives you the option to install unauthenticated packages, although only do this if there is no other real alternative. Kernel updates are important for your computer's stability and security, and your other updates probably fix several bugs as well. So if you keep getting that error try installing from the terminal, but as I said previously only do this as a last resort.

---

### Post by llmunro on 2011-03-05
Hi,

The command: sudo apt-get update && sudo apt-get upgrade  seems to have updated most of the stuff, although I'm getting the following error and there are still six updates in the update manager that can't seem to be updated:

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic

Thoughts?

Thanks for the help.

Best,
Lisa

---

### Post by llmunro on 2011-03-06
Hi,

Marking this as solved.  

sudo apt-get dist-upgrade has worked an I have no more updates to install! 

Thanks to all for the help and ideas!

Best,
Lisa

---

