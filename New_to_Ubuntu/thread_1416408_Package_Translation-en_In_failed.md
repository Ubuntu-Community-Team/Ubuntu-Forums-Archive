---
title: "Package: Translation-en_In failed"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by chaitu_021 on 2010-02-26
When i try to reload the Synaptic Package manager

I am getting failed messages for the particular packages only
 
Translation-en_IN

please help me

---

### Post by mikeyphi on 2010-02-26
> **chaitu_021 said:**
> When i try to reload the Synaptic Package manager

I am getting failed messages for the particular packages only
 
Translation-en_IN

please help me

Welcome!!

Please confirm if you get the failed message when you are trying to download a package OR when you try to update the software list?

Also - if possible, please expand on what the on-screen message says.

Meanwhile, do this, it might help, can't hurt!

open a terminal and enter:

sudo dpkg --configure -a

(enter your user password on next line when prompted)

---

### Post by chaitu_021 on 2010-03-21
i am getting failed message when i am updating the software list.
I am using Ubuntu 9.10 and the message look like

Failed   0 B    Translation-en_IN   [http://security.ubuntu](http://security.ubuntu) ...

---

