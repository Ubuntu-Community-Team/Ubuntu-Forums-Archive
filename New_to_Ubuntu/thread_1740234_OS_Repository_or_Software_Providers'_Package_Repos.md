---
title: "OS Repository or Software Providers' Package Repository?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by garl on 2011-04-26
I'm trying to understand the difference between the OS Repositories and Software Providers' Package Repositories. 


For example, in Software Sources I have: [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu)
Is this through Ubuntu or LibreOffice? How do you tell the difference?


Could someone please explain, and maybe show an example of each? Thank you!

---

### Post by cipherboy_loc on 2011-04-26
OS Repositories come from the Ubuntu domain ([http://www.ubuntu.com/foo](http://www.ubuntu.com/foo)), while Software Providers' Repositories from from all other domains ([http://ppa.launchpad.net](http://ppa.launchpad.net), etc). OS Repositories provide most of the packages, while Software Providers' Repositories contain specialized software. Debian and others have their own OS Repositories providing other versions of software, etc. It is generally speaking not wise to enable other OS Repositories outside of your OS's repositories.



Cipherboy

---

### Post by garl on 2011-04-26
I read that the OS repositories contain most applications? I'm not sure if I'm understanding right, but would there be a way to add LibreOffice through the OS repositories? And where do you find the repositories to add?

---

### Post by cipherboy_loc on 2011-04-26
If you take the jump and install 11.04, LibreOffice is in those repositories (replacing OpenOffice). And no, OS Repositories can not be modified by the user on their system, but other repositories (containing various softwares) can be. Most of the repositories I have are from Launchpad ([http://launchpad.net](http://launchpad.net)), and you can install more via Ubuntu-Tweak. Oh, and yes, OS Repositories contain most of the applications on your system (all if you have a fresh install).


Cipherboy

---

### Post by el_koraco on 2011-04-26
The OS repositories are Ubuntu's repositories, maintained by Canonical. The packages in them are taken from Debian unstable, some of them tweaked a little, and "frozen" a month before release. That means that no new applications enter the official repositories. 

If you want to stay on top of newer software, but don't want to compile, you can enable further "Personal package archives", or binary packages maintained by others, be it individual developers or big projects like Google Chrome, Firefox and so on.

---

### Post by garl on 2011-04-26
Ok, so OS repositories contain all the software that's installed in the OS by default? And they update through the update manager? Thanks so much for your help! I've only been using Ubuntu (or Linux for that matter) for a couple of days. :)

---

