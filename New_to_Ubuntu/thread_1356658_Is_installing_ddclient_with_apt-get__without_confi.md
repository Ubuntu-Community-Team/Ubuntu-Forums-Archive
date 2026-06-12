---
title: "Is installing ddclient with apt-get  without configuring it possible?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by CharlesA on 2009-12-16
Hi,

I'm trying to write a script that'll get everything setup on a clean install. I am wondering if it's possible to install *ddclient* from apt-get without it configuring the package with **debconf**.

The reason I am asking is that I already have a conf file for it set up, so I just want it to install ddclient and I'll create the conf file myself.

Is this possible?

Thanks in advice.

---

### Post by bruno9779 on 2009-12-16
what if you let it do it, and then just overwrite the file?

alternatively, after setting it up you could remove the conf file

---

### Post by CharlesA on 2009-12-16
> **bruno9779 said:**
> what if you let it do it, and then just overwrite the file?

alternatively, after setting it up you could remove the conf file

I was going to do that as a last resort, since I was to run the script with minimal prompting.

If it's not possible, I'll just configure ddclient as one of the last steps. :)

---

