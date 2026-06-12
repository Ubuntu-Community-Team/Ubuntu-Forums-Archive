---
title: "installing .rpm file..."
date: 2009-07-20
forum: New to Ubuntu
---

### Post by CD4+ on 2009-07-20
is there way to install .rpm file on ubuntu.. please help...

regards
cd-4+

---

### Post by yeats on 2009-07-20
You could try a program called alien (in the repos)...  What is it you're trying to install?

---

### Post by TuckLive on 2009-07-20
Not without converting it to .deb.  If the program you want has a .deb package use that.  If not this will show you how to convert [http://http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html]("http://http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html").  It has step-by-step instructions.

---

### Post by ahmatti on 2009-07-20
You can do this easily with alien and a lot of times it also works nicely. First install alien:

```
sudo apt-get install alien
```

then install the rpm:

```
sudo alien -i -c someprogram.rpm
```

---

### Post by Rodemire on 2009-07-24
Hallo,

I have a similar problem. I downloaded an rpm package instead of the deb package for Adobe Reader. The problem i have now is at my wotkplace they have put restrictions on download sizes and they are on to me. I installed alien so i could convert to a .deb package but when i installed and evrything I got the following error:

"Failed to execute child process "acroread" (Permission denied)"

What have I done wrong?

---

### Post by Rodemire on 2009-07-24
I apologise for the above message, I realised when I was converting to deb packages that i was using the following command:

sudo alien -i AdobeReader.rpm

and I was not including the scripts, that is, with the argument -c. So i used the command below and it worked:

sudo alien -ic AdobeReader.rpm 

Sorry again.

---

### Post by oldos2er on 2009-07-24
Adobe Reader is in the repositories.

---

### Post by philcamlin on 2009-07-24
> **oldos2er said:**
> Adobe Reader is in the repositories.

yes there is no need to install an rpm when its in synaptic :popcorn:

---

### Post by Rodemire on 2009-07-24
Yes, Adobe is in the repos. I am schooling myself on using Linux so i was trying my hand at installing manually downloaded packages. It worked out for the better as i now know about alien, rpms and manual installation.
Thanks guys.

---

### Post by markharding557 on 2009-07-24
you can find the vast majority of things in .deb format

---

### Post by Mark Phelps on 2009-07-25
I know from experience that while converting an .rpm to a .deb DOES work using Alien, the result does not always work.  I've run into situations where, especially with libraries, the component names are different in the .deb packages than in the .rpm packages.

As others have said, it's best to check Synaptic first, and if there's nothing there, you can always do a search of the Debian libraries to see if such a package DOES exist.

---

### Post by aysiu on 2009-07-25
If you don't see Adobe Reader in the repositories, you may have to add some:
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

---

### Post by CD4+ on 2009-08-02
soory for replyn late as i was out of station... I tried to install via the way mentioned here: [http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html).

but to my surprise when i try 
# alien -k VMware-Workstation-6.5.2-156735.i386.rpm
i get the following:

Warning: Skipping conversion of scripts in package VMware-Workstation: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
chown: changing ownership of `VMware-Workstation-6.5.2//var/cache/vmware/VMware-Workstation-6.5.2-156735.i386.bundle': Operation not permitted
failed chowning /var/cache/vmware/VMware-Workstation-6.5.2-156735.i386.bundle to 0:0:  at /usr/share/perl5/Alien/Package/Rpm.pm line 263, <GETPERMS> line 1.

please help ...


regards
CD4+

---

### Post by Riaku on 2009-08-02
normally you'd install the .deb file and not the the .rpm. check to see if there's one before doing this but :
[http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html](http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html)

---

### Post by CD4+ on 2009-08-03
well riaku thats the same method i did and the following result i got in the last post... 

regards
CD4+

---

### Post by CD4+ on 2009-08-05
please reply someone to my problem please.. 

regards
cd4+

---

