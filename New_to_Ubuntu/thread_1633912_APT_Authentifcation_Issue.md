---
title: "APT Authentifcation Issue"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by ericstrom on 2010-11-29
Getting the following messages when the update manager runs. Any suggestions how to fix it ? I am running Lucid with DropBox. 

Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release](http://linux.dropbox.com/ubuntu/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by olalonde on 2010-11-30
Got the same problem. I also asked advice over at [http://askubuntu.com/questions/15484/error-caused-by-dropbox-in-update-manager](http://askubuntu.com/questions/15484/error-caused-by-dropbox-in-update-manager)

---

### Post by tajiknomi on 2010-11-30
[SIZE=2]Try this..> Go to >System>admin>software-sources >Repositories >& Un-check [/SIZE] [http://linux.dropbox.com/ubuntu/dists/lucid/Release](http://linux.dropbox.com/ubuntu/dists/lucid/Release)

then type "[SIZE=2]sudo apt-get update[/SIZE]"

---

### Post by ericstrom on 2010-11-30
tajiknomi recommended that I uncheck the following in my repository list:
 
[http://linux.dropbox.com/ubuntu/dists/lucid/Release](http://linux.dropbox.com/ubuntu/dists/lucid/Release)

However, when I look at the repository list per the instructions, I do not see the above line. In other words, it is not available to uncheck. The only line I see in the repository list that refers to dropbox is as follows:

[http://linux.dropbox.com/ubuntu/lucid](http://linux.dropbox.com/ubuntu/lucid) main

So it appears something is out of synchronization. What do you recommend ?

---

### Post by oldos2er on 2010-11-30
> **ericstrom said:**
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 

It looks like linux.dropbox.com is down; but you can get the gpg key with ```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
```

---

### Post by tajiknomi on 2010-12-01
> **oldos2er said:**
> It looks like linux.dropbox.com is down; but you can get the gpg key with ```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
```


[SIZE=2]Can you *explain* a little bit , i means the *code* which you had posted i-e "***5044912E***"...?[/SIZE]

---

### Post by oldos2er on 2010-12-01
That is Dropbox's key. I copied it from [https://www.dropbox.com/downloading](https://www.dropbox.com/downloading)

---

### Post by jmagsho on 2010-12-02
> **oldos2er said:**
> That is Dropbox's key. I copied it from [https://www.dropbox.com/downloading](https://www.dropbox.com/downloading)

Ann, just want to say thanks for the solution.  Much appreciated.

---

### Post by oldos2er on 2010-12-02
You're welcome.

---

### Post by Shellbak3 on 2010-12-16
10.10 64 bit
I followed the instructions above, JIC, but I'm still getting the error below.


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

