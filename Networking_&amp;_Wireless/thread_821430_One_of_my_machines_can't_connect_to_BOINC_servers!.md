---
title: "One of my machines can't connect to BOINC servers?!"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by infinitejones on 2008-06-07
This is weird. I have three machines on a network, connected to the internet via a router, all with Hardy Heron installed. All three run BOINC and I noticed two days ago that one of them had a lot of completed units (for more than one project) backed up - completed but not uploaded.

This sometimes happens when the relevant BOINC servers are down so I left it until tonight but still no change. However - the other two machines seem to be uploading and downloading units with no problem.

So from the machine that's not uploading I tried logging onto the relevant BOINC sites to see if there's a problem, and Firefox gives me a Page Load Error ("Though the site seems valid, the browser was unable to establish a connection.")

The weird bit is this - from the other two machines, all the sites load perfectly. Also - and this is even weirder - the machine that can't access the BOINC websites **can access any other website**. I'm submitting this post from that machine, but I can't get onto setiathome.berkeley.edu (or berkeley.edu), boinc.bakerlab.org (or bakerlab.org), milkyway.cs.rpi.edu (or rpi.edu), or climateprediction.net - to name a few. Every other website/server I try is fine, but anything related to BOINC gives a page load error.

I can't think of anything different about the non-connecting machine compared to the other two - I certainly haven't changed anything since the time it was last working. It doesn't have a firewall and there's nothing in the router that makes it any different from the other two machines. It can't be a DNS issue because all three machines resolve via the router, which uses OpenDNS (plus the other two machines can resolve with no problem.) All using the same version of Firefox. The non-connecting machine can't even ping the BOINC sites (100% package loss - it can't even resolve the hostname) but it can ping any other just fine.

Any ideas?!

---

### Post by infinitejones on 2008-06-08
Any ideas on this one?

---

