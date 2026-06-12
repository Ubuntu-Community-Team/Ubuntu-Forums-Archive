---
title: "Can't get rid of network proxy server address"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by triwave on 2006-11-21
Hi,

I'm new at this Linux thing and am having fun (so far) but my fun came to a halt this evening. I installed Ubuntu 6.06 after some trials and tribulations to what now looks like a working version. I configured a proxy server for internet connections and tested that out - worked great.

Now I have the laptop at home and have a direct connection to the internet. I  changed to direct connect both in Firefox Browser and in a utility called Network Proxy. 

Problem: When I try to get updates, new s/w or anything that seems to do with a repository I get unable to reach destination errors. The errors state that Linux is trying to reach these addresses through the old proxy address I had configured.

How do I get rid of that?? I doesn't want to go away....

Incidentally, by removing the proxy in Firefox I do get out to the internet OK so functionally I can get to the web, but the address for my repositories are wrong.

Help in simple terms is much appreciated, I'm still learning where to look, how to edit, etc. so take it slow  ....   ](*,)

---

### Post by triwave on 2006-11-22
Update: Took the laptop back to work and verified functionality through the internet proxy server. I was able to update/install new packages. I never changed the proxy settting! Under Network Proxy it says "Direct Connect to Internet" which doesn't work at my office.

Somewhere there is a lingering proxy address from the original installation that doesn't get changed - anybody know where that could be??

---

### Post by triwave on 2006-12-29
The mystery file the proxy is contained within is a part of "apt" itself. Thanks to Zigford who pointed this out. 

[http://ubuntuforums.org/showpost.php?p=1892747&postcount=10]("http://ubuntuforums.org/showpost.php?p=1892747&postcount=10")

Problem solved!

---

