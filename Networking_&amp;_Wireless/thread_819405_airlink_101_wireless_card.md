---
title: "airlink 101 wireless card"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by alillowr on 2008-06-05
I am having a hard time Getting wirless to work on 8.04 64bit.  My wireless card is an airlink101 awlh3028 and it uses the 8185 chipset.  I have scoured many many threads and tried numerous solutions without success.  I was thinking that means that I just dont understand something or am missing something along the way becuase many others have been helped.  The latest solution looked like it should work here is the link.  [http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy](http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy)

Im not sure where to start with the questions so here is my output when I enter in lshw -C network:

*-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32

I think that unclaimed means that it wasnt installed properly but I am not sure.  

What is my next step?

What info do I need to post here for help with my issue?

---

### Post by alillowr on 2008-06-05
Well I ended up solving the problem.  The thing that I missed was to install the build-essentials package.  Before I didnt have a way to connect to the internet at all so I ended up connecting my computer to a freinds wired so that I could get the package installed.  I redid all of the steps in the instal directions and waahlaah  it works.  So I give the solution a 2 thumbs up for good job and thanx.

---

### Post by RichardStabone on 2008-07-18
thanks for the follow up.

i ran into the same problem, and this is the first post i clicked on.

---

