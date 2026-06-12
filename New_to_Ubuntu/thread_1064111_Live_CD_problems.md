---
title: "Live CD problems"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Bruv on 2009-02-08
I am currently dual booting with XP and Kubuntu, but want to change to Ubuntu due to its wider usage, ease of use and better response time for problems on this site.

I have downloaded and burnt Ubuntu via K3b,it automatically checks the md5sum which was good, K3b takes over from then after clicking start.

When I boot with the disk, it gets past choosing language then just stops. The disk drive stops its activity, the cursor disappears and then nothing.
I have checked out whether the disk is good via that option and it says it is.

What can I do ?
Is it worth burning again, with another burner, or did I get something wrong somewhere ?

---

### Post by taurus on 2009-02-08
Try burning it at a slow speed like 4x.  However, why not just install the ubuntu-desktop package if you want to run Gnome instead of reinstalling?

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by theozzlives on 2009-02-08
> **taurus said:**
> Try burning it at a slow speed like 4x.  However, why not just install the ubuntu-desktop package if you want to run Gnome instead of reinstalling?

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

If you add GNOME you'll have both Kubuntu and Ubuntu, you just switch at the sign on screen.

---

### Post by Bruv on 2009-02-08
Wont that mean bloating the system ?

---

### Post by taurus on 2009-02-08
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Bruv on 2009-02-08
Many thanks.

Now all I need to know, how do I find out what distro I am using ?

---

### Post by taurus on 2009-02-08
I assume you meant release since you are using Ubuntu (or Kubuntu) distro.

```
lsb_release -a
```

---

### Post by Bruv on 2009-02-08
> **taurus said:**
> I assume you meant release since you are using Ubuntu (or Kubuntu) distro.



Yes I'm sorry.....I'm am a noobie.

Would I be correct in going for this [link]("http://www.psychocats.net/ubuntu/puregnomehardy"), with this output ?

bruv@MyComputor:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy

---

### Post by taurus on 2009-02-08
Yes.  You are running hardy so use the hardy method.

---

### Post by Bruv on 2009-02-08
All done.
I am very impressed,very,very impressed.

Not only with the depth of knowledge and assistance that is freely available on this site but the way Linux can be manipulated, if that is the correct word.

I had a hairy moment concerning screen resolution,but I tweaked the settings, rebooted and asked to repair, and everything was alright.

Now all I have to do is find my way around this new setup, the task bar at the top, for a start, oh well.

Many thanks for the assistance, much appreciated.
(No spell checker installed yet....forgive me)

---

