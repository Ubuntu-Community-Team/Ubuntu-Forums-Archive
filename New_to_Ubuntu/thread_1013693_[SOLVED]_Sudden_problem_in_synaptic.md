---
title: "[SOLVED] Sudden problem in synaptic"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Andavane on 2008-12-17
For over a year I have used synaptic package manager -
typing in a word with "search" and then viewing the list of applications which may suit.

Suddenly I am drawing a blank: I usually see it performing the search, then the screen goes dark, and it comes up with a list.

Now suddenly when I click "search", nothing happens.

I was searching earlier for "pingus" and it came up with two files.
Deciding to do it later, I left it, but on trying again I get nothing
(and get nothing with other typed-in words as well).

Ideas?

Regards

John

---

### Post by Bucky Ball on 2008-12-17
What are the results of:

```
sudo apt-get update
```

in a terminal? Could you post them here please?

---

### Post by Andavane on 2008-12-17
Hi - I get this:

> andavane@vaayubuntu:~$ sudo apt-get update
[sudo] password for andavane: 
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy Release.gpg
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy/main Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy/restricted Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy/universe Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy/multiverse Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-updates Release.gpg
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-updates/main Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-updates/restricted Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-updates/universe Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-updates/multiverse Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-security Release.gpg
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-security/main Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-security/restricted Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-security/universe Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Err [http://ftp.hostrino.com](http://ftp.hostrino.com) hardy-security/multiverse Translation-en_GB
  Could not resolve ‘ftp.hostrino.com’
Reading package lists... Done
W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/Release.gpg](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/Release.gpg)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/main/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/restricted/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/universe/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/multiverse/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/Release.gpg](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/Release.gpg)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/main/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/Release.gpg](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/Release.gpg)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/main/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/universe/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Failed to fetch [http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2](http://ftp.hostrino.com/pub/ubuntu/archive/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘ftp.hostrino.com’

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
andavane@vaayubuntu:~$ 


---

### Post by Pconfig on 2008-12-17
You can try to set the "Download from" to "main server" in

System ==> Administration ==> Software sources

As it seems you can't resolve your server :)

---

### Post by Bucky Ball on 2008-12-17
Yep, as Pconfig mentions.

System->Administration->Software sources

again and you can change the mirror/server setting in there.

Or you could try:

[http://panjul.wordpress.com/2008/08/02/debian-ubuntu-source-list-update-package/](http://panjul.wordpress.com/2008/08/02/debian-ubuntu-source-list-update-package/)

and copy and paste that sources.list file into your own.

---

### Post by Andavane on 2008-12-17
> **Pconfig said:**
> You can try to set the "Download from" to "main server" in

System ==> Administration ==> Software sources

As it seems you can't resolve your server :)

A strange server indeed ! :rolleyes::rolleyes:

I selected "main" and got there¬

However with pingus I get this (bottom of post)

so assume this just means "try later" ?  ;)

regards

John

---

### Post by Bucky Ball on 2008-12-17
Nope, still the same problem. Run

sudo apt-get update

again and you should get the same result that can't resolve any server. There is a fix for this, but not finding it right now. Are you getting any error messages from other sudo commands? Try:

sudo blkid

(Don't post, just tell us if there's an error like 'can't resolve ... ):

---

### Post by Andavane on 2008-12-17
> **Bucky Ball said:**
> Nope, still the same problem. Run

sudo apt-get update

again and you should get the same result that can't resolve any server. There is a fix for this, but not finding it right now. Are you getting any error messages from other sudo commands? Try:

sudo blkid

(Don't post, just tell us if there's an error like 'can't resolve ... ):
Hi again - for
sudo apt-get update
I am now getting no errors

Just for interest for the sudo blkid I get

> andavane@vaayubuntu:~$ sudo blkid
/dev/sda1: UUID="89e3bb6c-1aae-4de7-b97b-7082ce34cf36" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="7e453884-b3cc-4826-80fe-76c8a391410d" 
/dev/sdb2: UUID="4800-2C85" TYPE="vfat" 
/dev/sdb5: UUID="4800-2DCD" TYPE="vfat" 
andavane@vaayubuntu:~$ 


which as far as I can see means that all is hunky dory... ;)

Will log in here again tomorrow

Regards

John

---

### Post by Bucky Ball on 2008-12-17
Excellent news. So that means you are having no more probs with Synaptic? If apt-get work for the update, then Synaptics should be happening, too because that is the same command it is using (Syn-apt-ics) behind the GUI.

Good luck with that and let us know how you go ... :)

If it is solved could you mark it as such from the 'Thread Tools' drop down menu, please?

Incidentally, if you are still having problems with Pingus, I suggest it might be in a repository that is not in your sources.list ... if it is not in Synaptics, it is not in any of your repositories. The 'sudo apt-get update' command you ran earlier may put it there though if you have another look. Or,

You could try downloading the .tar from here:

[http://pingus.seul.org/download.html](http://pingus.seul.org/download.html)

.. and then untar and install. And this page looks like the go for a repository and all things Pingus:

[http://savannah.nongnu.org/cvs/?group=pingus](http://savannah.nongnu.org/cvs/?group=pingus)

---

### Post by Andavane on 2008-12-18
Hi there:
Indeed, everything has gone fine now, and pingus is correctly installed.
I give these things a day or so before trying again, as I think the servers are a bit iffy here.
Additionally, have stored the extra info (offline); as there is currently no net for me at home, I think to pdf and take home to study later.

It's really good what you can learn here:
If only world leaders/politicians could a leaf out of ubuntu philosophy
(off course it takes two to tango - that's ubuntu too I believe! ;) )

Problem marked as solved  :guitar:

kind regards

john

---

