---
title: "libyaz3 and dependencies not downloading"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Booky_lillz on 2011-04-30
I am trying to install Koha 3.02.01 on Ubuntu 10.04 Linux Lucid I have had loads of problems (including my IT Linux expert quitting leaving beginner me to handle it) now my prroble is that I need libyaz3 however it won't work because
>>  Depends: libgnutls13 (>=1.4.0-0) but it is not installable
>>   Depends: libicu36  but it is not installable

Also I need idzebra-2.0 but that depends on libyaz3

Any help would be appreciated 

Thanks.

---

### Post by Paddy Landau on 2011-04-30
I have not heard of Koha (and its website is not responding at this time), but it looks as though libgnutls13 and libicu36 have been superseded by libgnutls26 and libicu42 respectively. I could be wrong, but that's what it looks like.

I see several results when Googling "koha ubuntu", including [Koha's own description]("http://wiki.koha-community.org/wiki/Koha_on_Ubuntu"). If you don't have any luck, contact Koha about these dependencies.

---

### Post by Booky_lillz on 2011-05-02
Thanks.

---

### Post by Booky_lillz on 2011-05-04
Ok That didn't work further searching found me this [https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/304261](https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/304261)
 
 
 
 
  but I don't understand it.  Can this help me?

---

### Post by Paddy Landau on 2011-05-05
It seems to me -- but I could be wrong -- that Koha requires libgnutils and libicu. However, Koha seems to explicitly require versions 13 and 36, but they are unavailable as versions 26 and 42 are already in use. (Two versions cannot be installed at the same time. If you uninstall libgnutil26 to install libgnutils13, you'll break the programs that depend on the later version.)

Have you contacted Koha to ask for help?

---

