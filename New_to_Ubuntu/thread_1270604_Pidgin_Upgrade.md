---
title: "Pidgin Upgrade"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by ovid9 on 2009-09-19
Ok, so I have pidgin, and the issues with yahoo and such have been posted on here a lot.  I had mine fixed.  Then I reinstalled my OS (Hardy) which messed up my settings.

I currently have Pidgin 2.4.1.  I tried following the instructions on the Pidgin site, but to no avail.  Here are the instructions i'm sure you've seen 

> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
  

Now, I wasn't sure if I cut and paste that whole block at once, so I did it both ways.  Neither worked.   Here is what I seem to think the issue is...what do I do now?

> gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

I feel like an idiot,but 99% of the stuff I use is all handled through the add/remove stuff.  I have been using Ubuntu for probably about a year, but its almost all the GUI aspect of it.  

Thanks!

---

### Post by jmszr on 2009-09-19
ovid9,

I would suggest installing it from here: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

---

### Post by ovid9 on 2009-09-19
Thank you!

---

