---
title: "WINE is old"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by bart1452 on 2008-12-23
I've got WINE 1.0 from the Ubuntu repository, but it is an old version. Is the Ubuntu Project going to add a current version?

---

### Post by jerome1232 on 2008-12-23
> **bart1452 said:**
> I've got WINE 1.0 from the Ubuntu repository, but it is an old version. Is the Ubuntu Project going to add a current version?

1.0.1 is the current stable version.

You can add winehq's repository if you want the newer beta versions [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by bart1452 on 2008-12-23
Thanks. I was having trouble getting the WINE repository loaded in the Software Sources. That's fixed, at least I have one that has 1.1.10. I'd like to get the 1.1.11 version that's supposed to have some bug fixes and maybe a few new functions, but I'm having trouble getting the complete APT line for the Software Sources to accept it.

---

### Post by kostkon on 2008-12-23
> **bart1452 said:**
> Thanks. I was having trouble getting the WINE repository loaded in the Software Sources. That's fixed, at least I have one that has 1.1.10. I'd like to get the 1.1.11 version that's supposed to have some bug fixes and maybe a few new functions, but I'm having trouble getting the complete APT line for the Software Sources to accept it.
Wine 1.1.11 is not yet available for Ubuntu yet. If you added the Wine repository to your software sources list then just be patient, will come to you as an update pretty soon.

---

### Post by BGFG on 2008-12-23
Ubuntu tweak also easily adds the wine repo, as well as many other useful apps really easily.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by jimmyhacker on 2008-12-27
you can switch to slackware for wine 1.8 stable.check wine repository.

---

### Post by 3rdalbum on 2008-12-27
> **jimmyhacker said:**
> you can switch to slackware for wine 1.8 stable.check wine repository.

Does Slackware also have Duke Nukem Forever? :-P   There is no Wine 1.8 yet - do you mean 1.1.8? Seems a bit drastic to change distributions just to get a more recent Wine, especially when the Wine HQ repository has a later version (1.1.10) than Slackware anyway.

---

### Post by blazemore on 2009-02-04
1. ```
sudo su
```
This means that all commands run from now on will be run as the Super User (root), until you close the terminal window.


2.```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add
```
We download (wget) something called a "key" that verifies downloaded installation files. We install it. (apt-key add)


3. ```
echo deb http://wine.budgetdedicated.com/apt intrepid main >> /etc/apt/sources.list
```
echo just means display the next bit. The >> means append to the file /etc/apt/sources.list, which is a list of locations your computer uses to get software, when you ask it to.
In this case, we're using the official Wine repository, which has a more up-to-date version of Wine than the included Ubuntu repository.
We could just download the installation file from the Wine website, but the method I chose ensures Wine will be kept up-to-date.


4. ```
apt-get update
```
We refresh the list of repositories, making your computer aware of any new or updated packages


5. ```
apt-get install wine -y --force-yes
```
We install the package Wine (If it's not already installed). When the installer asks a question, we assume the answer is yes, even if yes is not the default option (You'll just have to trust me on this one!).


6. ```
apt-get upgrade -y --force-yes
```
If Wine was already installed, this command will update it to the version in the Wine repo, again, assuming Yes to all questions.

---

