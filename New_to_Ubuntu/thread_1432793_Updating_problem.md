---
title: "Updating problem"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by daniell59 on 2010-03-18
I just installed ubuntu 9.10 on a laptop.

While updating, I got the following message.

Some of the packages could not be retrieved from the Servers.
Any idea what this means?

In a somewhat off topic question, I would appreciate the feedback.
This laptop is having a problem charging. It is either the power jack or the plug. Any suggestions on how I can determine which? If it is the power jack it does not pay to have it fixed.

Thanks

---

### Post by MelDJ on 2010-03-18
try going to software sources and change your software server

---

### Post by daniell59 on 2010-03-18
> **MelDJ said:**
> try going to software sources and change your software server

Thanks

I would appreciate it if you could elaborate on what you said.

---

### Post by Paddy Landau on 2010-03-18
System > Administration > Software Sources

Download from: Other

Either choose a server near you, or "Select Best Server".

---

### Post by MelDJ on 2010-03-18
sorry :p
go to system-administration-software sources
click on the current server you are using (near the download from:)
then press other.
then either manually pick a server or let it pick the best server.
after changing the server, let it reload or manually do sudo apt-get update

---

