---
title: "help with nctuns installation"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by leomyster on 2009-11-12
hello guys,

I am trying to install NCTUns on ubuntu 9.04. I am doing it as given in the instructions in this page :
[http://wiki.ehas.org/index.php?title=How_to_install_NCTUns_in_Debian/Ubuntu](http://wiki.ehas.org/index.php?title=How_to_install_NCTUns_in_Debian/Ubuntu)

I am stuck at step "Build NCTUns".
How do i 'enable all configuration variables except install_kernel'??

Pleas help me out guys. I don't have Fedora and am earnestly trying to get it installed in ubuntu. How exactly do i do that step?

---

### Post by indigodavid on 2010-07-07
You have to create a file named install.conf and then you copy into it the content of the file 

install.conf-example

that is on NCTUns installation folder. Then you check in the file you created that all the variables are equal to yes, with the exception of install_kernel, that must be equal to no.

install_kernel=no

---

### Post by jayaram_21 on 2010-10-26
hello i m trying to install nctuns on kubuntu9.04
but the following command [http://nsl10.csie.nctu.edu.tw/download/NCTUns-allinone-linux-2.6.25.9-f9.20080919-3.tar.gz](http://nsl10.csie.nctu.edu.tw/download/NCTUns-allinone-linux-2.6.25.9-f9.20080919-3.tar.gz) is not working:(:(:(:(:(:(:(
i m getting error as 404:not found what to do for this??

---

