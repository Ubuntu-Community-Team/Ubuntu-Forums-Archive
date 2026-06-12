---
title: "Upgrade process - existing packages ?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by Eben Fourie on 2009-12-22
I've read the [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) page.
 
What actually happens when you upgrade i.t.o. package downloads ?
 
Let's say I am running 9.04, with lots of (large) development packages installed:
 
sun-java-jdk, php, mysql, apache2 etc
 
When I upgrade 9.10, what gets downloaded ? Just the parts of the OS that have changed, or new (karmic) versions of all currently installed packages ?
 
I guess another way of asking the question would be if you upgrade a "standard" Ubuntu installation, will that involve less download than upgrading an Ubuntu installation with lots of existing software installed on it ?
 
Is there any way of determining beforehand how much bandwidth you will require to upgrade ?
 
Hope this makes sense :)

---

### Post by slakkie on 2009-12-22
> **Eben Fourie said:**
> I've read the [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) page.
 
What actually happens when you upgrade i.t.o. package downloads ?
 
Let's say I am running 9.04, with lots of (large) development packages installed:
 
sun-java-jdk, php, mysql, apache2 etc
 
When I upgrade 9.10, what gets downloaded ? Just the parts of the OS that have changed, or new (karmic) versions of all currently installed packages ?
 
I guess another way of asking the question would be if you upgrade a "standard" Ubuntu installation, will that involve less download than upgrading an Ubuntu installation with lots of existing software installed on it ?
 
Is there any way of determining beforehand how much bandwidth you will require to upgrade ?
 
Hope this makes sense :)

Every package you have installed will be upgraded if the package exists on the repository of the release you are upgrading to. Which packages will be upgraded are calculated by the update-manager package. See also [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades) for various ways of upgrading.

If you want to limit bandwidth, use the alternate CD to upgrade.

Best of luck.

---

### Post by Paqman on 2009-12-22
Any applications or packages that you install from the normal Ubuntu repos will get automatically upgraded when you upgrade the OS. 

During an upgrade the system will disable any other repos you are using (such as PPAs, Google repo, Medibuntu, etc). You'll than have to manually switch them to the correct version after the upgrade. Obviously you'll want to check that they support the new version before upgrading.

Anything you install from a .deb or a tarball simply won't be upgraded at all. This is one of the main reasons why it's always best to use software from the repos.

---

### Post by crtlbreak on 2009-12-22
AFAIK
there will be universe and multiverse packages marked as the matched new version <karmic> but they could be identical to the previous version <ibis>  - depending whether they have had amendments in the interim between releases.
As most of the people (contributors) who develop their packages are continually refining their respective releases the chances of a package being identical to the previous release is quite slim - but the possibility is there. With something like samba it is more likely to be almost identical apart from a possible bug fix (if one has occurred) between releases.
the bigger is always the better when it comes to bandwidth, memory and processor power. The download of a new release will just take longer if you have a more tailored installation - irrespective of bandwidth.
hope this helps.

---

### Post by Eben Fourie on 2009-12-23
thank you

---

