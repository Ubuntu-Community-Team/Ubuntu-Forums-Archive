---
title: "Public Key not available for Medibuntu"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-11
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Is what the terminal said, after I cut & pasted from the 

[Medibuntu Community Documentation]("https://help.ubuntu.com/community/Medibuntu") page; viz:

sudo wget \
  --output-document=/etc/apt/sources.list.d/medibuntu.list \
  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list &&
sudo apt-get --quiet update &&
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get --quiet update

Now, is this just me? Or everybody?

and

How do I add the public key?

---

### Post by k3lt01 on 2009-12-11
Sometimes glitches happen. You have 2 options, you can try the terminal process again or you can go into Synaptic, type in medibuntu into the quick search, select medibuntu-keyring, click apply and go from there.

---

### Post by wojox on 2009-12-11
Use this:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by howefield on 2009-12-11
You'll can search for the key and get it from one of these servers...

[http://pgp.mit.edu/](http://pgp.mit.edu/)
keyserver.pgp.com

---

### Post by Mark_in_Hollywood on 2009-12-11
Wojox:

I tried your line of code. It ran and said:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Howefield:

After I get the key, what do I do with it? And is that link the only way to fix this?

(Developers -Why isn't this stuff more automated? -- or at least some explanation of what to do.)

---

### Post by mkvnmtr on 2009-12-11
It is automatic. Like the other poster said if you have enabled the medibuntu rapositories just click on the keyring and it will be installed. A hint look under origin and search in the medibuntu repositories.

---

### Post by sisco311 on 2009-12-11
> **Mark_in_Hollywood said:**
> Wojox:

I tried your line of code. It ran and said:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Howefield:

After I get the key, what do I do with it? And is that link the only way to fix this?

(Developers -Why isn't this stuff more automated? -- or at least some explanation of what to do.)

It should be automated, but in your case something went wrong.

Try:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783
```

[https://launchpad.net/+help/soyuz/ppa-sources-list.html]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

Or save the key in a file on your desktop (i.e. ~/Desktop/m.key)
and run:
```
sudo apt-key add ~/Desktop/m.key
```

link to the key: [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x2EBC26B60C5A2783]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x2EBC26B60C5A2783")

---

### Post by Mark_in_Hollywood on 2009-12-11
sisco311

The line:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783

and a sudo aptitude update seems to have fixed it. Thanks!



mkvnmtr

?

---

### Post by linxuser14 on 2010-04-22
> **k3lt01 said:**
> Sometimes glitches happen. You have 2 options, you can try the terminal process again or you can go into Synaptic, type in medibuntu into the quick search, select medibuntu-keyring, click apply and go from there.

 Through synaptic worked for me. Thanks for the info.

:guitar:

---

