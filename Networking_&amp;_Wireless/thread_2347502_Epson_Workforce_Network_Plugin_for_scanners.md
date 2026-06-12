---
title: "Epson Workforce Network Plugin for scanners"
date: 2016-12-26
forum: Networking &amp; Wireless
---

### Post by tony-buckley on 2016-12-26
I have an Epson WF-3520 multifunction that developed a problem with network scanning after the release of the 4.4... Linux kernels. There is a bug currently in 'triaged' state for this ([https://bugs.launchpad.net/bugs/1613027](https://bugs.launchpad.net/bugs/1613027)). I've spent countless hours narrowing down where the problem lies only to find that its a known issue ([https://patchwork.ozlabs.org/patch/618164/](https://patchwork.ozlabs.org/patch/618164/)) which basically says that failing applications will have to be fixed rather than the kernel code line changed.
The problem for me is that epson network plugin (iscan-network-net) almost certainly calls the socket 'listen' function with a backlog argument or default of zero, which now causes it to fail. I can't find any source code for this plugin nor can I find anything to do with its origins or who may be contacted about it.

I'd be delighted if anyone has any insight regarding the plugin or how to get it fixed. Epson support have been no help at all.

BTW. If anyone is experiencing this problem, I've contrived a workaround here: [https://github.com/mr-headwind/ListenOverride](https://github.com/mr-headwind/ListenOverride)

Thanks.
Tony

---

