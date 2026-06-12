---
title: "An error occurred"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Peterfc on 2009-02-04
I tried to chek for any updates and got a message that an error occurred.
It seems to be about Wine, i use wine for Adobe Photoshop. If someone can help thanks.

Second after getting help from a post how do you do THANKS.

Thanks for reading this post.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by iaculallad on 2009-02-04
Try reading this [thread]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304") from launchpad. It talks of the same problem.
HTH.

---

### Post by clive littlewood on 2009-02-04
Hi

Lots of people are getting this message as Launchpad have changed the security on some PPA's.

If you go to the Launchpad site you will find the correct public key and instructions to add this to your sources info.

The "thanks" and "solved" features are not currently available in the forums as they were causing some instability to the servers.

Hope this helps        :D

Clive

---

### Post by linux_tech on 2009-02-04
If there is a missing GPG key, then in the terminal type-

```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF 
```


```
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
```

This should add the key to the list.
(Repeat this for each missing key)

---

