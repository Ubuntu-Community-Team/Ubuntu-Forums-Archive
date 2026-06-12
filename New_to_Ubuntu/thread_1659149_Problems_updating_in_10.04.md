---
title: "Problems updating in 10.04"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by djyoung4 on 2011-01-03
So I keep trying to update but everytime I do the pop-up in the attached screenshot shows up.  Then I click close and then check for updates and I get an error saying "could not download all repository indexes" and this in the box
```
GPG error: http://linux.dropbox.com karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912EGPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061GPG error: http://deb.playonlinux.com lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/dists/lucid/Release  Unable to find expected entry  deb-src/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found
Failed to fetch http://archive.ubuntu.com/dists/YOURDIST/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch http://archive.ubuntu.com/dists/YOURDIST/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.30 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```
if I click close on that box it goes back to the partial upgrade popup.  I haven't tried to update recently or anything like that.  any suggestions?

---

### Post by drs305 on 2011-01-03
You have some problems with your repository lists.

Open Synaptic and go to Settings, Repositories.

In the third party tab, look for linux.dropbox entry and untick it. It's for karmic so you may even want to remove it, but for now, just untick it.

Next find the skype entry. I don't know why that is not working but you don't need it at the moment, so untick it as well.

The last two are more important but also corrupted:
> Failed to fetch [http://archive.ubuntu.com/dists/YOURDIST/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/YOURDIST/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/dists/YOURDIST/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/YOURDIST/universe/binary-amd64/Packages.gz)  

The "YOURDIST" shouldn't be there. If these are listed in the third party tab just untick them as they are incorrect.
Take a look at the Ubuntu Software tab. If you see a "main" and "universe" enabled there, go back and remove the ones in Third Party. If the ones in Ubuntu Software aren't currently selected, select them. It might help to deselect and then reselect them.

After making the changes, press the RELOAD icon and see if it runs without errors.

---

### Post by djyoung4 on 2011-01-03
> **drs305 said:**
> You have some problems with your repository lists.

Open Synaptic and go to Settings, Repositories.

In the third party tab, look for linux.dropbox entry and untick it. It's for karmic so you may even want to remove it, but for now, just untick it.

Next find the skype entry. I don't know why that is not working but you don't need it at the moment, so untick it as well.

The last two are more important but also corrupted:


The "YOURDIST" shouldn't be there. If these are listed in the third party tab just untick them as they are incorrect.
Take a look at the Ubuntu Software tab. If you see a "main" and "universe" enabled there, go back and remove the ones in Third Party. If the ones in Ubuntu Software aren't currently selected, select them. It might help to deselect and then reselect them.

After making the changes, press the RELOAD icon and see if it runs without errors.
now i get this:
```
GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061GPG error: http://deb.playonlinux.com lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/dists/lucid/Release  Unable to find expected entry  deb-src/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by drs305 on 2011-01-03
The ones you fixed aren't showing up as errors any longer but I didn't scroll far enough right to see the others. Some are missing the public key, which you can add with this command:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FAC5991 9D1A0061 C4676186  0C5A2783

```

This leaves one more (if I didn't miss any). Back in the third party tab, disable or remove the jre-phoenix launchpad entry.

---

### Post by djyoung4 on 2011-01-03
> **drs305 said:**
> The ones you fixed aren't showing up as errors any longer but I didn't scroll far enough right to see the others. Some are missing the public key, which you can add with this command:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7FAC5991 9D1A0061 C4676186  0C5A2783

```

This leaves one more (if I didn't miss any). Back in the third party tab, disable or remove the jre-phoenix launchpad entry.
ok i did that but I still get the popup that says i can do a partial update and it still won't let me upgrade

---

### Post by drs305 on 2011-01-03
> **djyoung4 said:**
> ok i did that but I still get the popup that says i can do a partial update and it still won't let me upgrade

There are various reasons why it might say only a partial upgrade is available. A common one is that some packages have been updated but not all the dependencies have been updated as yet. Sometimes it takes a few days to get all the dependencies updated. 

A partial update may work, but it can also break your system and is generally not recommended. 

If you provide us what type of update you are trying to accomplish we may be able to provide some more insight. If it's just a regular update within the same release, give it a few days and hopefully the 'partial update' message will go away. Another option would be to change servers on the Ubuntu Software tab of Synaptic or Software Sources.  Click on the 'download from' and try a different server. Some servers are updated earlier than others...

---

