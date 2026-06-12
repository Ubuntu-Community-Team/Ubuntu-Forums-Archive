---
title: "Repository error"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by Nickjpost on 2011-04-22
Hello, 
I'm continually getting the following error message

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444

despite following the advise outlined in similar posts here, such as adding the key manuallly, I am unsuccessful. 

Please, any other suggestions would be a great help!

---

### Post by wojox on 2011-04-22
These two commands didn't work:

```
gpg --keyserver pgpkeys.mit.edu --recv-key  83FBA1751378B444
gpg -a --export 83FBA1751378B444 | sudo apt-key add -
```

---

### Post by Nickjpost on 2011-04-24
> **wojox said:**
> These two commands didn't work:

```
gpg --keyserver pgpkeys.mit.edu --recv-key  83FBA1751378B444
gpg -a --export 83FBA1751378B444 | sudo apt-key add -
```

No. I tried them again=fail

---

### Post by oldos2er on 2011-04-24
Can you post the terminal output from those commands? Just saying "fail" doesn't give enough info.

---

### Post by tgm4883 on 2011-04-24
Agreed, we need more info (output of those commands). All we can tell so far is that it is the Libreoffice PPA key.

I just ran them here, and they work. I'm assuming you are behind some sort of firewall which is blocking the download of the key. (I have a similar issue at work.)

I get around that by copying the PGP block from [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x83FBA1751378B444](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x83FBA1751378B444) into a text file, then adding they key via

```
apt-key add <FILENAME>
```

---

### Post by Nickjpost on 2011-05-07
> **tgm4883 said:**
> Agreed, we need more info (output of those commands). All we can tell so far is that it is the Libreoffice PPA key.

I just ran them here, and they work. I'm assuming you are behind some sort of firewall which is blocking the download of the key. (I have a similar issue at work.)

I get around that by copying the PGP block from [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x83FBA1751378B444](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x83FBA1751378B444) into a text file, then adding they key via

```
apt-key add <FILENAME>
```
I used the PGP block method and it worked!
Thank you!!!

---

