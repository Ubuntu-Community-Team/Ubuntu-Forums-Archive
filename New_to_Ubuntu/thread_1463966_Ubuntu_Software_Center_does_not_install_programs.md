---
title: "Ubuntu Software Center does not install programs"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by jgerlach on 2010-04-27
I am running Ubuntu 10 on a Virtual Box.  The Ubuntu Software Center shows all the programs available for installation but when I select one,  I am not ask for my administrator password and so nothing happens.

---

### Post by Ceiber Boy on 2010-04-27
Is VB configured to allow Ubuntu to have Internet access?

---

### Post by demuxer on 2010-04-27
in fact, USC must authenticate after you click the INSTALL button, but if you are trying Lucid Lynx please be sure to have the latest beta and reporte the bug, also maybe this thread must be moved to another forum.

---

### Post by jgerlach on 2010-04-27
> **demuxer said:**
> in fact, USC must authenticate after you click the INSTALL button, but if you are trying Lucid Lynx please be sure to have the latest beta and reporte the bug, also maybe this thread must be moved to another forum.
Yes I am using the Internet connection for this post.  I downloaded the beta of Lucid Lynx on Monday so it should be the latest.  I am not sure that it is a bug.  I tweaked the VB settings.  I am not sure how to report a bug.

---

### Post by arnab_das on 2010-04-27
you need to update.

Go to Accessories > Terminal and type :

sudo apt-get update

**OR**

go to System >Administration > Update Manager and then check for updates.

Software Center will run fine after that.

---

### Post by jgerlach on 2010-04-28
Ran sudo apt-get update twice yesterday and again this morning.  Same problem USC does not ask for authentication and so does not appear to respond.

---

### Post by philinux on 2010-04-28
> **jgerlach said:**
> Ran sudo apt-get update twice yesterday and again this morning.  Same problem USC does not ask for authentication and so does not appear to respond.

Can you install via synaptic?

---

### Post by jgerlach on 2010-04-28
Sorry, I am unfamiliar with synaptic.

---

### Post by jgerlach on 2010-04-28
No problem using synaptic to install a game.

---

### Post by philinux on 2010-04-28
System>admin>software sources.

Try changing the server to main and then see if USC will run.

---

### Post by jgerlach on 2010-04-28
I deselected all the sources except for main and tried to download a program with the same result - no authentication request and no joy.

---

### Post by demuxer on 2010-04-28
ok, if synaptics is working fine, try this

sudo apt-get remove software-center
apt-get clean
apt-get check <- Is everything OK ?
restart
sudo apt-get install software-center
and try to add programs

if that fails, may be related to your user/group permissions, maybe you create a wrong group, so you can create a new user, re-login that user and try USC

---

### Post by jgerlach on 2010-04-29
Reinstalling USC had no effect.  However I noted that I could not create another user using System Administration Users and Groups.  I had to issue the command using a terminal window.  Then I got GUI but with a statement that Root was not enabled.  When I enabled it I could create another user and that user could get USC to work correctly.   PROBLEM SOLVED but I still don't know what is wrong with my original user.

---

### Post by cuberts on 2010-04-29
> **jgerlach said:**
> I am running Ubuntu 10 on a Virtual Box.  The Ubuntu Software Center shows all the programs available for installation but when I select one,  I am not ask for my administrator password and so nothing happens.I think that your problem might be that you are running it in Virtual BOx. So well you should be able to just click on the arrow of the program that you want to install. It is a little hard to explain right now because I am not on Ubuntu right now.

---

