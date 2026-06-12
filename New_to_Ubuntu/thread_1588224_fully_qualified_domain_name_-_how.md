---
title: "fully qualified domain name - how?"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by canam101 on 2010-10-04
I found out that mail to certain addresses is being rejected because when I installed ubuntu I specified the computer name as 'renfrew', and the mail servers said that was not a fqdn (fully-qualified domain name).

After looking around, I have the idea that I could turn it into a fqdn if I went to etc/hosts, and /etc/hostnames and changed 'renfrew' to 'renfrew.google.com'.

So I did that, but my email still gets rejected for not having a fqdn. It looks like the mail servers see the same thing I see when I open up a terminal window: joe@renfrew.

So is there some way I can change what I see in a terminal window to:
[email]joe@renfrew.google.com[/email]?

I'm hoping that if I do that, the mail servers will see a fqdn and accept my mail.

I looked at various system type menus but don't see what will do the trick.

Maybe I should be clear that the 'from' address in the emails is a fqdn. But that is not what is causing the problem with the mail servers. It is something else called a HELO command/address/some other component of sending emails.

Thanks for any help.

---

### Post by bodhi.zazen on 2010-10-04
You have to change /etc/hosts and /etc/hostname at the same time.

Second you can not use someone else's FQDN, ie, you are not google.com, you need to register your own.

---

### Post by drdos2006 on 2010-10-04
Check out [http://www.dyndns.com/](http://www.dyndns.com/) to get a domain name.

regards

---

