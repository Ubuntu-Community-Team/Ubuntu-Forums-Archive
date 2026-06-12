---
title: "Fixing my package manager..or installing IE 4 linux without it"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-03-09
I  wrecked my package manager trying to install IE for Linux, no I get this error: E: Type 'and' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
I googled, but didn't really understand the instructions.  If anyone knows how to either:  fix his easiily  OR install  IE 4 Linux without using the synaptic package manager, and easily too,  I would appreciate knowing becasue I need IE to access our college math site and  input my  work before tomorrow or else...lol  thanks in advance!

---

### Post by t0p on 2009-03-09
Your sources list has somehow been altered/corrupted.  So you need to edit the file /etc/apt/sources.list.  Post the contents of that file and we can tell you what needs doing.

EDIT: Incidentally, are you sure you need IE to access the college site?  There's an add-on available for Firefox that changes the browser's user-agent, ie it can make sites think it's IE or Opera.

---

