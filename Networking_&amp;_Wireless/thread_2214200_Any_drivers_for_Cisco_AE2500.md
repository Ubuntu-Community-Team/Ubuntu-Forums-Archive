---
title: "Any drivers for Cisco AE2500 ?"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by Shibblet on 2014-03-30
Just moved into a new location that will not allow me to use a direct connection to the router anymore, so I have to go Wireless.  Since my computer doesn't have any more open expansion slots, I purchased a Cisco (Linksys) AE2500 USB Wireless Adapter.

There is unfortunately no driver for this in Ubuntu, but there are directions out there showing how to use the NDIS Wrapper.  However, I am not able to get this to work for the 64-Bit version of Ubuntu... I've tried everything they're asking over and over and over and over... nothing.

Why is there no driver for this?  It's a pretty popular Wireless adapter.  Is there a .DEB out there for this device that I am missing?

---

### Post by Shibblet on 2014-04-02
Bump.

---

### Post by chili555 on 2014-04-02
Was this no help? [http://ubuntuforums.org/showthread.php?t=1805830&page=14&p=12954710#post12954710](http://ubuntuforums.org/showthread.php?t=1805830&page=14&p=12954710#post12954710)

---

### Post by Shibblet on 2014-04-10
> **chili555 said:**
> Was this no help? [http://ubuntuforums.org/showthread.php?t=1805830&page=14&p=12954710#post12954710](http://ubuntuforums.org/showthread.php?t=1805830&page=14&p=12954710#post12954710)

How am I supposed to download these things with no internet connection?

Make doesn't compile the ndiswrapper because Kubuntu doesn't have GCC installed by default.

I need internet access in order to download GCC in order to compile my ndiswrapper in order to get internet access.  Catch-22.

So I'll ask again... Why is there no .DEB driver for this device?  A lot of people have one.

---

### Post by chili555 on 2014-04-10
> **Shibblet said:**
> How am I supposed to download these things with no internet connection?If you can download them on another machine and transfer them on a USB, that's a poor option but it is possible. You'd also need linux-headers and build-essential and all their dependencies.

If you can visit a friend with an ethernet connection, you can get everything in two or three minutes. That's a better option. 

Finally, another option is to return that device, do some research here and find a fully supported plug and play device instead.

---

### Post by Shibblet on 2014-04-10
I can feel an argument about "why I even bother" with Ubuntu coming on.  It always seems to be something that just doesn't work... 

Ubuntu lives on the edge of absurdity.  Ubuntu is always ["Close, but No Cigar."]("https://www.youtube.com/watch?v=PtMU8nvZzOs")  If you follow the meaning.

It always seems that you have to jump through some hoop just to get something simple working... Either that or research the product you are going to buy before you buy it.  My problem is that I have a desktop that is mostly immovable.  I have access to a laptop that runs Windows, so I was able to download the XP Driver and ndiswrapper-1.59.tar.gz, but now I have a list of things to download, and really don't know what I am looking for.

Don't get me wrong chili555, I truly do appreciate your help.  I just don't like the solutions.  ;)

I just see the solutions as something that a lot of people would look at and say "I'm not going to fart around for hours trying to get this to work." or "I'm not buying a new wireless adapter just for this!"  When you order a piece of pie, and the waitress brings you a beautiful, delicious, mouth-watering slice of apple pie with no whip cream on it, you instinctively ask for whip cream.  Then the waitress brings you a can of heavy whipping cream, some sugar, and a pair of electric beaters.  Not really what you wanted... most people would say "Forget it."  and eat the pie without.

No offense, but ["Ain't nobody got time for that."]("https://www.youtube.com/watch?v=zGxwbhkDjZM")

---

### Post by chili555 on 2014-04-10
I harbor no illusions that Linux is all things to all people all the time. Neither do I believe that Windows or OSX is, either. If you want to have the debate (read: flame war) about Ubuntu and absurdity, then this is not the forum and I am not the missionary to whom to preach. Check here: [http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

My self-appointed role is to fix wireless and ethernet when and where I can or to offer my regrets and move on where I can't. If you'd like to proceed, I'll do my very best. If not, I certainly understand and you have my regrets. I respect the decision of anyone to make any choice that's best for them although it may differ from mine.

---

