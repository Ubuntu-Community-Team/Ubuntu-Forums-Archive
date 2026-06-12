---
title: "I need an Internet access management packed for a Network."
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by grs on 2007-10-13
This may not be entirly relevent to Ubuntu.

I'm looking for an internet access managment program, at the moment the school where I'm working is using a setup called Netfort, its a box with 2 NIC's, all internet traffic passes through it, and its managed by a WEBGUI type interface. The software allows user names and passwords to be setup, without these access to the internet is not possible. There are a number of things about it I don't like, users setup there own accounts, it does keep a record of sites that a user has accessed and times they were logged on but its not well layed out.
The people who provide the package manage some aspects of the system and access from there end which I don't like too much, it slows down the running if I have to be dealing with some via email who is on the other side of the country.

I'm not here too long but I have a feeling there might be a contract between the Department Of Education and Netfort so I may not be able to change anything, but I would like to know of alternatives.

Can anyone suggest an alternative, either software or and hardware options, all price ranges.

---

### Post by bravo911 on 2007-12-05
I'd say IPcop has everything you need and more. With a third NIC and a wireless access point, you could offer SECURE wireless as well. There are many addons available that will even do content filtering based on a score system. User passwords can be implemented as well, and the documentation is quite good. Take a look. I've used it for years.

[http://ipcop.org]("http://ipcop.org")

---

### Post by jonallport on 2007-12-05
I agree with bravo911, IPcop is good, as is Smoothwall (v3 has traffic shaping - cool!).

If you're feeling more adventurous you could start with a vanilla Ubuntu server and see what you can do.  Chillispot installs smoothly from the repos (best to do a LAMP install first in my opinion or you'll get apache-perl with no SSL) and that will take care of a lot of the access control and activity logging.  Also try Dansguardian, the ubiquitous Squid, the list goes on...

---

