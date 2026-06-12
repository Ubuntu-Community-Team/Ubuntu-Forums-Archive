---
title: "Nautilus-Elementary not installing?"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by darknomel on 2011-03-16
Hi all,

I know Nautilus-elementary is no longer being developed by I'd still like to use it.

I followed the guide from the developers blog here:

[http://ammonkey.posterous.com/the-right-way-to-install-nautilus-elementary]("http://ammonkey.posterous.com/the-right-way-to-install-nautilus-elementary")

However, as soon as I do sudo apt-get update, I get this error:

```
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4D17133CFC5D50C5
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E4010F076C2225A4

```

So when I do sudo apt-get dist-upgrade, it doesn't work and install nautilus-elementary.

I'm using 10.10 64 and I'm behind a proxy that I do have authentication for.

Has anyone got any tips for me on what I can check?

---

### Post by jtarin on 2011-03-16
Simply type the following commands, taking care to replace the number of the key that displayed in the error message: 
```
gpg --keyserver pgpkeys.mit.edu --recv-key  010908312D230C5F 
```
```
gpg -a --export 010908312D230C5F | sudo apt-key add -
```

---

### Post by darknomel on 2011-03-16
oops, stupid me, I typed the wrong thing! Will try again and post output.

Output:

```
michael@michael-ThinkPad-W510:~$ gpg --keyserver pgpkeys.mit.edu --recv-key  61E091672E206FF0
gpg: requesting key 2E206FF0 from hkp server pgpkeys.mit.edu
gpgkeys: key 61E091672E206FF0 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

```
michael@michael-ThinkPad-W510:~$ gpg --keyserver pgpkeys.mit.edu --recv-key  4D17133CFC5D50C5
gpg: requesting key FC5D50C5 from hkp server pgpkeys.mit.edu
gpgkeys: key 4D17133CFC5D50C5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

```
michael@michael-ThinkPad-W510:~$ gpg --keyserver pgpkeys.mit.edu --recv-key  E4010F076C2225A4
gpg: requesting key 6C2225A4 from hkp server pgpkeys.mit.edu
gpgkeys: key E4010F076C2225A4 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

This is the same for all the keys:

```
michael@michael-ThinkPad-W510:~$ gpg -a --export 61E091672E206FF0 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

```

What could be causing this?

---

### Post by jtarin on 2011-03-16
OOPS!! Try this command......replacing your key number```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 313D312748A22A95; gpg --export --armor 313D312748A22A95 | sudo apt-key add -
```

[The Nautilus Elementary team seems to be working on another file manger.]("https://launchpad.net/marlin")

---

### Post by darknomel on 2011-03-16
> **jtarin said:**
> OOPS!! Try this command......replacing your key number```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 313D312748A22A95; gpg --export --armor 313D312748A22A95 | sudo apt-key add -
```

[The Nautilus Elementary team seems to be working on another file manger.]("https://launchpad.net/marlin")

New error :)

> michael@michael-ThinkPad-W510:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 61E091672E206FF0
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 61E091672E206FF0
gpg: requesting key 2E206FF0 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


Connection refused? Where else do I need to set proxy settings?

---

### Post by jtarin on 2011-03-16
Repositories are like that. every repository issue I've had in the last 2 years has been remedied simply by waiting a day. 

There was once when I had to re-add mediubuntu, but other than that, they tend to work themselves out.

---

### Post by darknomel on 2011-03-16
I have an export http_proxy= in my .bashrc but I have a ! in my password, would that cause any issues?

---

### Post by gandaran on 2011-03-16
> **darknomel said:**
> I have an export http_proxy= in my .bashrc but I have a ! in my password, would that cause any issues?
see if this helps
[http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html](http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html)

---

### Post by darknomel on 2011-03-16
> **gandaran said:**
> see if this helps
[http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html](http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html)

That, outputs this: 

```
Trying to import all the missing keys
gpg: requesting key 2E206FF0 from hkp server keyserver.ubuntu.com
gpgkeys: key 61E091672E206FF0 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: requesting key FC5D50C5 from hkp server keyserver.ubuntu.com
gpgkeys: key 4D17133CFC5D50C5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpgkeys: key 531EE72F4C9D234C not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: requesting key 6C2225A4 from hkp server keyserver.ubuntu.com
gpgkeys: key E4010F076C2225A4 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

And I still get the key issues on apt-get update :(

---

### Post by gandaran on 2011-03-16
> **darknomel said:**
> That, outputs this: 

```
Trying to import all the missing keys
gpg: requesting key 2E206FF0 from hkp server keyserver.ubuntu.com
gpgkeys: key 61E091672E206FF0 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: requesting key FC5D50C5 from hkp server keyserver.ubuntu.com
gpgkeys: key 4D17133CFC5D50C5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpgkeys: key 531EE72F4C9D234C not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: requesting key 6C2225A4 from hkp server keyserver.ubuntu.com
gpgkeys: key E4010F076C2225A4 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

And I still get the key issues on apt-get update :(
did you try the modified Launchpad-Getkeys script for proxy users?

---

### Post by darknomel on 2011-03-16
> **gandaran said:**
> did you try the modified Launchpad-Getkeys script for proxy users?

Yes, that was the output from the modified script.

---

### Post by gandaran on 2011-03-16
then all I can do to help is recommend adding the key manually,
copy this [nautilus-elementary PPA key]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x61E091672E206FF0") file to gedit and save it on desktop then click on the import button in software sources authentication tab.
then try running the update command.
hope this fixes it.

---

### Post by seess on 2011-03-16
> **jtarin said:**
> Repositories are like that. every repository issue I've had in the last 2 years has been remedied simply by waiting a day. 

There was once when I had to re-add mediubuntu, but othe[r4](http://www.r4-buy.co.uk) than that, they tend to work themselves out.
Yes, You are right. I have similar opinion. I am working on it.

---

### Post by darknomel on 2011-03-16
> **gandaran said:**
> then all I can do to help is recommend adding the key manually,
copy this [nautilus-elementary PPA key]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x61E091672E206FF0") file to gedit and save it on desktop then click on the import button in software sources authentication tab.
then try running the update command.
hope this fixes it.

Could you kindly post that with code tags here? Even that site says network refused here.. :/ I don't think the proxy here is up to scratch.

---

### Post by gandaran on 2011-03-16
> **darknomel said:**
> Could you kindly post that with code tags here? Even that site says network refused here.. :/ I don't think the proxy here is up to scratch.
I was expecting that!
this key is just for nautilus-elementary PPA, I believe you still need two other keys.

---

### Post by Frogs Hair on 2011-03-16
I have had the  NE PPA for  along time and my sources seem to connect . Check out the Apt Key Manager in the in the software center or here is another method  . After the word keys leave a space and enter the key.  ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys (Missing Key)
```

---

### Post by darknomel on 2011-03-16
> **gandaran said:**
> I was expecting that!
this key is just for nautilus-elementary PPA, I believe you still need two other keys.

Seems like I only need this one still:

3B22AB97AF1CDFA9

Thanks so much for everyones help so far! Especially gandaran for pasting the key!

---

### Post by gandaran on 2011-03-16
> **darknomel said:**
> Seems like I only need this one still:

3B22AB97AF1CDFA9

Thanks so much for everyones help so far! Especially gandaran for pasting the key!
I will post the key but need to know for which PPA

---

### Post by Frogs Hair on 2011-03-16
```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
```

---

### Post by darknomel on 2011-03-17
> **gandaran said:**
> I will post the key but need to know for which PPA

It's for ubuntu-x-swat :)

---

### Post by gandaran on 2011-03-17
> **darknomel said:**
> It's for ubuntu-x-swat :)
got it!

---

### Post by darknomel on 2011-03-17
> **gandaran said:**
> got it!

Awesome, that's a lot dude!

---

