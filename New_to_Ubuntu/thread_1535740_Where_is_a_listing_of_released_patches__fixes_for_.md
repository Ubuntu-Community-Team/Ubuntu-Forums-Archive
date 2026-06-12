---
title: "Where is a listing of released patches / fixes for Lucid?"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by Rumpletumbler on 2010-07-21
When update manager tells me I have updates I'd like to be able to go somewhere and confirm that the updates are genuine at least to the extent that the names and file sizes match.

---

### Post by bprins on 2010-08-10
you don't trust the default ubuntu repositories?

---

### Post by Rumpletumbler on 2010-08-10
> **bprins said:**
> you don't trust the default ubuntu repositories?

I'd just like to check and see if the updates that are asking to be applied to my system match what's been released.

I've been just using [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn) for the security fixes. 

Thanks.

---

### Post by stlsaint on 2010-08-10
What is in the official ubuntu repos will more than likely NOT match was has been newly released by the website you are looking at. For instance:
If FF(firefox) version 1 was released when Ubuntu Lucid was released than FF1 is what lucid will be released with. Then two months later FF version 2 is released, you will need to manually upgrade your system to FF2. Thats just an example of how package managment works persay.

---

### Post by Rumpletumbler on 2010-08-10
So you just kind of have to take it on faith when Update Manager pops up I take it or either it'd be more trouble than it was worth.

Thanks.

---

### Post by Bachstelze on 2010-08-10
> **Rumpletumbler said:**
> I'd just like to check and see if the updates that are asking to be applied to my system match what's been released.

Where else could they come from? Unless you added third-party repositories to your system, if you see an update, it's because it has been "released".

---

### Post by Rumpletumbler on 2010-08-10
> **Bachstelze said:**
> Where else could they come from? Unless you added third-party repositories to your system, if you see an update, it's because it has been "released".

I have no idea, just trying to be safe. 

Thanks.

---

### Post by amauk on 2010-08-10
Packages in the repositories are digitally signed.

If anything is "off" with the package signing, you are notified

Packages that fail to authenticate will refuse to install

If you attempt to install unsigned packages (some third party sources distribute unsigned packages) you are warned that authentication is not possible

---

### Post by Rumpletumbler on 2010-08-10
> **amauk said:**
> Packages in the repositories are digitally signed.

If anything is "off" with the package signing, you are notified

Packages that fail to authenticate will refuse to install

If you attempt to install unsigned packages (some third party sources distribute unsigned packages) you are warned that authentication is not possible

Excuse my ignorance and thank you for your assistance. I'm new.

---

### Post by amauk on 2010-08-10
> **Rumpletumbler said:**
> Excuse my ignorance and thank you for your assistance. I'm new.no worries - it's a legitimate question

---

### Post by mikewhatever on 2010-08-10
Ubuntu has a tracker for its security updates:
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)
Of cause, that only covers security updates and not the recommended.

---

