---
title: "Upgrading to Openoffice 3 from Pen Driver"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by varadharajanv1983 on 2009-01-31
I downloaded all the .deb files from

[http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/)

to my windos PC and copied to a PEN Drive

No how to update the Openoffice 2.4.1 in Ubuntu Intepid 8.10
using his pen drive

Since I am using five computers I should not want to connect all the computers to internet so i need to install these packages from pen drive

suggest me a solution

---

### Post by prshah on 2009-01-31
> **varadharajanv1983 said:**
> how to update the Openoffice 2.4.1 in Ubuntu Intepid 8.10 using this pen drive

Copy the DEBs from the pendrive to each computers HDD, to a subdirectory in your home directory (~). (You can delete from the harddrive once installed, this will save wear-and-tear on your pen drive).

Uninstall the existing open office from synaptic. (Optional)

Install the new DEBs with the command```
sudo dpkg -i *.deb
```

Note that this will not install icons for openoffice to the menu. In the downloaded files, you will find a subdirectory containing the DEB required to install the menu shortcuts. Double click on it to install program shortcuts in the menu.

Post back if you need more specific instructions,

---

### Post by varadharajanv1983 on 2009-02-01
Thanks for your valuable solution for installing openoffice 3

but i did not downloaded the linux deb archive from Openoffice.org site which can be unpacked and installed


i just downloaded the deb files from launpad ubuntu which can be used for update manager to update openoffice

So how to manually update the openoffice using this debs 

I tried to install debs using sudo dpkg -i *.deb

but there are lot of warnings and errors

so i need a method to direct the update manager to get deb files from my pen drive

so how to do that

is there any procudure to follow

Why i need this solution is, I am trying to write a python script to automates the Impress presentation files from a know folder. for that i need to monitor the presentation events

I just gone through the Openoffice 2.4.1 and I read that there is no slideshow event interfaces 

So that I am moving to openoffice 3 since it holding the XSlideShowEvent interface

so how o do that ?

---

### Post by HotShotDJ on 2009-02-01
> **varadharajanv1983 said:**
> Since I am using five computers I should not want to connect all the computers to internet so i need to install these packages from pen drive

suggest me a solutionSet up a local repository on your network or on each computer.  See: [http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)

---

### Post by prshah on 2009-02-03
> **varadharajanv1983 said:**
> 
but there are lot of warnings and errors


Please post the specific warnings and error messages.

---

