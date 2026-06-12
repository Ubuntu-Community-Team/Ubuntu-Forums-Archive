---
title: "host name problem / question"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by canam101 on 2009-01-17
My user name on my ubuntu os is 'joe', and if I go to administration/network/general, I see next to the 
host-name 'joe-desktop'.

joe-desktop must have been some default I took during installation.

Usually I have no problem with sending email, but I recently noticed that certain sites were bouncing my emails because my 'helo' was not a 'fully-qualified domain name'. Maybe I should add that I am sending directly to the smtp servers on the other sites, using exim4.

After rooting around, I ended up changing host-name to a yi.org name that points to my static ip, <somename>.yi.org. When I did that, the bouncing stopped and the emails went through.

But the computer seems to be a bit sluggish when I use the yi.org name.

I was wondering if using the yi.org name would account for that, and if there is some other way of convincing the sites to accept my email.

---

### Post by cmnorton on 2009-01-17
It sounds like you need to add a SMARTHOST entry in /etc/mail/sendmail.mc, and then rebuild with m4. You need to go google that, but usually you:

1) Become root in /etc/mail

2) Enter these commands:

cp sendmail.mc sendmail.mc.install
cp sendmail.cf sendmail.cf.install
# so you can go back if something goes wrong

3) Edit sendmail.mc

4) Compile sendmail.mc
 
m4 sendmail.mc > sendmail.cf

5) /etc/init.d/sendmail restart (I think the daemon is sendmail. To be sure, ps -ef grep mail to see what's running.)

---

### Post by albinootje on 2009-01-17
> **canam101 said:**
>  Maybe I should add that I am sending directly to the smtp servers on the other sites, using exim4.


I don't like using Exim4, and I don't know so much about it, but with postfix there's /etc/mailname in use.
I suggest you find out how to change hostname instances in the Exim4 configuration files.

This could help :
```

grep -r -i your_old_hostname /etc/exim4*

```
but better check the Exim4 documentation, or do a "sudo dpkg-reconfigure -phigh" on the relevant exim4 package.

---

### Post by albinootje on 2009-01-17
I've reread your OP. Sorry for reading it too quickly the first time.

Can you please post the output of :
```

cat /etc/hosts
cat /etc/hostname

```

In general a fully qualified hostname is not needed on a desktop computer, and for emails via your smtp software (Exim4) it would be best to set a proper hostname and/or domain name in those settings.

Yes, it's possible that the slowdown is because of that.
Your machine should be called (for example) desktop.yi.org instead of yi.org.

---

