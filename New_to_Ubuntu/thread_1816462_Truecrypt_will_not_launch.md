---
title: "Truecrypt will not launch"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by robmard on 2011-08-02
I am new to Linux and Ubuntu. I am using Ubuntu 11.04. I have installed Truecrypt and it appears to install correctly but nothing appears to happen when I click the Truecrypt icon to launch the application. I checked the other Truecrypt threads and could not find a similar problem. Am I missing something simple? Thanks.

---

### Post by alphacrucis2 on 2011-08-02
> **robmard said:**
> I am new to Linux and Ubuntu. I am using Ubuntu 11.04. I have installed Truecrypt and it appears to install correctly but nothing appears to happen when I click the Truecrypt icon to launch the application. I checked the other Truecrypt threads and could not find a similar problem. Am I missing something simple? Thanks.

It works ok for me on 11.04.Try running it from a terminal and see if it throws out any error messages.

---

### Post by EkuquoL on 2011-08-02
GNU already has a encryption embedded into it... It could be conflicting your little program. Keep in mind that file encryptions only fortify while the system isn't turned on / you are not logged on.

---

### Post by alphacrucis2 on 2011-08-02
> **EkuquoL said:**
> GNU already has a encryption embedded into it... It could be conflicting your little program. Keep in mind that file encryptions only fortify while the system isn't turned on / you are not logged on.

Truecrypt doesn't conflict with other encryption methods.

---

### Post by robmard on 2011-08-02
Thanks for the advice. I tried launching Truecrypt in terminal and go the following error:

error while loading shared libraries: libfuse.so.2: wrong ELF class: ELFCLASS64

---

### Post by sandyd on 2011-08-02
> **robmard said:**
> Thanks for the advice. I tried launching Truecrypt in terminal and go the following error:

error while loading shared libraries: libfuse.so.2: wrong ELF class: ELFCLASS64
wrong arch. 

choose 64bit.

see pic.

---

### Post by robmard on 2011-08-02
I have found the problem. I was installing the 32 bit version of Truecrypt but I should have been installing the 64 bit version. I downloaded and installed the 64 bit version and it know works. Thanks for the help.

---

