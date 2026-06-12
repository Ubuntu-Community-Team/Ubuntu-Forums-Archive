---
title: "trying to blacklist b43 &amp; ssb for ndiswrapper"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Tholley on 2009-12-27
I'm following instructions for installing ndiswrapper, since I am trying to get a linksys wireless adapter to work, and after running "sudo apt-get install ndisgtk",
it says to make sure and blacklist b43 & ssb.

I went to /etc/modprobe.d/blacklist.conf: and added the two blacklists, but when I try to save, it says I do not have permision to save. 

So I am thinking I should be logged in as root? or is there a simper way to do it?

Thanks for any help!

---

### Post by Tholley on 2009-12-27
oh yeah, I am running 9.04 on this machine.

I have access to root using terminal, but don't know how to get to the modprobe blacklist from there.

---

### Post by firsttimeubunter on 2009-12-27
> **Tholley said:**
> I'm following instructions for installing ndiswrapper, since I am trying to get a linksys wireless adapter to work, and after running "sudo apt-get install ndisgtk",
it says to make sure and blacklist b43 & ssb.

I went to /etc/modprobe.d/blacklist.conf: and added the two blacklists, but when I try to save, it says I do not have permision to save. 

So I am thinking I should be logged in as root? or is there a simper way to do it?

Thanks for any help!

Do the same using with SUDO... i.e. Open Terminal and type

sudo gedit /etc/modprobe.d/blacklist.conf 

this will open the blacklist.conf file in gedit, then add your blacklists then save it.

---

### Post by Tholley on 2009-12-27
Thanks! Looks like that worked!

now on the the problem of installing the drivers...

new thread.

---

