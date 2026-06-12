---
title: "need help with frostwire install"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Indy452 on 2010-05-02
I downloaded the new version and this error comes up...what does it mean?

I thought that installing the Ubuntu restricted extras would have that version of Java in it but??? I guess not.

How can I get this fixed?

---

### Post by akand074 on 2010-05-02
weird.. I literally just reinstalled Frostwire with my new install of Lucid and it automatically installed the java jre. Anyways go to Accessories > Terminal and copy/paste this in:

```
sudo apt-get install sun-java6-jre
```

hope that helps.

---

### Post by Indy452 on 2010-05-02
It is weird...I shouldn't be having this trouble..I may have a bad burn or something hmmm.

Look..

---

### Post by akand074 on 2010-05-02
Weird... try going to System > Administration > Synaptic Package Manager and searching the java jre and see if you can find it and install it from there. Also in synaptic package manager, go to Settings > Repositories, and then go to the second tab labeled "Other software" and make sure everything there is checked.

---

### Post by Indy452 on 2010-05-03
Shut it down last night and this AM was able to install fine...I don't know what the deal was last night.  This Am Gdebi needed 6 additional packages to install and it fetched them, I agreed and FW is up and running.

I thought that version of Java was in the Ubuntu restricted extras...oh well.

Thanks for the help.

---

