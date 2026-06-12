---
title: "Concerned re updating packages with UNAUTHENTICATED warning"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Andavane on 2009-01-11
Over the past week I've noticed that some packages in synaptic I wish to install such as some OpenOffice updates have carried the "UNAUTHENTICATED" warning. As it seemed to be part of the OpenOffice system I carried on anyway.
Now I want to get some of the Ubuntu Obex bluetooth things going and I'm getting the same warning.

Does anybody know what is going on here?
Kind regards

John

PS: Due to a stuttery connection I have bee able to retrieve much from google, but am getting through on this forum. For same reason there are delays in response.

---

### Post by Elfy on 2009-01-11
IF you don't have the signature for a repo that you are using or there isn't one then you will get the warning. As long as you are happy that the repos you have in your sources list are ok then carry on.

---

### Post by eragon100 on 2009-01-11
> **forestpixie said:**
> IF you don't have the signature for a repo that you are using or there isn't one then you will get the warning. As long as you are happy that the repos you have in your sources list are ok then carry on.

In addition, most repos have instructions for importing their key on the page you got them from. If you follow those instuctions, the system should now "thrust" that repo and stop giving the warnings.

---

### Post by ugm6hr on 2009-01-11
You should know which non-standard repository you have installed.

Did you install a newer version of OpenOffice from the PPA repo?

If this doesn't make any sense to you, post the contents of /etc/apt/sources.list

---

