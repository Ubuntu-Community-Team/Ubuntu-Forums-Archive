---
title: "repositories fail"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by soryu on 2009-12-23
i have updated but,some repositories cannot download or have been ignored old ones have been used instead.
how do i fix this?
the icon is still on the desktop.

---

### Post by bodhi.zazen on 2009-12-23
Can you post the contents of /etc/apt/sources.list ?

---

### Post by soryu on 2009-12-23
is this it?
GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/Release.gpg  Unable to connect to  http:
Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/karmic/i18n/Translation-en_US.bz2  Unable to connect to  http:
Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/main/i18n/Translation-en_US.bz2  Unable to connect to  http:
Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/karmic/binary-i386/Packages.gz  Unable to connect to  http:
Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/main/binary-i386/Packages.gz  Unable to connect to  http:
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Shpongle on 2009-12-23
have you tried to change your source ? , system -> admin-> software sources and change the download from  location , i had a problem like that for a good while , with the irish server so i used the uk one instead , its all good now tho :-)

---

### Post by Shpongle on 2009-12-23
oh looks like unverified keys , you can either remove those sources if you dont use them or you can get the keys and verify them , they should be on the webpages where you first added them ,

see [http://deb.opera.com/](http://deb.opera.com/)


and   [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/Release.gpg)

Synaptic window: Settings --> Repositories --> Authentication --> Import key file.

---

### Post by soryu on 2009-12-23
the icon is now gone, but it left before i made any changes. i changed the source anyway.
now there's no icon but i got this
GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/Release.gpg  Unable to connect to  http:
Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/karmic/i18n/Translation-en_US.bz2  Unable to connect to  http:
Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/main/i18n/Translation-en_US.bz2  Unable to connect to  http:
Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/karmic/binary-i386/Packages.gz  Unable to connect to  http:
Failed to fetch http:/dists///ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/main/binary-i386/Packages.gz  Unable to connect to  http:
Some index files failed to download, they have been ignored, or old ones used instead.
same thing.

the  icon is back (red triangle with exclamation)

---

### Post by Shpongle on 2009-12-23
see my above post , you haven't verified your sources ,

---

### Post by soryu on 2009-12-23
no valid openpgp data found??

---

### Post by Shpongle on 2009-12-23
> **soryu said:**
> no valid openpgp data found??

you need to save the pgp in a file  eg below for the deb opera one  and import that file , note i think you may need to call it whateverfilename.pgp so it recognizes [PHP]-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.1 (GNU/Linux)

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
=wGGg
-----END PGP PUBLIC KEY BLOCK-----[/PHP]

---

### Post by soryu on 2009-12-23
sorry,dont know how to do that.
can you explain?

---

### Post by oldsoundguy on 2009-12-23
or you can install Ubuntu Tweaks and let it do the work for you on many of those sites.

---

### Post by Shpongle on 2009-12-23
yea you basically save the whole key from start to finish in a textfile use gedit or something call it anything you want eg opera.pgp , then in software sources -> authentication import that file and it should work,

use this for opera 

wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -

but for the other one [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/Release.gpg) youll have to save this key ina text file and add it , ```
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iQCVAwUASzHfD+9Bhv4kdRC+AQLDxgP/dXoyGLtssWySyUFdwCvgUvW0K0duTeRg
wU1OTX4F5O8ooj5laHNld4Nje8VTcD/Wr18XCXIMXfI527PZj/1MXuwNYhx1Bx56
yvVPlJypO7Kb5X4RNRgN1HKrrpFt5aIYL/y+ZCeQglU0bDQ8apYhQTY2uESUROf3
nkiQNBU/up8=
=Grnd
-----END PGP SIGNATURE-----
```

---

### Post by soryu on 2009-12-23
finally got one. i just clicked on the opera link downloaded the key to desktop.
then imported it to the repository . i think it  worked
opera is not listed on the  failing to download repository index list anymore.

when i copied the whole key and saved it opera.pgp  and tried importing it to the repository list it said it was corrupted

thank you for the help. on to the next one on the list.

---

### Post by Shpongle on 2009-12-23
no problem glad one of them worked , you should get it workin dont worry , you could always try remove the corrupted source and go to the website and add it again and add the key saved as a text file  before it  refreshes the sources list and updates your sources.

---

### Post by Shpongle on 2009-12-23
actually before you try that save the mozilla daily builds key in a file called eg mozilla.key and try import it


if that doesnt work see here [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) , i think this is the original site where you added your source if so look for this ,

Signing key:
1024R/247510BE (What is this?)

and click the whats this and it will tell you what to do, make sure you select the correct distro version

---

### Post by soryu on 2009-12-23
i'm saving the key in gedit.
i renamed it mozillakey,mozillakeygpg ,mozillakeypgp. and other stuff when i try to import it
i get a message might not be a GPG key or corrupt.
 

save in text file.. is that  gedit or something else?


when i open file with  verify signature it says (key not in keyring)

---

### Post by Shpongle on 2009-12-23
> **soryu said:**
> i'm saving the key in gedit.
i renamed it mozillakey,mozillakeygpg ,mozillakeypgp. and other stuff when i try to import it
i get a message might not be a GPG key or corrupt.
 

save in text file.. is that  gedit or something else?


when i open file with  verify signature it says (key not in keyring)

it should be saved as whatever_name_you_wish.key the .key is the important bit , youre better off removing the corrupted sources and doing it again visiting the site and following the steps in the whats this link  , see the link to the page on my last post

---

### Post by soryu on 2009-12-23
thank you Dill all done.

firefox  is now shiretoko.
is that normal?

i checked new version of firefox or something like that.

---

### Post by Shpongle on 2009-12-23
no problem , glad I could help :-) , yea thats right theres different names for firefox releases.

---

