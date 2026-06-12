---
title: "Help please - Failed to fetch - ubuntu 10.10"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by luckylucky on 2010-11-12
More fun... anyone know how to fix this?

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by luckylucky on 2010-11-12
Is there no solution to this?

---

### Post by bryangwilliam on 2010-11-12
Perhaps try looking at [this]("http://www.linuxquestions.org/questions/linux-newbie-8/apt-get-install-command-is-not-able-to-fetch-packages-from-ubuntu-repositary-806674/") post:

Not sure if it is exactly the same thing, but looks like it could be related.

---

### Post by sandyd on 2010-11-12
> **luckylucky said:**
> More fun... anyone know how to fix this?

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.


```you need to setup a DNS server
check out [http://openubuntu.com/index.php/topic,230.0.html](http://openubuntu.com/index.php/topic,230.0.html)

---

### Post by luckylucky on 2010-11-12
Ironically, the solution works for some, but not for everyone.  I tried to implement it by changing my networking to the alternate dns servers.  I tried a couple servers and also google's.

Basically followed post #23 of
[http://ubuntuforums.org/showthread.php?t=1475399&page=2](http://ubuntuforums.org/showthread.php?t=1475399&page=2)

Still didn't work for me.

Anyone have another good idea?  Thanks for any suggestions.

---

### Post by babydrivers on 2010-11-21
having the exact same issue. i've been trying to set up internet for my  ubuntu operating system because (as i've recently come to discover)  ubuntu doesn't like broadcom wireless cards. it also doesn't seem to  like hp pavillion so you have to work around that with some kind of  ndiswrapper command. 

anyhow, i fixed some of the problem (not  the internet connection though)  by terminal by deleting a malformed row  in the sources list. so now the update manager seems to actually open  up for me.BUT when i tried to force an update (i found the update for  broadcom configuration and network card in the list of updates) it tells  me the same thing you just wrote out. actualy i think it's a bit  different but here it is:


```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W:  Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2   Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Could not resolve 'archive.canonical.com'

W:  Failed to fetch  http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2   Could not resolve 'archive.canonical.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W:  Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2   Could not resolve 'security.ubuntu.com'

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2   Could not resolve 'security.ubuntu.com'

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2   Could not resolve 'security.ubuntu.com'

W: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2   Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/maverick/dists/main/Release.gpg  Could not resolve 'archive.ubuntu.com'

W:  Failed to fetch  http://archive.ubuntu.com/ubuntu/maverick/dists/main/restricted/i18n/Translation-en_US.bz2   Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.


```i  was told by others that i would need to go online to those listed  addresses and download the update files and then store them in the  ubuntu folder and access them through remote host file when logged into  unbuntu. then it is supposed to ask for your password and it will renew  the updates. 
the problem is that a lot of those addresses are no  longer valid. a lot of the files are stored in different folders now and  the maverick address doesn't even exist anymore. 
for instance-
 [HTML]http://archive.ubuntu.com/ubuntu/maverick/dists/main/restricted/i18n/Translation-en_US.bz2 [/HTML]doesn't  exist there but if you go onto ubuntu you will find a place to download  updates from maverick but they aren't the actual updates, they are the  updates to the programs. that means you would have to click  on every  since program/appliciation separately and yeah....it would be a huge  mess. 

i'm not gonna lie, i'm not an expert on this kind of  stuff. i only recently started using windows  xp after being spoiled by  the world of apple mac before my lap died after 6 years of faithful  service. what i miss most about apple- terminal easily appeared right  before your eyes.  you could download python and perl easily. you could  download applications Fugu for ssh.  if you moved a file out of a system  folder and forgot where to put it back it wouldn't completly destroy  your computer. all you would have to do is reboot and it would magically  restore the file and move it back to where it should be. where you  could easily use disk utility or get into single user mode and run a  fsck repair. the keys didn't make the annoying clicky clicky sound  everytime you pressed the keyboard. oh how i miss those days. and let's  not even get started on how hard it is to setup or get connected to an  internet network on windows. nor shall i get into how hard it is to  simply search for a file in the library. 

anyhow, if anyone ever  finds a solution to this problem with ubuntu and the wireless internet  card for hps and all those using a broadcom cards. please let us  know!  if i figure it out i'll let you all know.

---

### Post by babydrivers on 2010-11-21
okay well i found out a couple things that might help.

a couple of the addresses trying to be fetced are incorrect.
 here are some corrected archive directory addresses

[HTML]http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/

http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/[/HTML]

but you can't just go directly to the file in the directory because it is no longer called "Translation-en_US.bz2"

the new ones are



[Translation-en_CA.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_CA.bz2")
[Translation-en_GB.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2")

[SIZE=1][Translation-en_AU.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_AU.bz2")[/SIZE][SIZE=1]

[/SIZE]

---

### Post by wobbe on 2010-12-14
This fixed it for me on linux mint 10

[http://ubuntuforums.org/showpost.php?p=9397572&postcount=23](http://ubuntuforums.org/showpost.php?p=9397572&postcount=23)

---

### Post by felixzilla on 2011-11-01
try and stop some servers running on your machine, in my case i had to stop ssh server with "sudo /etc/init.d/ssh stop"

---

### Post by oldos2er on 2011-11-01
Closed, please don't bump old threads.

---

