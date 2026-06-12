---
title: "How do I make an ISO of my ubuntu setup?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by cricketbird on 2010-10-11
I installed Ubuntu Netbook Remix.  I've removed some programs I never use, and added some that I do.   I'd like to make a bootable USB key of MY ubuntu setup, with my apps and settings.

I've been searching and seen lots of info on how to back up your files to a hard drive, and lots on how to download and use an existing ISO file, but nothing on how to make my own ISO from my computer setup.  

Is this something within reach of a newbie?  Is there a tutorial out there? 

Thanks!
CB

Samsung NC10 Netbook, Atom processor, 1 GB ram
Ubuntu 10.04 (although am open to 10.10)
zero command-line experience

---

### Post by celticbhoy on 2010-10-11
try remastersys from the software centre

---

### Post by cricketbird on 2010-10-11
Thanks celticbhoy,

remastersys looks like exactly what I want.  However, when I try to download it, it says "The action would require the installation of packages from not authenticated sources." 

Do you have any ideas how to get around this?

Thanks,
CB

---

### Post by celticbhoy on 2010-10-11
In software centre, click on edit --> software sources.

make sure all four of the top options are checked

---

### Post by celticbhoy on 2010-10-11
Sorry, my mistake. What you need to do is this :-

Go to system --> Admin --> Synaptic

Then setting --> repositories --> other tab

click add & paste this

deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

then reload & search for remastersys click & install.

---

### Post by cricketbird on 2010-10-12
Thanks!  Got it!

---

