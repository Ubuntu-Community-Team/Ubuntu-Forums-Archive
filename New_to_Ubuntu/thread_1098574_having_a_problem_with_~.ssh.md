---
title: "having a problem with ~/.ssh"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by bcoron on 2009-03-17
Hello, first time poster here, can't figure out a problem with my ~/.ssh. It seems that .ssh is a key file instead of a directory. In my shell I can't create the .ssh directory as it says file exists. Does my private key belong in my home directory, or ~/.ssh directory? I may be trying to put the key in the wrong place. OS-X has it in a .ssh directory below my home directory. Is this the same in Ubuntu?

---

### Post by Fijitotev on 2009-03-17
> **bcoron said:**
> Hello, first time poster here, can't figure out a problem with my ~/.ssh. It seems that .ssh is a key file instead of a directory. In my shell I can't create the .ssh directory as it says file exists. Does my private key belong in my home directory, or ~/.ssh directory? I may be trying to put the key in the wrong place. OS-X has it in a .ssh directory below my home directory. Is this the same in Ubuntu?
Hello. yes you are correct ~/.ssh should be a directory.
To fix it, just move your current .ssh out of the way and create thie directory

> mv ~/.ssh ~/someUnknownKey
> mkdir ~/.ssh
> chmod 0700 ~/.ssh

---

### Post by bcoron on 2009-03-18
Thanks so much. I didn't want to blow up my OS, so I thought I'd ask. I don't know how the .ssh file got there, but it appears to be a rsa public key or very short private key. At any rate it isn't mine.

Thanks again for your help!

---

