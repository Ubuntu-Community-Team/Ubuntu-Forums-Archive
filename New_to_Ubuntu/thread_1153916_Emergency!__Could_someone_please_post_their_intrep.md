---
title: "Emergency!  Could someone please post their intrepid source.lst"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by josephellengar on 2009-05-09
I did something abysmally stupid and switched to the jaunty repositories for a single package and now everything is screwed up.  Please help!?

---

### Post by taurus on 2009-05-09
Can you just edit your /etc/apt/sources.list and replace the word **jaunty** back to **intrepid**?

Save it and then run the update/upgrade again.

---

### Post by albinootje on 2009-05-09
> **idigchess said:**
> I did something abysmally stupid and switched to the jaunty repositories for a single package and now everything is screwed up.

Here's a list :
[https://answers.launchpad.net/ubuntu/+question/44045](https://answers.launchpad.net/ubuntu/+question/44045)

---

### Post by albinootje on 2009-05-09
And for a single package from a newer Ubuntu release you would use either apt-pinning or backporting.
See here :
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by 3rdalbum on 2009-05-09
System > Administration > Software Sources

Untick all the "third party" entries and tick all the regular Ubuntu repositories.

---

### Post by bodhi.zazen on 2009-05-09
> **albinootje said:**
> and for a single package from a newer ubuntu release you would use either apt-pinning or backporting.
See here :
[https://help.ubuntu.com/community/pinninghowto](https://help.ubuntu.com/community/pinninghowto)

+1 :)

---

### Post by josephellengar on 2009-05-09
thanks everybody, the errors were irreparable, but it gave me a good test of restoring with clonezilla, which I hadn't done before :)  now I'm trying to use the backports.

---

