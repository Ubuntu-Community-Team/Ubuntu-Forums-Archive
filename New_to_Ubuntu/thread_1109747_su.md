---
title: "su"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by bmachia on 2009-03-29
I have for months used sudo when I needed to install or compile software.  Recently I wanted to switch to SuperUser, and while I have already 'sudo xxx xxx' I can't complete the su command.  When I type su at a command line it just returns the path#, no error and no path$.  I expected it to ask me for a password.

Can anyone please tell me What step am I'm forgetting?

Bill

---

### Post by Linux&amp;Gsus on 2009-03-29
If I got that right you made a password for the user root? But when you type 'su' in a terminal it's not doing it?
If I'm not totally wrong then you should type 'su root' to change to root user. Then the password request for root should come up.

Or did I miss-understand that somehow?

Cheers,
L&G

---

### Post by hyper_ch on 2009-03-29
you don't need su at all... if you want to issue multiple things as root use
```

sudo -i

```

btw, it's against forum CoC to tell how to enable root. You might want to edit your post.

---

### Post by bmachia on 2009-03-29
Thanks for responding L&G and hyper

L&G, it sounds like the MS world, but the only way I could get to su was through a ReBoot.  After the RB, I could su without any problems.  strange...

Problem solved


hyper, point well taken, sorry, edited

Bill

---

### Post by Linux&amp;Gsus on 2009-03-29
> **bmachia said:**
> L&G, it sounds like the MS world, but the only way I could get to su was through a ReBoot.  After the RB, I could su without any problems.  strange...


Hu? sounds scary...
Has MS bought Ubuntu? Did they manage to insert a virus into the Kernel? I shall boycott Linux from now on, I switch to Sun Solaris... Can I have KDE with that?? :KS
haha :P

Glad it worked out.

Cheers,
L&G

---

