---
title: "Problem with Xampp vbox and Gufw"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by MaxVK on 2010-10-23
Hi.

I have a little problem with Xampp vbox and Gufw (ufw).

I have Xampp installed and working fine for my web development needs. For testing I have Windows XP in a virtualbox machine, along with all of the major browsers. It is set to connect to Xampp with a Host-only adapter setting on 'vboxnet0' so that the only thing Windows can connect to it the Xampp localhost.

All works fine and I can test my development in the Windows virtual machine, while windows is unable to connect to the net (just to keep things clean and save running secondary protection for windows).

However, if I have ufw enabled (I'm using Gufw) the XP virtual machine cannot connect to localhost to test anything.

Iv tried all manner of things in Gufw to get it to connect but to no avail.

Can anyone suggest anything please?

[EDIT] By the way, the XP VM can connect just fine if I turn off ufw, so I know its the firewall that is blocking the connection and I need to know how to allow the VM.

Regards

Max

---

