---
title: "Public key not available error"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2009-01-22
I get the following error every time I run update-manager:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C71839136CF5CE97
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513

Here is my source list as well:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed main universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed main universe #Added by software-properties
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
deb [http://ppa.launchpad.net/bearoso/ubuntu](http://ppa.launchpad.net/bearoso/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/bearoso/ubuntu](http://ppa.launchpad.net/bearoso/ubuntu) intrepid main
deb [http://ppa.launchpad.net/project-neon/ubuntu/](http://ppa.launchpad.net/project-neon/ubuntu/) intrepid main #Amarok
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) intrepid main #Screenlets
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free #VirtualBox
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe


I have some things on here twice, is that my problem. Thank you.

---

### Post by kostkon on 2009-01-23
You need to add the keys for the three PPAs that you have in your software sources list, because now PPAs offer signed packages. Thus, for example for the following PPA in your list:
```
deb http://ppa.launchpad.net/bearoso/ubuntu intrepid main
```
you'll need to go to the PPA's page on *Launchpad*, i.e. [here]("https://launchpad.net/~bearoso/+archive"), and then press on the link for the key. You'll get [this page]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0xDCEF94F365801075ECBB7353C71839136CF5CE97&op=index"). Again press the first link and you'll see the actual gpg key (i.e. [this]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xC71839136CF5CE97")). Copy the text (start copying from the *-----BEGIN PGP PUBLIC KEY BLOCK-----* section) and then paste it in the text editor. Save it for example on your desktop (better save it with the *.key* extension) like this
```
bearoso.key
```
Then go in *System &#8594; Adminstration &#8594; Software Sources* and in the *Authentication* tab select the *Add Key* button to add the key you have saved.

Repeat the above steps for the rest of the PPAs that you have in your sources list.

Hope that helps.

---

### Post by blackgr on 2009-01-23
I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
You have to run this with sudo

---

### Post by war59312 on 2009-01-26
Yeah I too was wondering what the heck...

Anyhow.. Nice script blackgr.. Can someone else pls cofirm it is safe?

Update: Script worked great, thanks a lot!!

---

### Post by Lostincyberspace on 2009-01-26
> **war59312 said:**
> Yeah I too was wondering what the heck...

Anyhow.. Nice script blackgr.. Can someone else pls cofirm it is safe?

It is safe if you downloaded it you could open it up and look at the code your self.

I don't know a ton about the code there but I was able to pic out the commands and I recognize most of them.

---

### Post by adobrakic on 2009-01-26
The script is fine, I used it.

---

### Post by bigstras on 2009-01-26
@blackgr, thanks for the script... made things a lot easier.

---

### Post by blackgr on 2009-01-26
im glad it helped! i know its hard to set all the keys manually especially if you have many entrys from launchpad.

---

### Post by woyzeckswoe on 2009-01-27
> **blackgr said:**
> I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
You have to run this with sudo

i love you;)
worked smooth like oil for me too.
nice nice

---

### Post by FAMUgolfer on 2009-01-27
Can't wait to mark this thread as SOLVED

Thank You blackgr!!!!!!!!!

---

### Post by war59312 on 2009-02-03
Well just starting happening again and script does not solve the problem. :(

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FE8956A73C5EE1C9

ok disabled Midori third party software source and no more errors, looks like there is no key for it.. :(

this is: [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu)

---

### Post by jerome1232 on 2009-02-04
> **war59312 said:**
> Well just starting happening again and script does not solve the problem. :(



ok disabled Midori third party software source and no more errors, looks like there is no key for it.. :(

this is: [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu)

This repo has midori and it has a key

[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)


The key is here [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x991E6CF92D9A3C5B](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x991E6CF92D9A3C5B)

---

