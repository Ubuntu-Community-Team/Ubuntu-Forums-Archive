---
title: "/etc/shadow question"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by CosmicFlux on 2009-07-25
Hi,

OK, whilst sifting through Linux in the Terminal I brought up **/etc/shadow** file.

The password field shows an encrypted string beginning with an $ character. 

My first question is this:

**Is it normal for this encrypted string to be displayed in plain text? I noticed the other accounts were protected with a * character.**

My second question is: 

**What type of encryption is used? I know it isn't DES, and I'm pretty sure it isn't MD5 either.**

**NOTE:**

*These are legitimate queries from a user who is interested in exploring Linux in depth through the command-line in order to gain a deeper understanding of the system as a whole. NO 'HACKING TIPS' wanted.*


Cosmic

---

### Post by ptn107 on 2009-07-25
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)

---

### Post by aysiu on 2009-07-25
> Is it normal for this encrypted string to be displayed in plain text? I noticed the other accounts were protected with a * character. By definition if it's encrypted it is *not* in plain text. It is visible, but it is not in plain text. If you saw the password as it is and not as a bunch of gibberish, then it would be in plain text.

---

