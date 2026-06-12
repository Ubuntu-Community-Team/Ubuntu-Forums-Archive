---
title: "passing the NN_XMX startup parameter???"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by jfbooth on 2011-08-12
I am trying to 'configure' a program I just installed.  It is called NEVERNOTE.  The instructions refer to NixNote but the docs are 'poor' and they apply to the newer product name NEVERNOTE.  The instructions say:

> you can try to reduce the amount of memory NixNote (sic) uses by passing the NN_XMX startup parameter.

NN_XMX=<memory>

This specifies the maximum heap size that Java uses. The default is 1024M. If you are concerned, you can probably reduce this after the first synchronization and indexing is complete. I've been able to decrease it to 256M with no noticeable problems.

I do not know how to 'pass' a startup parameter.  There is a NEVERNOTE icon on my desktop.  When I right click on it, and left click properties, I get what is shown in the attachment.  I gather I edit the command line, but not sure exactly what the edit should be.  Guessing:

/usr/share/nevernote.sh NN_XMX=256

but being an 'absolute beginner, I am not quite certain.

Any help is appreciated in advance.

---

### Post by jfbooth on 2011-08-13
While waiting for help, I decided to give it a try.

I changed properties to

/usr/share/nevernote.sh NN_XMX=256

and then

/usr/share/nevernote.sh NN_XMX=<256>

and with each, nothing happens when I click the icon .. so apparently, neither is right.

Any help is appreciated in advance.

---

### Post by jfbooth on 2011-08-18
I am sorry to bump this.  It has been 5 days with no answer.  I read somewhere if that happens, I should bump it but no more than once in 24 hours.

Can anyone help me with this?  Thank you again, in advance.

---

### Post by jfbooth on 2011-08-28
> **jfbooth said:**
> I am sorry to bump this.  It has been 5 days with no answer.  I read somewhere if that happens, I should bump it but no more than once in 24 hours.

Can anyone help me with this?  Thank you again, in advance.

bump

---

### Post by jfbooth on 2011-08-30
bump

---

