---
title: "Unable to use TOR at all"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Equity49 on 2009-01-11
Cannot use TOR.
Network times out on all attempts, and....I get this message:

Vidalia was unable to apply your Server settings to Tor.
Unacceptable option value: Servers must be able to freely connect to the rest of the Internet, so they must not set Reachable*Addresses or FascistFirewall.

How do I configure? I tried using relays and brides and everything else imaginable.

---

### Post by invenit on 2009-01-11
>Vidalia was unable to apply your Server settings to Tor.

I doubt if you can use Vidalia in linux since it is part of the Windows package for Tor. Check out the linux-centric suggestions at [https://www.torproject.org/download-unix.html.en](https://www.torproject.org/download-unix.html.en)

If you need the Vidalia features in linux then you need to install Tork for KDE. (Personally, I don't use Tor now since it just too slow.)

---

### Post by karlec on 2009-01-30
> **invenit said:**
> I doubt if you can use Vidalia in linux since it is part of the Windows package for Tor. 

That is actually inaccurate.  I was able to download the source code from the vidalia site compile it in Intrepid and have it working.

My only problem is that when I restart my box there seems to be some conflict as Tor starts automatically as a service and Vidalia cannot seem to handle that.  Perhaps I need for Tor not to start automatically and just start it from Vidalia.  Ideas??

Thanks

---

### Post by raysolomon on 2009-02-08
I am having a problem too.

I am unable to use tor on my Ubuntu Intrepid box since 3 weeks ago.

I used tor all the time and it stopped working after some recent OS updates.

---

### Post by invenit on 2009-05-17
> **karlec said:**
> That is actually inaccurate.  I was able to download the source code from the vidalia site compile it in Intrepid and have it working.


Wow! You are right. Check out [http://ubuntuforums.org/showthread.php?t=1136056&highlight=vidalia](http://ubuntuforums.org/showthread.php?t=1136056&highlight=vidalia) for a solution. I was able to get it working.

---

