---
title: "How to revert back to an older version of NetworkManager"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by r3bol on 2009-05-11
Does anybody know where I can get a .deb of NetworkManager? I could only find one called [NetworkManager pptp]("http://packages.ubuntu.com/hardy/i386/network-manager-pptp/download"). Is this what I need?

If you were wondering, I can't use SPM or anything because I can't connect to the net with NetworkManager anymore ;)

Thanks.

---

### Post by tripolitan on 2009-05-11
What is SPM?

What makes you think that not being able to connect has anything to do with Network manager? Please be as detailed as possible.

Answering your question: You cannot, you should not. Just post your network specifications and someone will help you by-pass Network Mangler... 

sudo apt-get install network-manager

or, the hard way, assuming you are running Hardy Heron:

[http://packages.ubuntu.com/hardy-updates/net/network-manager](http://packages.ubuntu.com/hardy-updates/net/network-manager)

---

### Post by r3bol on 2009-05-11
Hi, The error is that NM is not detecting my 3G UTMS modem anymore [https://bugzilla.redhat.com/show_bug.cgi?id=494069](https://bugzilla.redhat.com/show_bug.cgi?id=494069) (sounds like it).

I can't use apt-get because I would need a net connection for that (unless there is something I missed) :P

SPM = Synaptic Package Manager

---

### Post by tripolitan on 2009-05-11
> I can't use apt-get because I would need a net connection for that (unless there is something I missed)

Use other computer and USB thumb drive...
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) pick the version, the package is under the Network category. Just out of curiosity, what version of Ubuntu were you using when your card worked?

---

### Post by Viva on 2009-05-11
I tried to do that, but couldn't because of the dependancy issues.

---

### Post by tripolitan on 2009-05-11
I know. My first answer was "You cannot, you should not." So, if you are the same person as the original poster:what version of Ubuntu were you using when your card worked? Also, is this a laptop or desktop?

---

### Post by r3bol on 2009-05-11
> **Viva said:**
> I tried to do that, but couldn't because of the dependancy issues.

Yeh, I got dependency issues too. I think some of the new ones were not compatable with the older version of NM. I'm gonna try and remove them and install the older versions and see if that works, but hey, don't try that until someone with more experience tells you the correct way to do it ;)
I have a feeling I'm digging myself into a hole I can't get out.

---

