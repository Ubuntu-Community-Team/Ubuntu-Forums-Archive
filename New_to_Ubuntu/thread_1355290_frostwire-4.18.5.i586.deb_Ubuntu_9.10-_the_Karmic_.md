---
title: "frostwire-4.18.5.i586.deb Ubuntu 9.10- the Karmic Koala"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-12-14
i downloaded from
[http://www.frostwire.com/](http://www.frostwire.com/)

i downloaded the frostwire-4.18.5.i586.deb

the install was different then in the past.

i have attached the install pic and errors pic

I have tried to run frostwire by clicking on the icon and command line frostwire.

---

### Post by cariboo on 2009-12-17
It looks like you haven't got the correct java version installed, try installing the xubuntu-restricted-extras meta package, it is in the repositories.

---

### Post by lance bermudez on 2009-12-18
I have the xubuntu-restricted-extras meta package and ubuntu-restricted-extras meta package installed. and it dose not work.

---

### Post by sreyan on 2009-12-20
> **lance bermudez said:**
> I have the xubuntu-restricted-extras meta package and ubuntu-restricted-extras meta package installed. and it dose not work.

You need to install sun's jre, and set it as the default.

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
sudo update-java-alternatives -s java-6-sun

frostwire doesnt seem to work with open jdk.

---

### Post by lance bermudez on 2009-12-21
sudo update-java-alternatives -s java-6-sun

fixed my prob i had all the other things already. thank you.

---

