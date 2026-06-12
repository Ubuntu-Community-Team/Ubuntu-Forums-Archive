---
title: "Can't administer printers"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by japhyr on 2010-04-07
Hello,

I am trying to add a networked printer to a computer running 8.04.4.  When I check Server Settings >> Show printers shared by other systems, I am prompted for my password.  My password never gets accepted, the password prompt keeps reappearing.  I get the same response if I use a browser and go through CUPS.  Can someone help with this?  Thank you.

---

### Post by byStanderone on 2010-04-07
...would just like to know if your 8.04 is at its latest update?

---

### Post by japhyr on 2010-04-08
The computer is fully up to date, except one package that fails to be fetched (tzdata, a time zone data update).

I think I may know the source of the problem.  The system was installed by one person.  I then added a new admin user, and deleted the original admin account.  Is it possible the CUPS server is asking for the original username/ account (which I no longer have)?  If so, is there a way to reset the CUPS username/ password?

---

