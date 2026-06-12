---
title: "Untrusted Packages!"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by sallam on 2011-03-22
Greetings

Recently, when I try to install software from the ubuntu software center, I often get an "Untrusted Package" error message, saying:
> The action would require the installation of packages from not authenticated sources.
And it refuses to install them, even though they are  listed within the software center itself!

Any idea why is that happening recently?
(I was trying to install SuperTux game, AcetoneIso, Secret Maryo Chronicles, among others ..)

---

### Post by Razorback on 2011-03-22
This explains it and offers help to install:

[http://jaypeeonline.net/tips-tricks/install-untrusted-software-ubuntu/](http://jaypeeonline.net/tips-tricks/install-untrusted-software-ubuntu/)

---

### Post by arochester on 2011-03-22
Try updating. Connect to the Internet. Open  a Terminal. Issue the command: sudo apt-get update

Try again

---

### Post by vivek.pandey on 2011-03-22
you need to update your system..execute each command one by one
sudo apt-get update
sudo apt-get upgrade
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
apt-key add ~/.gnupg/pubring.gpg

---

### Post by sallam on 2011-03-22
vivek.pandey, thanks.
But during the first command, it gave a few gpg errors about some invalid signatures. Is this normal, or did something went wrong?
And what are the third and forth command lines about, what is this key for?

---

### Post by sallam on 2011-03-22
does those commands update my ubuntu from 10.10 to 11.04 pre-release version or what?

---

### Post by Razorback on 2011-03-22
No it won't.

sudo apt-get dist-upgrade 

will migrate you to the next version.

EDIT:  I stand corrected. :)

---

### Post by arochester on 2011-03-22
> sudo apt-get dist-upgrade 

will migrate you to the next version.

Not necessarily. See e.g. [http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/](http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/)

---

### Post by sallam on 2011-03-22
I did update and upgrade, but still getting the untrusted packages error..
btw, I'm not trying to install some downloaded file. I'm trying ti install software that the ubuntu software manager itself is offering from its search results...

this is weird..!

---

### Post by 5149.5 on 2011-03-22
> **sallam said:**
> I did update and upgrade, but still getting the untrusted packages error..
btw, I'm not trying to install some downloaded file. I'm trying ti install software that the ubuntu software manager itself is offering from its search results...

this is weird..!

I'm not sure if it has anything to do with your problem but  the ubuntu keyserver has been down all day.

---

### Post by sallam on 2011-03-23
Finally I found out a very simple solution!
I tried installing them from Synaptic package manager, and it worked!
It did warn me too that I'm about to install un-authenticated software, but it did not prevent me from installing them.

Thanks everyone for trying to help.

---

