---
title: "Torrents + Mobloquer"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by travmanx on 2009-11-15
Hello
I am finding trouble to understand what exactly Mobloquer does. From the Mac world, I use Peer Guardian(works perfect)... From what I can grasp on what they are doing, is it filters IP address that basically spam your computer with junk while on the internet. I have heard all good things about it when it comes to torrents. 
However, I currently have it running and downloading Kubuntu 9.1 for a buddy and I am getting extremely slow speeds. I know **tons** of people write they don't know how to open ports and getting slow speeds, blah blah blah. I already know how to do that and whatnot.
My problem is when I stop Mobloquer from blocking IP's I get WAY more download speeds (100% more)...
Is it doing more harm than good? Or am I just not using it right :\. 
Thanks for any help!
Travis

PS: Torrent Client - Transmission

---

### Post by Meskarune on 2009-11-15
You may want to contact the Mobloquer support team, wiki or devs as this program is not really ubuntu specific. The people that are part of the Mobloquer project will be more knowlegable about how to configure the program to your needs.

---

### Post by lovinglinux on 2009-11-16
> **travmanx said:**
> I am finding trouble to understand what exactly Mobloquer does. From the Mac world, I use Peer Guardian(works perfect)... From what I can grasp on what they are doing, is it filters IP address that basically spam your computer with junk while on the internet. I have heard all good things about it when it comes to torrents

Moblock does exactly what PeerGuardian does. It blocks IP addresses from a list of IP ranges, which are usually saved in PeerGuardian format (.p2p).

> **travmanx said:**
> My problem is when I stop Mobloquer from blocking IP's I get WAY more download speeds (100% more)...

That's probably because you are using too many blocklists and thus blocking too many IP addresses. Keep in mind that the most popular lists used by moblock and PeerGuradian are not perfect. The people who create those lists usually uses broader IP ranges to make sure the bad IP addresses are kept out, since IP addresses changes a lot. But this inevitably end up blocking legitimate IP addresses.

> **travmanx said:**
> Is it doing more harm than good? Or am I just not using it right :\.

Depends. For instance, if you just want to avoid downloading corrupted file pieces, then the [badpeers list](http://iblocklist.com/list.php?list=bt_templist) should be enough and should do more good than harm. You might get better speeds without it, but that doesn't necessarily means your download will finish sooner. For example, you might get too many corrupted torrent pieces from bad peers that would force your client to download them again, if you are not using that list.

Take a look at [iBlocklist](http://iblocklist.com) and choose the lists that fits your needs. Keep in mind that more lists are not necessarily better.

---

