---
title: "[SOLVED] Computer names and workgroups in UBUNTU"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by bilijoe on 2008-03-23
I have been having trouble with the association of computer names, and workgroups.  The worst case is with one computer where, in the screen where the association between a computer and its workgroup appears to be made, the "correct" association is shown, yet, when navigating through the "Network" system, from the "places" list, the computer itself is listed as if it were a network, along side the "Windows Network".  Select it, and it appears to be an empty "group".  Select  "Windows Network" and, even though there should be only one workgroup on my system, there is the one there is supposed to be, and then there is Microsoft's default workgroup, "MSHOME".  There is one (and only one) Windows computer, in the system.  But neither the computer in question, nor the computer on which I am viewing the information, have been touched by a Microsoft operating system, since having their HDDs wiped, using DOD approved methods for destroying computer data (and therefore any trace of all things "Microsoft").  However, the computer in question is associated with the MSHOME workgroup, while all other computers in the system are [correctly shown] associated with the other,and therefore only valid workgroup in my system.  There must be a file someplace, where individual computers (names) are associated with the network's various workgroups, which has [somehow] become corrupted, but which is not being appropriately edited when changes are made (which should [eventually] correct the error.  Can anyone tell me the name(s) of system files where I might look for an error that might confuse the system so?

---

### Post by Eiríkr on 2008-03-23
Hey there Bili Joe --

Your post is a bit confusing.  Here's what I see on my system, maybe it will sound familiar.  

In Nautilus, I click Go -> Network.  Here I see a network icon labeled "Windows Network", and (when things are working properly) the computer icons for the two machines in my workgroup.  Double-clicking Windows Network now shows me one network icon labeled "homelan" (my workgroup name).  Double-clicking this now shows me the two computer icons again.  Double-clicking either of these will show me the shares on that machine.  Double-clicking a share shows me a login prompt, with options to remember forever, forget right away, or remember until logout.  Does this sound at all right?

As far as what workgroup any Ubuntu machine might belong to, look in /etc/samba/smb.conf if that machine is also a Samba file server (look for the "workgroup = " line), and in System -> Shared Folders -> General Properties tab.  

Cheers,

Eiríkr

---

