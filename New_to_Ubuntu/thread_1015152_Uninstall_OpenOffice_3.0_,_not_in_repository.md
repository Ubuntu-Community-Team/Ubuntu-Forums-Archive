---
title: "Uninstall OpenOffice 3.0 , not in repository"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by sah302 on 2008-12-18
Hi all!

I have recently installed OpenOffice 3.0 using this method: 

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

but then it's not in the repository and exists along side OpenOffice 2.4, so then I had found a better tutorial for installing 3.0 here:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

However when I try and do the 'reload' step after adding the software source I get the following error:

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE

I can't help but wonder if it's because I already have open office 3.0 installed? I thought if I remove my current installion of OO3.0 it would work, but I can't figure out how to do this.

Any suggestions? Thanks in advance!

---

### Post by kanikilu on 2008-12-18
It seems the error you are getting is related to VirtualBox, not OOo3.

Try importing the key again, [instructions from the VBox page]("http://www.virtualbox.org/wiki/Linux_Downloads"):

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

---

### Post by gettinoriginal on 2008-12-18
Just use the following syntax:
sudo apt-get remove {package-name}

Remove package with all configuration files, enter:
$ sudo apt-get --purge remove lighttpd

To list all installed package, enter:\
dpkg --list
dpkg --list | less
dpkg --list | grep -i 'http'

:p

---

### Post by sah302 on 2008-12-18
Thank you, kanikilu's solution worked.

Edit: Can I mark my own thread as solved or does a mod do that? I can't seem to edit the title.

---

### Post by Simplicius on 2008-12-18
> **sah302 said:**
> 

Edit: Can I mark my own thread as solved or does a mod do that? I can't seem to edit the title.

Look in Thread Tools, on the page's right top corner.

---

### Post by kanikilu on 2008-12-18
> **sah302 said:**
> Thank you, kanikilu's solution worked.

Edit: Can I mark my own thread as solved or does a mod do that? I can't seem to edit the title.

Yes, look under the thread tools link above your first post, and it should have it there.

*EDIT* - gah, too slow, opened this tab a few minutes ago

---

