---
title: "Unable to create  a new PGP key"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by telovin on 2011-04-11
Hi All,
I am unable to create a new openPGPKey. I go to system-preferences-passwords and encryption keys-file-new-PGPKey-enter my name, email id, comment, select my advanced key options, but the create button is still grayed out. I am unable to click on create and proceed further. Under my personal keys, I can't find any keys. I searched for posts for this problem. Went through the help document again and again, but unable to find a solution. I am using Natty.

Under my personal key, I cant see anything. There is no keys listed there

When I try synching one of my user accounts with servers, I get the following error
Couldn't retrieve keys from server: keyserver.ubuntu.com:11371
"Invalid key data (missing UIDs). This may be due to a computer with a date set in the future or a missing self-signature."

---

### Post by telovin on 2011-04-11
Hello everyone,
I googled for it and found the answer. Before doing the above steps
Guess we have to type the command
```
gpg --gen-key --enable-dsa2
```
and follow the procedure. Hope it will be of use for anyone who is trying to create an openPGPkey.

---

### Post by isa.dsouza on 2012-09-19
This helped. But still had a load of trouble signing the code of conduct. Encryted file was a problem so I installed Thunderbird and enigmail addon to decrypt the email link that gets sent to activate the PGP for Launchpad. 

Now I have some other issues to sort out. Hopefully I should sort them out. Bottomline is I have signed the code of conduct finally. Other matters now regarding the Passphrase & Keyrings etc need to be sorted.

---

