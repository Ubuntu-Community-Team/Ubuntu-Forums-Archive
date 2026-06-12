---
title: "Newest kernel update broke my system"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by Papa-san on 2010-08-24
I ran update manager this morning. There was a new kernel included. I needed to re-boot to finish the installation, and it failed to fully boot. I booted to a completely blind grey screen.

I am using 8.04 on a Dell Latitude D610.

When I noticed the fail, I held my power button down to shut it off. (Nothing else worked) I am currently using the previous kernel, but need to know what to do to remove the latest one, or fix whatever went wrong.

---

### Post by linux-hack on 2010-08-24
try this : 
```

dpkg -l | grep linux-headers-*
sudo apt-get remove --purge 2.6.2x-xx-*

```

where X is the version you installed.

[http://digitalpbk.blogspot.com/2008/11/ubuntu-remove-old-kernel-grub-list-long.html](http://digitalpbk.blogspot.com/2008/11/ubuntu-remove-old-kernel-grub-list-long.html)


Hope this helps

---

### Post by Calash on 2010-08-24
Do you have any 3rd party drivers, like Nvidia, installed?  If so you may need to remove them or boot into Recovery and reinstall them.

---

### Post by Papa-san on 2010-08-24
How would I find out if I have any third party drivers?
I know that I had to mess with some at initial setup, though I don't remember exactly what they were.

Also, for learning purposes, how would this particular new kernel flub it up when several previous ones didn't? This is like the fourth or fifth time since my initial installation...

---

