---
title: "Synaptic Ubuntu Icon and how to tell if a package is installed"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by cparmer on 2011-06-30
Hi all,

I read that the Ubuntu Icon next to packages in Synaptic Package Manager means that the package is installed by default on Ubuntu. 
a) is this true?
b) if I search 'lapack', then synaptic tells me that liblapack-dev is installed (because of the ubuntu icon). However, if I search dpkg --get-selections | grep blas in terminal, nothing 
appears. So, how do what is the best way to know if a package is installed already?

Thanks!

---

### Post by amjjawad on 2011-06-30
> **cparmer said:**
> Hi all,

I read that the Ubuntu Icon next to packages in Synaptic Package Manager means that the package is installed by default on Ubuntu. 
a) is this true?
b) if I search 'lapack', then synaptic tells me that liblapack-dev is installed (because of the ubuntu icon). However, if I search dpkg --get-selections | grep blas in terminal, nothing 
appears. So, how do what is the best way to know if a package is installed already?

Thanks!

Ubuntu icon means it's supported by Ubuntu (Canonical).

If the box is GREEN then that means it's installed.

---

### Post by ajgreeny on 2011-06-30
In synaptic's left hand pane choose **Status->Installed** and you will see all that is already installed on your machine.

If you choose Not-installed you will see there are many packages that are not installed by default, but still show the ubuntu logo.  The icon simply shows if that package is supported by ubuntu itself, or by another organisation.  It is nothing to do with the package being in a default installation of ubuntu.

---

