---
title: "Wireless connection problems since kernel upgrade w/ Xubuntu"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by too_many_people on 2006-08-17
Hi there.  I recently had a rather strange experience with my new(er) installation of Xubuntu and thought I'd drop by here to ask a question or two about it.
I installed xubuntu on my laptop (a compaq presario 1692) recently and, other than a few speed issues (which I expected), everything was working fine, including my netgear wg511t wireless pcmcia card.
Shortly after installing, I ran the software updating/patching program that came with the OS and it mentioned that a new kernel image (2.6.15.26, I believe) had come out, as of August 17th.  I thought the new kernel might fix the errors I was getting with my IDE driver (alim15x3).  While the new kernel did fix my IDE diver errors, it seems to have broken my network connection.  My card can recognize networks and supposedly connects to them, but it cannot negotiate an address.  When I re-run the live CD (containing the old kernel), I can connect and negotiate an address.
What happened?  I can't seem to find any information on an incompatibility between the new kernel and my card, but I don't see any other issue causing this.
Any help (or instructions on where to properly post this) would be greatly appreciated.

---

### Post by csevcik on 2006-09-24
I have the same problem with my HP Pavillion dv8275la under Kubuntu. The problem seems to be that the iwconfig eth1 key xxxxxxxxxxxxxxxx command does not work anymore, this is the output in my case

iwconfig eth1 key xxxxxxxxxxxxxxxxxxxxxxxxxxx
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Operation not supported.

(Key replaced on purpose)

Can anybody help?

Updating the kernel to 2.6.15-27-686 make things worse the wireless chips are not recognised at all!.

---

