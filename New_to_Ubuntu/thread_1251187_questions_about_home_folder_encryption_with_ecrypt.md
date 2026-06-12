---
title: "questions about home folder encryption with ecryptfs"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by dcccc on 2009-08-27
I encrypted my home folder during installation of ubuntu 9.04, when i logged in there was a message saying that I should write down my passphrase. So I wrote this in the terminal: 

$ ecryptfs-unwrap-passphrase ~/.encryptfs/wrapped-passphrase
Passphrase: [password i chose during install]
Warning: Using default salt value (undefined in ~/.ecryptfsrc)
[32 random numbers and small letters]
 

I suppose I should write the numbers and letters down but the warning message made me a little uncertain that I was doing it 100% right.


I also have a different question, is there any risk in updating my system when I have the home folder encrypted with ecryptfs? I have read that some people discourage updates when the system is encrypted since stuff could go wrong, but I don't know if it something to worry about in this case.

---

### Post by fela on 2009-08-27
All I can say is, yeah go for it (the updating) - **as long as you have your data backed up**. I mean if it's backed up you can't go wrong, apart from the hassle of getting all your data back from the backup disk.

---

### Post by dcccc on 2009-08-28
Yeah, that makes sense, thanks.



Could someone answer my first question, please?

---

### Post by mapes12 on 2009-08-28
I think the encryption stuff is leading you to change your password. Here's the bug report: [https://lists.launchpad.net/ecryptfs/msg00485.html](https://lists.launchpad.net/ecryptfs/msg00485.html)

If you encrypt all of /home would that not affect other user accounts?

Ubu already has a very strong encryption technology built in. From a normal install go to Application>Accessories>Password and Encryption keys to make yourself a key(s). Then right click any folder or file and select Encrypt. To open it the passphrase is then required.

The other way to keep your stuff safe and invisible is to change permissions. So for the account /home/username right click the username folder>Properties>Permissions tab and change the "Others" Folder Access to None. Then not even other users on the same machine will even be able to see your folders. Create another dummy user account to check it out yourself. Try doing that on windoze = no chance!

---

### Post by dcccc on 2009-08-28
> **mapes12 said:**
> I think the encryption stuff is leading you to change your password. Here's the bug report: [https://lists.launchpad.net/ecryptfs/msg00485.html](https://lists.launchpad.net/ecryptfs/msg00485.html)

If you encrypt all of /home would that not affect other user accounts?


The bug you refer to seems to be about changing password, which I didn't try to do. 

As far as I know the encryption I performed when I installed Ubuntu is only for the default user's home folder, that is the whole home folder is not encrypted, just the user's folder in the home folder (everywhere I have read about it is refered to as "home folder encryption", hence that's why I gave this thread this title). So if I were to create a new user it would not have it's folder encrypted, I think.

> **mapes12 said:**
> 
Ubu already has a very strong encryption technology built in. From a normal install go to Application>Accessories>Password and Encryption keys to make yourself a key(s). Then right click any folder or file and select Encrypt. To open it the passphrase is then required.

The other way to keep your stuff safe and invisible is to change permissions. So for the account /home/username right click the username folder>Properties>Permissions tab and change the "Others" Folder Access to None. Then not even other users on the same machine will even be able to see your folders. Create another dummy user account to check it out yourself. Try doing that on windoze = no chance!


The thing about the way I choose to encrypt my home folder is that it is very convenient since it will be decrypted when I log in and it is all setup during installation. That is why I did it since I'm new to Ubuntu, but sure, it can probably be arranged in the same or similar fashion after installation in serveral ways too.

But wouldn't changing permission have no effect if someone used rescue mode for example? (I have not tried myself so I don't know). I am using encryption in case the computer gets stolen (it's a laptop) not to keep my information from other users as I am the only one who will be using the computer. You did not know this of course, maybe I should have explained more in my first post, what I really wanted to know was about the warning message but thank you anyway.

---

### Post by bodhi.zazen on 2009-08-29
The "warning" message is fine, you did not specify a "salt" value and so one was generated for you.

[http://en.wikipedia.org/wiki/Salt_%28cryptography%29](http://en.wikipedia.org/wiki/Salt_%28cryptography%29)

As far as the "risks" of encrytped partitions - Take care to back up any data you do not wish to use. Although errors are rare, when they happen there is no way to recover.

In terms of "updates" you should be fine.

If, however, you mean upgrade by re-installing and keeping a separate encrypted /home partition you may have problems. Best thing to do is to go through the process of mounting your encrypted home partition on a live CD, that is the basic proceedure you would need to follow if you re-install.

Personally, IMO, it is easier to not use a separate /home with ecryptfs and simply back up your data and restore from backup if you perform a fresh install.

---

### Post by dcccc on 2009-08-29
> **bodhi.zazen said:**
> The "warning" message is fine, you did not specify a "salt" value and so one was generated for you.

[http://en.wikipedia.org/wiki/Salt_%28cryptography%29](http://en.wikipedia.org/wiki/Salt_%28cryptography%29)

As far as the "risks" of encrytped partitions - Take care to back up any data you do not wish to use. Although errors are rare, when they happen there is no way to recover.

In terms of "updates" you should be fine.


Thank you! That is good news, I will of course back up my data whether it is encrypted or not.

> **bodhi.zazen said:**
> 
If, however, you mean upgrade by re-installing and keeping a separate encrypted /home partition you may have problems. Best thing to do is to go through the process of mounting your encrypted home partition on a live CD, that is the basic proceedure you would need to follow if you re-install.

Personally, IMO, it is easier to not use a separate /home with ecryptfs and simply back up your data and restore from backup if you perform a fresh install.

I am not sure what you mean by "keeping a separate encrypted /home partition". But what I was going to do on my system was to have only the default user's /home encrypted, if I where to create another user (a guest user) it would not have it's /home encrypted.

And if I were to perform a major update such as from 9.04 to 9.10, or 9.10 to 10.04, I think I would use the method described in your last paragraph since it seems most straight forward, it's the way i "planned" (as in thought loosely of) from the beginning I guess.

---

### Post by bodhi.zazen on 2009-08-29
You should be good to go then (don't get confused if I used technical terms you do not understand, lol).

---

### Post by dcccc on 2009-08-29
Haha it's all right, thanks for your help.

---

