---
title: "ltsp - nfs not responding on clients"
date: 2005-06-03
forum: Networking &amp; Wireless
---

### Post by plockery on 2005-06-03
I have a peer to peer windows network at home and want to move away from windows to linux. I am aiming to move to ubuntu on my main pc with ltsp and have the other pcs connecting to the main pc via etherboot floppy.

So far ubuntu hoary is installed on the main pc. So also ltsp 4.1.1 - no dramas.

Of the 4 client pcs - 3 have realtek 8029as nic cards or chips (different motherboards etc. but same nic/chip) and one has a 3com 10/100 fast etherlink nic.
In windows the three realtek pcs connect through the switch at 10MPS and the 3 com at 100MPS.

My problem is this.

When I boot any of the three realtek pcs I get exactly the same problem at the same point as follows:

Mounting the root filesystem /opt/ltsp/i386 on 192.168.1.5
Doing the pivot_root
nfs: server not responding   still trying...

And each pc just hangs and gets no further.

When I boot the 3 com pc there is no problem. It goes straight to the login screen and connects to the user's desktop without a hitch - with sound as well.

So I know all the services (dhcp3, nfs, tftpd, rpc.mountd) are all working and have checked that anyway.

So the problem seems to be with the realtek chip although for such a generic chip that seems very strange.

Alternatively I was wondering whether the speed at which the nics are connecting through the switch makes any difference? (I do not have any spare network cards at the moment to test this).

Does anyone have any idea what the problem with the realteks could be with nfs?
I am just wanted to see if anyone has any suggestions as to what I might try.

Peter

---

### Post by elvis on 2005-06-04
There was a realtek NIC specific issue a while back where high network loads spike CPU load and cause dropouts.  I had the same issue with large SMB copies dropping packets, and fixed it with a kernel upgrade.

Try using a different kernel on your lts clients, or using newer PXE images if you're PXE booting.  ltsp.org has a good guide on how to build lts client kernels.

Also, if you are using the 2.6 kernel on the new 4.1.1 ltsp, drop back to the 2.4 kernels instead.

---

### Post by plockery on 2005-06-04
Thanks for the reply.

I have seen some of the references to heavy loads and dropping out while trawling the net, but that cant be the case this time. There is no traffic at all!

Also in those cases from what I could see the nfs server does connect haphazardly whereas the problem i'm having is that it does not connect at all.

I've tried both the 2.6 and 2.4 kernels and the only difference is that the use of the 2.6 kernel gives me an extra error which reads:

nfs warning: mount version older than kernel.

With the 2.4 kernel this message does not appear. But it still does not connect.

I'm not keen to try and build a kernel - haven't done that before. But I am not sure what it is that I would be looking for. I would have thought that all recent linux kernels must have built in support for realtek 8029 cards unless they are now too old for the newer kernels.

Is it possible to just download an older kernel (from ltsp 3) and use it to see if the boot worked?
What issues might I encounter if I did that?

Peter

---

### Post by plockery on 2005-06-04
Just an addition.

I also downloaded and tried kernel 2.4.19-ltsp-1 which is the earliest debian kernel I could find on the ltsp site.

Gives exactly the same problem.

Peter

---

### Post by NigelBurman on 2005-06-15
I encountered the same problem running Suse 9.1 as my terminal server, but over a wireless link. 

I tried it a few times, each with the same result, but when I logged on to the terminal server (the terminal server was initially at the login kdm screen), suddenly everything started working. 

If I didn't use the wireless link, but instead connected via a 100Mbps switch, everything  worked fine.

I can only therefore put this down to a problem associated with bandwidth.

I'm not sure if this is helpful advice, but as you can buy 100Mbps network cards very cheaply (they don't have to be a named brand), you may find you're better off going this route.

---

