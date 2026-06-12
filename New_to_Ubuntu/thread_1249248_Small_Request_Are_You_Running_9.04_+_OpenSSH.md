---
title: "Small Request: Are You Running 9.04 + OpenSSH?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by mapes12 on 2009-08-25
Hi

I'm having problems with very slow file transfer speeds between two 8.04 machines which are running OpenSSH 4.7. After 2 hours of Googling and reading it would appear that there maybe a bug in 4.7 causing my problem (client side). I've checked the Backports repo but there isn't are more up to date version. The only way I can see to upgrade is to compile from source, but that's too scary for me. Therefore, if 9.04 has a more up to date version above 4.7 I think I will go to the trouble and upgrade both machines. 

If you have 9.04 + OpenSSH to check the version - Terminal ```
ssh -V
```

TIA

Mark

---

### Post by miklcct on 2009-08-25
You can try grabbing the packages from the mirrors by hand and install them.

---

### Post by jimcooncat on 2009-08-25
Or maybe roll-your-own backport:
[https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu)

---

### Post by XCan on 2009-08-25
> **mapes12 said:**
> Hi

I'm having problems with very slow file transfer speeds between two 8.04 machines which are running OpenSSH 4.7. After 2 hours of Googling and reading it would appear that there maybe a bug in 4.7 causing my problem (client side). I've checked the Backports repo but there isn't are more up to date version. The only way I can see to upgrade is to compile from source, but that's too scary for me. Therefore, if 9.04 has a more up to date version above 4.7 I think I will go to the trouble and upgrade both machines. 

If you have 9.04 + OpenSSH to check the version - Terminal ```
ssh -V
```

TIA

Mark

```
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
```

---

### Post by mapes12 on 2009-08-25
Thanks everyone. It looks like 9.04 has OpenSSH 5.1 which I'm hoping will solve my problem.

However, before upgrading two machines I thought I'd have a go at what jimcooncat suggested:

> **jimcooncat said:**
> Or maybe roll-your-own backport:
[https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu)

I had to change the wiki instructions to get this to work because I'm usung a test machine running 9.10 (which I test everything on before deploying to main machines) Also, error messages kept popping up without the feed to the Debian .dsc file.

This is what I did:

Install Prevu ```
sudo apt-get install prevu
```Then initialsed it per the wiki ```
sudo -E prevu-init
```Let it run then sure enough it asks for confirmation to add to sources list > You can have APT use the packages built by prevu by adding this to /etc/apt/sources.list:
        deb file:/var/cache/prevu/karmic-debs ./
Would you like prevu to do this for you? [Y/N]I selected yes but given that I was looking to create a Backport for Hardy this file was of no relevance. See later.

Under the side heading "Use" I tried all the options everything except option 3. failed. To find the correct .dsc package you need to navigate through the Debian Package site carefully.

I went to: [http://packages.qa.debian.org/common/index.html](http://packages.qa.debian.org/common/index.html) as the wiki said. In the search field "openssh" took me to here: [http://packages.qa.debian.org/o/openssh.html](http://packages.qa.debian.org/o/openssh.html) Somewhat confusing what to do next but look down the left hand side to "Versions". Click "stable:1:5.1p1-5" or whichever you need. Then you end up here: [http://packages.debian.org/source/stable/openssh](http://packages.debian.org/source/stable/openssh) Any of the related package links on the left will take you to the same place. I clicked on the first option "openssh-client". 

The next page is the page you need. On the right is a file called "[openssh_5.1p1-5.dsc]". Right click it, Properties then copy the link into your clipboard. 

Now, if you are running the version of Ubu you are looking create the Backport for then you can just go ahead and have prevu do its stuff like this ```
prevu http://ftp.de.debian.org/debian/pool/main/o/openssh/openssh_5.1p1-5.dsc
```But in my case I need to have Prevu configured to backport for Hardy (because I'm running Karmic). So to configure for Hardy ```
DIST=hardy sudo -E prevu-init
```Once that's done I could then build the Backport from the .dsc file like this ```
DIST=hardy prevu http://ftp.de.debian.org/debian/pool/main/o/openssh/openssh_5.1p1-5.dsc
```

I now have my package .deb files in file:/var/cache/prevu/hardy-debs - I've taken a screenshot.

So I guess I can just move them off this test machine onto my production machines and install. That's the next step. Do I need to publish these Backported openssh .debs anywhere for others to access? There aren't any in the Hardy Backports repo? And how would I do it?

---

### Post by mapes12 on 2009-08-25
Alas, it was not to be. I moved the openssh-client and openssh-server debs to my other machine. The Gdebi Package Installer then threw out a dependency error about libssl0.9.8 and refused to go any further. I checked with ```
sudo apt-get install libssl0.9.8
``` to be told that I already have the latest version installed.

Hmmmmm............off down the upgrade root then

:lolflag:

---

### Post by jimcooncat on 2009-08-26
Sorry it didn't work out for you. You gave it a good shot, though!

---

