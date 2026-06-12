---
title: "problem with restricted-extra"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by aam-aadmi on 2011-05-20
Hi All,

I just installed Ubuntu 10.04 on a Dell Latitude E5510. I followed the advice on [HTML]http://ubuntuguide.org/wiki/Ubuntu:Lucid#Add_Extra_Repositories[/HTML]
by adding the extra repositories and geeting the keys, etc. Then I proceeded to install the restricted extras with ```
sudo apt-get install ubuntu-restricted-extras

```

but the process does not finish. The terminal just freezes with the following message:
```
TrueType core fonts for the Web EULA                                      &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement       &#9618; 
 &#9474; ("EULA") is a legal agreement between you (either an individual or a      &#9618; 
 &#9474; single entity) and Microsoft Corporation for the Microsoft software       &#9618; 
 &#9474; accompanying this EULA, which includes computer software and may include  &#9618; 
 &#9474; associated media, printed materials, and "on-line" or electronic          &#9618; 
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your      &#9618; 
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be    &#9618; 
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of      &#9618; 
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                          &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>     
```

The <Ok> is not enabled and I cannot proceed any further. Any advice?

---

### Post by josephmills on 2011-05-20
lets try an install it using System-->Admin-->synaptic package manager then type in ubuntu-restricted-extras in the search bar click on it mark for install and then press the apply button then open your terminal anad ```
sudo apt-gwt upgrade 
``` are they installed?

---

### Post by Dennis N on 2011-05-20
Just press the right arrow key (tab key might work also) until the ok at the bottom turns red (or is highlighted). then you can press enter and continue.

---

### Post by wildmanne39 on 2011-05-20
> **aam-aadmi said:**
> Hi All,

I just installed Ubuntu 10.04 on a Dell Latitude E5510. I followed the advice on [HTML]http://ubuntuguide.org/wiki/Ubuntu:Lucid#Add_Extra_Repositories[/HTML]
by adding the extra repositories and geeting the keys, etc. Then I proceeded to install the restricted extras with ```
sudo apt-get install ubuntu-restricted-extras

```

but the process does not finish. The terminal just freezes with the following message:
```
TrueType core fonts for the Web EULA                                      &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement       &#9618; 
 &#9474; ("EULA") is a legal agreement between you (either an individual or a      &#9618; 
 &#9474; single entity) and Microsoft Corporation for the Microsoft software       &#9618; 
 &#9474; accompanying this EULA, which includes computer software and may include  &#9618; 
 &#9474; associated media, printed materials, and "on-line" or electronic          &#9618; 
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your      &#9618; 
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be    &#9618; 
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of      &#9618; 
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                          &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>     
```

The <Ok> is not enabled and I cannot proceed any further. Any advice?
Hi, thats because it is waiting for you to accept the agreement. I think you use the down arrow and you can high light the ok then click enter and it should finish.

---

### Post by aam-aadmi on 2011-05-20
Using the synaptic package manager worked! Thanks Joseph Mills.

---

