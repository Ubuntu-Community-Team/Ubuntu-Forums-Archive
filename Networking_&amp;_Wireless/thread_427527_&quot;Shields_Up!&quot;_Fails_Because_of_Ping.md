---
title: "&quot;Shields Up!&quot; Fails Because of Ping"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Dark Elitist on 2007-04-29
Hello,

I've setup a Ubuntu box for a friend and it passes the Shields Up! test in every way except it responds to pings.

How do you fix this in Ubuntu?  I saw no options in Firestarter.

Thanks!

---

### Post by Thomi on 2007-04-29
Do this:


echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all


This will stop the machine from replying to all ICMP packets, not just pings!

This change will drop once the machine is rebooted however. To apply it permenantly, either make yourself a nice boot script, OR (better solution), append this line in /etc/sysctl.conf:


net.ipv4.icmp_echo_ignore_all=1



Hope this helps!

---

### Post by Dark Elitist on 2007-04-29
> **Thomi said:**
> Do this:

echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all




Tried that part for testing and even with Sudo I get a permission denied error.  Any ideas?  Thanks for the reply!

---

### Post by kerry_s on 2007-04-29
Have you checked your router? By default most are set to answer pings.

---

### Post by tommcd on 2007-04-29
> **Dark Elitist said:**
> Hello,

I've setup a Ubuntu box for a friend and it passes the Shields Up! test in every way except it responds to pings.

How do you fix this in Ubuntu?  I saw no options in Firestarter.

Thanks!

There is an option to disable ICMP in firestarter. I'm not on ubuntu right now, but in firestarter I think it is under edit>preferences. Look for ICMP filtering and enable it.

---

### Post by Dark Elitist on 2007-04-29
> **kerry_s said:**
> Have you checked your router? By default most are set to answer pings.

He has no router, which is why I'm working so hard to secure him.

---

### Post by Dark Elitist on 2007-04-29
> **tommcd said:**
> There is an option to disable ICMP in firestarter. I'm not on ubuntu right now, but in firestarter I think it is under edit>preferences. Look for ICMP filtering and enable it.

That did it!  I don't know why I didn't notice that.

Any other security tips?

Thanks everyone!

---

### Post by Thomi on 2007-04-29
> **Dark Elitist said:**
> Tried that part for testing and even with Sudo I get a permission denied error.  Any ideas?  Thanks for the reply!

That's because sudo doesn't work with redirection..

You need to actually *be* root in order to redirect into system files (unless you use the tee command, or similar).

---

### Post by tommcd on 2007-04-30
> **Dark Elitist said:**
> That did it!  I don't know why I didn't notice that.

Any other security tips?

Thanks everyone!

Here is some stuff to keep you busy:
[https://help.ubuntu.com/community/InstallingSecurityTools?highlight=%28security%29](https://help.ubuntu.com/community/InstallingSecurityTools?highlight=%28security%29)

I have used chkrootkit. It can have false positives, and it has not been updated since October '06, so I'm not sure how current it is. 
[http://www.chkrootkit.org/](http://www.chkrootkit.org/) 

Here is a good article on netstat for monitoring internet connections:
[http://linuxplanet.com/linuxplanet/tutorials/5633/1/](http://linuxplanet.com/linuxplanet/tutorials/5633/1/)

EDIT: As long as you have no open ports, use strong passwords, install software only from trusted sources, and get all the security updates you are pretty safe. You can also consider the "noscript" extension (addon) for firefox.

---

### Post by TheMono on 2007-04-30
I'm not sure if it would work in that exact case, but it can often work when sudo fails to do

sudo -s

enter your password, and it makes you temporarily root. To exit this, type

exit

and you are back to being you again.

---

