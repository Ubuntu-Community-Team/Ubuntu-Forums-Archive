---
title: "something wrong with the repos."
date: 2009-03-22
forum: New to Ubuntu
---

### Post by new Student on 2009-03-22
i have installed two keys for two repos.

and then i removed the repos from the list

now everytime i update the repos 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DBF1CA1622460E60
W: You may want to run apt-get update to correct these problems

how to fix this ?

thanx...

something else how to make ubuntu ignore printscreen key 
if it was pressed more than once ?

---

### Post by Locutus_of_Borg on 2009-03-22
> **new Student said:**
> i have installed two keys for two repos.

and then i removed the repos from the list

now everytime i update the repos 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DBF1CA1622460E60
**W: You may want to run apt-get update to correct these problems**

how to fix this ?

thanx...

something else how to make ubuntu ignore printscreen key 
if it was pressed more than once ?
read the bold line

---

### Post by new Student on 2009-03-22
> **Locutus_of_Borg said:**
> read the bold line

i updated the repos again and again and again 

but the same error appears 
tanx

---

### Post by egalvan on 2009-03-22
Are you running

```
apt-get update
```

or

```
**sudo** apt-get update
```

sudo should be included.

---

### Post by new Student on 2009-03-22
> **egalvan said:**
> Are you running

```
apt-get update
```

or

```
**sudo** apt-get update
```

sudo should be included.

i am running > sudo apt-get update


i have found this 


[http://siking.wordpress.com/2009/02/18/launchpadnet-ppa-changes/](http://siking.wordpress.com/2009/02/18/launchpadnet-ppa-changes/)

---

### Post by hyper_ch on 2009-03-22
you did not import the gpg key for that repo so it can't authenticate and you get the error. So

- import the gpg key
- ignore that error
- check in my tool whether that repo is also added (see my sig)

---

