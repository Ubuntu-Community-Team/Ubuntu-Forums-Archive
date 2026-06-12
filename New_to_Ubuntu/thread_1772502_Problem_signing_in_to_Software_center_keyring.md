---
title: "Problem signing in to Software center keyring"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by JohnBonne on 2011-05-31
Like I said. I am having problems signing onto the Software Center using the keyring I was sent. How do I go about getting another key?

---

### Post by JohnBonne on 2011-05-31
Update on the problem. I have tied to recover my password using the tool in Software Center and I get the error message: can't reset this account!

---

### Post by Miljet on 2011-05-31
I don't know what keyring you are talking about that you were sent. The only password you should need is the one that you use to log on. It is the one that you created during install.

---

### Post by JohnBonne on 2011-06-01
> **Miljet said:**
> I don't know what keyring you are talking about that you were sent. The only password you should need is the one that you use to log on. It is the one that you created during install.

The Download Center in Ubuntu Natty.

Download Center requested a security password sent by Ubuntu forums manager. 

 When I entered the keyring, which is what they call the security password, the Download Center rejected it. 

Thanks

---

### Post by frankbooth on 2011-06-01
I had problems with synaptic rejecting my password on a Lubuntu installation, so this is a long shot...

Try this:

1) open terminal
2) write gksu-properties
3) change 'Authentication mode' to sudo

---

### Post by JohnBonne on 2011-06-01
> **frankbooth said:**
> I had problems with synaptic rejecting my password on a Lubuntu installation, so this is a long shot...

Try this:

1) open terminal
2) write gksu-properties
3) change 'Authentication mode' to sudo

It _was_ a firewall problem. I am using Firewall from the Software Center. I had it set up to reject all incoming and outgoing traffic.  I had to remove the outgoing restriction. 

Thanks, buddy.

---

