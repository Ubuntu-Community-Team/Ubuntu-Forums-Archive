---
title: "Problem message when trying to update"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by Toubab on 2011-05-22
Although conversant with Windows, I am very new to Linux .. so please if anyone can help, write the instructions in a clear way as though you were talking to your 70 year old Grandmother !! :) Many thanks in advance.
 
When I try to update my Dell Inspiron Mini 10 Netbook Ubuntu 8.04 LTS system, I get this message:
 
Could not download all repository indexes
 
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
 
GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8Failed to fetch [http://ftp.debian.org/dists/etch/main/binary-lpia/Packages.gz](http://ftp.debian.org/dists/etch/main/binary-lpia/Packages.gz) 404 Not Found
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-lpia/Packages.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-lpia/Packages.gz) 404 Not Found
Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/binary-lpia/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-lpia/Packages.gz) 404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
 
How do I correct these errors please ?

---

### Post by oldos2er on 2011-05-22
If you go to the first link in the error msg, [http://deb.opera.com]("http://deb.opera.com/") , you will see instructions for Ubuntu users on how to add the key.

[http://ftp.debian.org/dists/etch]("http://ftp.debian.org/dists/etch/main/binary-lpia/Packages.gz") doesn't exist anymore. 

[http://deb.opera.com/opera/dists/stable/non-free/binary-lpia/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-lpia/Packages.gz) doesn't exist either; but  [http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz) does, so you might be able to replace that one.

Visit [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) for info on that repository.

If you post your sources.list I can help you edit it. ```
cat /etc/apt/sources.list
``` and also ```
ls /etc/apt/sources.list.d
``` Run these two commands and copy and paste all their output here.

---

### Post by Frogs Hair on 2011-05-22
Opera was updated to 11.11 a few days ago so make sure you latest version installed .

---

### Post by Toubab on 2011-05-22
Many thanks oldos2er .. for the linkks and for your generous offer of help.
editing.
 
I will look at those links and post the sources.list tomorrow .. as it is the early hours of the morning here in the UK.
 
Also thanks to you Frogs Hair .. Opera did notify me and attempted to update itself to 11.11 this evening, but the update failed with a message to the effect that the update was not compatible with my system. Yet another problem to deal with.
 
Again, I am grateful to you both for your help.

---

### Post by Toubab on 2011-05-25
Hi Oldos2er .. my apologies for the delay in getting back to you.

I followed your suggestion to go to [http://deb.opera.com]("http://deb.opera.com/") and using  their instructions, easily added that key. 

I then downloaded and saved _[http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz)_ BUT I don't know what to do with it.

Also I could not understand the information on the _[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)_ page at all. 

Remember please, that I am very new to using this system.

Here is the information you asked for:

Code   cat /etc/apt/sources.list

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb [http://ftp.debian.org](http://ftp.debian.org) etch main
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free


Code    ls /etc/apt/sources.list.d

dell-mini.list  dell-mini.list.save  opera.list  opera.list.save


Thank you again in advance for your invaluable help.

Cheers

Toubab

---

### Post by oldos2er on 2011-05-25
You need to edit your sources.list to remove the repositories that no longer exist. Run ```
gksu gedit /etc/apt/sources.list
``` and remove the lines 

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron" 

and

deb [http://ftp.debian.org]("http://ftp.debian.org/") etch main

Save your changes, exit the editor, and run ```
sudo apt-get update
```
If there are any more errors, please copy & paste them here.

Hardy's going to be reaching its end-of-life soon, so you may want to consider upgrading to 10.04.

---

### Post by Toubab on 2011-05-25
Very many thanks again .. I think it will take a long time for me to unravel what is actually going on with Linux, but I am determined to try to understand it :)

Just one more error is showing:

GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/binary-lpia/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I think this must be the file **packages.gz** which I downloaded and is saved on my desktop, of which I asked you last time "what should I do with it please" ?

Although the 'post update screen' shows"Your system is up to date" it also says that "The package information was last updated 226 days ago". What is wrong here please ?

Yes thank you for the advice, I did think that an update to 10.4 was advisable .. but I wanted to get this system running properly and then attempt an update .. hopefully with more understanding gained.

Cheers  Toubab

---

### Post by oldos2er on 2011-05-25
Oops, forgot that other error. You can fix the NO_PUBKEY error by running ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A2019EA84E7532C8
```
This downloads and installs the key for you. You'll need to run ```
sudo apt-get update
``` again.

---

### Post by Toubab on 2011-05-26
Hi Ann and Many Thanks Again,
 
I carried out your suggestions which appears to have solved the NO_PUBKEY error .. but now we have a new error message when attempting updates:
 
W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release) Unable to find expected entry non-free/binary-lpia/Packages in Meta-index file (malformed Release file?)
 
E: Some index files failed to download, they have been ignored, or old ones used instead.
 
... and that Update Manager message "Although the 'post update screen' shows"Your system is up to date" also saying that "The package information was last updated 226 days ago".. still shows and remains a mystery.
 
Sorry this is not as straight forward as I assume it should be !
 
Cheers Toubab

---

### Post by oldos2er on 2011-05-26
Yeah, binary-lpia doesn't exist in that file anymore, if you check the URL. Can you run this command and post the output? ```
ls /var/lib/apt/lists
```

---

### Post by Toubab on 2011-05-26
Thanks Ann,  here is the list:

 ls /var/lib/apt/lists

deb.opera.com_opera_dists_stable_Release
deb.opera.com_opera_dists_stable_Release.gpg
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_main_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_main_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_multiverse_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_multiverse_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_Release
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_Release.gpg
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_restricted_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_restricted_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_universe_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-dell-mini_universe_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy_main_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy_main_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy_multiverse_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy_multiverse_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_main_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_main_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_multiverse_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_multiverse_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_Release
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_Release.gpg
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_restricted_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_restricted_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_universe_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-netbook-base_universe_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy_Release
dell-mini.archive.canonical.com_ubuntu_dists_hardy_Release.gpg
dell-mini.archive.canonical.com_ubuntu_dists_hardy_restricted_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy_restricted_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_main_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_main_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_multiverse_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_multiverse_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_Release
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_Release.gpg
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_restricted_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_restricted_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_universe_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-security_universe_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy_universe_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy_universe_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_main_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_main_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_multiverse_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_multiverse_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_Release
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_Release.gpg
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_restricted_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_restricted_source_Sources
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_universe_binary-lpia_Packages
dell-mini.archive.canonical.com_ubuntu_dists_hardy-updates_universe_source_Sources
dell-mini.archive.canonical.com_updates_dists_hardy-dell-mini_public_binary-lpia_Packages
dell-mini.archive.canonical.com_updates_dists_hardy-dell-mini_public_source_Sources
dell-mini.archive.canonical.com_updates_dists_hardy-dell-mini_Release
dell-mini.archive.canonical.com_updates_dists_hardy-dell-mini_Release.gpg
lock
partial
wine.budgetdedicated.com_apt_dists_hardy_main_binary-lpia_Packages
wine.budgetdedicated.com_apt_dists_hardy_Release

Cheers  Toubab

---

### Post by oldos2er on 2011-05-26
Ok, now let's try moving that Release file somewhere out of the way, and hopefully getting the new one ```
sudo mv /var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release /tmp

sudo apt-get update
```

---

### Post by Toubab on 2011-05-26
No luck I'm afraid, I tried running your first command and received this message:

mv: cannot stat `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release': No such file or directory

Cheers  Toubab

---

### Post by oldos2er on 2011-05-27
That's odd. **ls** says it's there, but **mv** doesn't see it. Try **cd /var/lib/apt/lists** then **sudo mv deb.opera.com** and hit the Tab key. Let me know if it completes the file name deb.opera.com_opera_dists_stable_Release for you.

---

### Post by Toubab on 2011-05-27
Hi Ann,

Yes it does complete the file name deb.opera.com_opera_dists_stable_Release 
 
Cheers  Toubab

---

### Post by Toubab on 2011-05-31
So what should I try next Ann, please ?

---

### Post by oldos2er on 2011-05-31
Did you move it to /tmp? Then run **sudo apt-get update**

---

### Post by Toubab on 2011-05-31
No I hadn't re-tried moving it to temp .. please remember the codes and instructions are still a mystery to me and I am only following your instructions to the letter and not doing anything else ! :-)
 
So I have tried again, but sadly I get the same failure as before when running
sudo mv /var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release /tmp
 
receiving the same message:
mv: cannot stat `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release': No such file or directory
 
Sorry my netbook is being such a pain ! :(

---

### Post by Toubab on 2011-05-31
So .. being braver, I have read up on Outdated Package Information on the Net and have solved the message showing by unchecking [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free in the synaptic third party software list and then running update again.

Now I get no failure messages when attempting updates and my package information has updated itself and my system is showing as up to date. But although Opera 10.10 continues to work properly, The downloaded Opera_11.11.2109_i386.deb will not install .. giving a DPKG warning of an overriding problem because .. force enabled package architecture (i386) does not match system (lpia). 

OK, so I really do not know the reasons behind what I have done or if the original problem that you were helping with has been corrected. Perhaps you can explain in simple terms if I need to do anything else and how I will be able to update Opera to version 11 .. also whether an attempt at a system update to Linux 10.04, should be simple ( LOL ) and advisable.

Cheers  Toubab

---

