---
title: "How to join a windows domain...."
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by andyk365 on 2008-06-17
Probably been asked a hundred times before, but I'm new to linux so here goes....

How do I join my new Ubuntu Hardy installation to a windows Active Directory / Domain? Tried installing samba, then winbind but stops here - something to do with dependencies....

Anyone got a step by step guide?

Thanks in advance...

---

### Post by cbobb@alinean.com on 2008-06-17
Check out the Likewise open that is available from the Universe repository.  I am in the process of checking it out to see if it works.

---

### Post by .nedberg on 2008-06-17
Have a look [here]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/").

And please let me know how it works, I am thinking of doing this myself :)

---

### Post by lisati on 2008-06-17
Have you seen[ http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605") ?

---

### Post by andyk365 on 2008-06-17
> **.nedberg said:**
> Have a look [here]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/").

And please let me know how it works, I am thinking of doing this myself :)


Looks good! Will try it in the morning when I get to the office...let you know how it pans out :)

---

### Post by andyk365 on 2008-06-18
Works right up until this command "# sudo domainjoin-cli join fqdn.of.my.domain Administrator" - then I get this error:

Error: Unable to resolve DC name [code 0x00080026]

Resolving '**mydomain**.local' failed. Check that the domain name is
correctly entered. Also check that your DNS server is reachable, and that your
system is configured to use DNS in nsswitch.

Anyone got any ideas?....

---

### Post by .nedberg on 2008-06-18
I got the same error when I tried with my fqdn.

However, using just the machine name got me further. I was asked to enter tha password and it tried to join, but could not create the machine account.

It might be some LDAP settings on the server...

---

### Post by andyk365 on 2008-06-18
> **.nedberg said:**
> I got the same error when I tried with my fqdn.

However, using just the machine name got me further. I was asked to enter tha password and it tried to join, but could not create the machine account.

It might be some LDAP settings on the server...
Yep - same here. Getting closer me-thinks.... :-)

---

### Post by andyk365 on 2008-06-20
Still no joy :-(

Anyone had any luck?

---

### Post by terencelhl on 2008-06-21
> **andyk365 said:**
> Still no joy :-(

Anyone had any luck?

Have you included line below in /etc/resolv.conf?

***************START of /etc/resolv.conf**************
search fqdn.of.my.domain
nameserver xxx.xxx.xxx.xxx

***************END of /etc/resolv.conf**************

Reboot and rejoin by using likewise command again. You should see the domain joining without failure this time.

Then reboot again and this time logon using [DOMAIN]\[user id] as username.

Hope these help.

Regards,

Terence Loo

---

### Post by cariboo on 2008-06-21
Has anybody had a look at this page?

[http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain](http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain)

It deals with Ubuntu 5.10 but I can't see how this type of thing has changed since then.

Jim

---

### Post by sol_101 on 2009-07-08
> **andyk365 said:**
> Works right up until this command "# sudo domainjoin-cli join fqdn.of.my.domain Administrator" - then I get this error:

Error: Unable to resolve DC name [code 0x00080026]

Resolving '**mydomain**.local' failed. Check that the domain name is
correctly entered. Also check that your DNS server is reachable, and that your
system is configured to use DNS in nsswitch.

Anyone got any ideas?....

OHH OHH I FIXED THIS!!! Noob FIXED IT. I am running Jaunty. I went to the synaptic Package Manager and install the pam and nss profile switcher. Then in once that is installed I had to edit the /etc/nsswitch.conf look for line host: then add dns on that line. REOBOOT! Once I did that it worked fine. :guitar:

---

