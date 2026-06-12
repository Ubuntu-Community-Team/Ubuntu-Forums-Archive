---
title: "Easy Peasy Ubuntu Help!"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Chubby93 on 2009-10-03
Hi,

What do I do?

Where can I fix this?

Here are the pictures:

[URL="http://photobucket.com/ubuntuhelp"]

Thanks,

Mike

---

### Post by TransitMan on 2009-10-03
The first picture indicates that communication with the appropriate download server could not be made and/or the file name your were looking for is unavailable.
The second pic indicates unsigned or non-existing keys of authentication for whatever you're trying to install.
For the first, give the server some time and try again.
For the second, try and locate the authentication key from where-ever you're trying to get whatever program you're trying to install.

---

### Post by Chubby93 on 2009-10-04
> **TransitMan said:**
> The first picture indicates that communication with the appropriate download server could not be made and/or the file name your were looking for is unavailable.
The second pic indicates unsigned or non-existing keys of authentication for whatever you're trying to install.
For the first, give the server some time and try again.
For the second, try and locate the authentication key from where-ever you're trying to get whatever program you're trying to install.
can u please explain that in beginner language?

like what should i do???

how can i fix it

thank you

---

### Post by nhasian on 2009-10-04
the servers have been really slow the past two days due to the release of Ubuntu Karmic Beta.  They should be better by now.  TransitMan is right, in the 2nd picture its complaining because you dont have the authentication key installed.

go to:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

and grab the signing key.  for more info see:

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

NOTE:  This step is eliminated in Karmic Koala 9.10 as it will automatically download and install the key for you when you add a PPA.

---

### Post by Chubby93 on 2009-10-05
> **nhasian said:**
> the servers have been really slow the past two days due to the release of Ubuntu Karmic Beta.  They should be better by now.  TransitMan is right, in the 2nd picture its complaining because you dont have the authentication key installed.

go to:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

and grab the signing key.  for more info see:

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

NOTE:  This step is eliminated in Karmic Koala 9.10 as it will automatically download and install the key for you when you add a PPA.

I fixed it by installing 9.10 and removing the easy peasy part of it.

---

### Post by Sarai the Geek on 2009-10-05
> **nhasian said:**
> 
NOTE:  This step is eliminated in Karmic Koala 9.10 as it will automatically download and install the key for you when you add a PPA.

+1,000,000

I am so psyched about this. Lazy people everywhere unite!!

---

