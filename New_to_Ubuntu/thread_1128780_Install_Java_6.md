---
title: "Install Java 6"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Veehmot on 2009-04-18
I'm following some steps found via googling, and this is my output:

[SIZE="4"]**sudo apt-get update**[/SIZE]

```
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-security Release.gpg
Ign http://us.archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://us.archive.ubuntu.com intrepid-updates Release
Hit http://us.archive.ubuntu.com intrepid-security Release
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-security/main Packages
Hit http://us.archive.ubuntu.com intrepid-security/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-security/main Sources
Hit http://us.archive.ubuntu.com intrepid-security/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-security/universe Packages
Hit http://us.archive.ubuntu.com intrepid-security/universe Sources
Hit http://us.archive.ubuntu.com intrepid-security/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-security/multiverse Sources
Reading package lists... Done
```

[SIZE="4"]**sudo apt-get install sun-java6-jre sun-java6-plugin**[/SIZE]

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```

I tried using source Main Server and this output is for server from US.

Oh I'm using Ubuntu Intrepid 8.10 64-bit version

---

### Post by amingv on 2009-04-18
If I recall correctly ubuntu-restricted-extras includes that package, maybe try there.

---

### Post by James_Lochhead on 2009-04-18
There are debs available for Jaunty. Just type details of package sun java in jaunty in google and a page where you can download them should pop up.

---

### Post by gandaran on 2009-04-18
I believe you must be running a 64-bits ubuntu, there is no sun-java6-plugin for 64-bits systems in the repositories, what you must do is remove all java you have installed then go to [java website]("http://java.com/en/download/manual.jsp") download the linux 64-bits package, read the instructions there for installing and linking java to firefox.

---

### Post by Crafty Kisses on 2009-04-18
Just download the latest version from Java right here: [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp). The following instructions are going to assume you're going to save it to your desktop and the file name is "java.bin". So what you want to do is navigate to the Terminal and run these commands:
```
cd ~/Desktop
chmod +x java.bin
sudo mv java.bin /opt
cd /opt
sudo ./java.bin
```
Once you've done that it will start unzipping the files in the /opt directory, there should be a new directory, and not sure what it would be called, but navigate to it:
```
cd jre_directory/bin
sudo ln -s /opt/jre_directory/bin/java /usr/local/bin/java
```
There's also instructions on Java's website if you don't understand mine, but if you followed mine, that should get Java up and running.

---

### Post by eddski on 2009-04-18
to grandaran: how do you remove all instances of java?

---

### Post by gandaran on 2009-04-18
> **eddski said:**
> to grandaran: how do you remove all instances of java?
open synaptic package manager, scroll down to sun-java6 or any other java (type java in search box) mark for complete removal all installed java packages and hit the apply button.

---

### Post by Paqman on 2009-04-18
> **gandaran said:**
> I believe you must be running a 64-bits ubuntu, there is no sun-java6-plugin for 64-bits systems in the repositories, what you must do is remove all java you have installed then go to [java website]("http://java.com/en/download/manual.jsp") download the linux 64-bits package, read the instructions there for installing and linking java to firefox.

Or just install ubuntu-restricted-extras, which will install the sun-java6-jre and the icedtea6-plugin automatically.

---

### Post by Veehmot on 2009-04-18
Thanks, I installed ubuntu-restricted-extras and it worked!

Thanks for your time.

---

### Post by gandaran on 2009-04-18
> **Veehmot said:**
> Thanks, I installed ubuntu-restricted-extras and it worked!

Thanks for your time.
the icedtea6-plugin (open-java) does work but only on some sites, some other sites you'll need sun-java!

---

