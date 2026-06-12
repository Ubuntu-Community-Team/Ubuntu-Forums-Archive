---
title: "WinXP VmWare Network Share Access"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by mike.grabowski on 2007-07-04
Ok... I've been fighting with this for a little while now.  A few different posts and tutorials have helped me get part of my problem figured out.  But, I still have this one problem that I'm not having any luck with.

Here is the current situation.

I have a Ubuntu desktop.  The Ubuntu desktop has an installation of WinXP using VMware Server.  I also have a WinXP desktop machine.  I've been attempting to get my shares on each machine to show up across all three.  And I'm oh so close.

The Ubuntu desktop and the WinXP desktop can see each others shares as well as themselves.  This took me a little bit to get straightened out, but, I think I'm good there now.  My remaining problem lies with the VMware WinXP installation.  When I browse the Network, it can see and access the WinXP desktop as well as its own share.  But, it will not find the Ubuntu Samba shares.  I can't connect to them by IP or anything.  Although I can ping the machine.

My guess at this point is that its a WinXP issue.  I'm just wondering if anybody has any suggestions.

So, to recap.  Neither physical machine can see the VMware WinXP.  But the two physical machines can see each other.  The VMware WinXP can see the WinXP desktop.  The VMware WinXP network is set up in bridge mode.  Firewall is turned off.  I've gone through the network setup wizard multiple times to make sure I had everything set right there.  I'm using the Ubuntu machine as a WINS server.

Thanks for any help and suggestions.

Mike

---

### Post by steve457 on 2007-07-04
I'm actually having the exact same problem.  I just installed VMWare server on my Ubuntu machine, and am running Windows XP Pro in the virtual machine.  My XP Pro installation within the VM is unable to access the samba share on the Ubuntu box that it is running on.  All other XP machines are able to access the samba share fine.

---

### Post by Gallows on 2007-07-04
Sounds like a similar issue to [this]("http://ubuntuforums.org/showthread.php?t=482860") thread.  Check out [this]("http://www.vmware.com/community/thread.jspa?threadID=78606&tstart=0") on the VMWare community site they may be able to get some answers for you.

---

### Post by mike.grabowski on 2007-07-05
Thanks for the info/links.  I tried some of the suggestions from the other posts.  Changing to Host-Only networking allows me to access the Ubuntu Host Samba Shares.  But then, there are no other network connections or internet.  So, at this point, I can live with switching the network settings back and forth as I need to.  I don't really use the VM for a whole heck of a lot at this point.  One poster suggested using some Manual Routing Table Entries to correct all of this.  But, right now, thats a little over my head.  I'll read more on that some other time.

Thanks again for the help!

Mike

---

### Post by steve457 on 2007-07-10
I tried using the host-only mode, but still am unable to connect to the samba shares on my host machine.  I also want to try bouncing the requests off my router, as suggested in another thread, but am having problems figuring out how to type in the route commands.

Here are the commands that were suggested.

Here is the command for the host: 
route -p add guestIP mask 255.255.255.255 routerIP metric 20 

Here is the command for the guest: 
route -p add hostIP mask 255.255.255.255 routerIP metric 10 

I tried typing the command for the host on my Ubuntu machine, but it complained as the syntax does not seem to be correct.  Also, were would I type the command for the guest machine?  At the cmd prompt in windows?

---

### Post by steve457 on 2007-07-11
Figured it out.  The command that needs to be typed into the host, must look like this:

route -v add -net guestIP gw routerIP metric 20 netmask 255.255.255.255

I did that, and now am able to browse my ubuntu linux shares, as well as the rest of the network.

---

