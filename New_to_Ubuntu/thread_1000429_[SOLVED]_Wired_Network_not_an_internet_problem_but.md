---
title: "[SOLVED] Wired Network not an internet problem but LAN"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Kellemora on 2008-12-02
Hi Gang

I have 8 computer 6 are Ubuntu, 2 are Doze XP.

Hardwired LAN that works fine except;

7 of the machines can see each other, including the 8th machine which works fine as far as the other machines are concerned.

If I go to Places Network no shares are shown 80% of the day.  In other words, all shares are showing for awhile, then they disappear.
I used to be able to get them back again by triple booting the computer.

However, that is no longer working on this machine!
The smb.conf file is identical to the smb.conf on the other 6 Ubuntu machines, and does work sometimes.

I can go to Places Network and click GO/Location and type in the IP for each machine and can bring up and mount each shared folder no problem, so the Ethernet is working just fine in that regard.
I can access all the files and folders doing it manually this way.
However, some other features we use do not work IF Places Network does not show the shares and no way to bring up those features manually.
EG:  Interoffice communications are DOWN when Places Network is not functioning.

We had one stubborn machine doing this last month too, which prompted a minor change to the smb.conf file that we made universal on all the machines.  And have not had any problems, EXCEPT each time we get an UPGRADE then the whole LAN goes down until we reboot each Ubuntu machine 3 times.  Then all works fine again until the next Update.

This is our MAIN file server and needs to be able to SEE the other computers automatically, not loading each file folder separately.

I've been asking about this problem now for over 3 months and find others have been having the same issue now for over two years and it's still unresolved.

Ubuntu is totally useless if it cannot be fixed to work properly!
I'm tired of working from 7AM until Midnight every day and burning up my weekends trying to keep the STABLE version of UBUNTU running properly.

If a simple wired LAN cannot work on Ubuntu Hardy My ONLY alternative is to dump Ubuntu and go back to something more reliable like CentOS (RedHat) or gasp Winders!

I've even dumped Network Manager for Wicd, but the problem is NOT with the LAN it's with Ubuntu or Samba.  But Samba works just fine on CentOS, so that obviously leaves Ubuntu as the problem child!

Looking for answers!

TTUL
Gary

---

### Post by taseedorf on 2008-12-10
Wow, I have the exact same problem except with only 3 computers.  

For me, it has something to do with wireless connections, I believe, but you said your boxes are all hardwired?

Hmm..are you using a dhcp server to distribute static IP addresses? or whatever is available?? try setting it up so each box gets an ip address based on its mac addy.


Make sure that if you are allowing SMB through local firewall that it is ALWAYS allowing this and that ALL local connections can accept... not just certain portions of the day.  On my router, I can allow smb only in the evening, etc...and when I only allowed certain computers on the network to access samba it got fussy...grrr....

also, what ubuntu are you using?
server?
hope so.

---

### Post by Peter09 on 2008-12-10
Could it be this bug?

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/244411)

---

### Post by Kellemora on 2008-12-10
Hi Tas

In my case it's NOT that I can't get to the shares, there are all there and accessible MANUALLY.  I can read and write to all the shares MANUALLY.  Whether they appear or don't appear in Places/Network.

However, during the times they don't appear in Places/Network, any automatic function will not work.  EG rsync folderA computerB to folderD computerC.  For months I thought it was something I was entering wrong in rsync.  Only to find it works sometimes, sometimes it don't.  I finally associated the times it worked right was when Places/Network WAS in fact showing the shares.  When they did not appear in Places/Network automatically, then no scripts would work either.

Auto-mount shares from fstab does not normally work since files are all over the place until we get a decent file server up and running again.  That's another project I'm currently working on.

TTUL
Gary

---

### Post by Kellemora on 2008-12-10
Hi Peter

I believe this bug is a PART of our problems, except for the fact we CAN access all shares and mount them using Places/Network/Go/Location and type in the IP address to bring up the machine, then click on the shared folders and they all mount just like they are supposed to do.

Interestingly, the 2 Doze machines see the shares just fine, whether or not they appear in Places/Network.

The weird thing is, every time there is an update the entire LAN drops out until we reboot.  Except between Doze machines, but they cannot see Ubuntu machines until we reboot.  Then depending upon the mood Ubuntu is in, I either have to manually load all the shares one at a time on each computer, OR Places/Network will decide to work for awhile and I can quickly mount everything by clicking on them there.

Just weird!  And very time consuming too, when they don't come up as expected.
I've more or less quit blaming it on Samba, because we do not have that problem in CentOs (Red Hat) and that machine is set up basically the same way as far as Samba and smb.conf are concerned.  But I rarely use CentOS for much of anything these days since discovering Ubuntu and how much better it performs on nearly everything else other than networking.

TTUL
Gary

---

### Post by Peter09 on 2008-12-10
You appear to have a 'name resolution' problem. That is, the IP address correctly identifies and can connect to the machine, however you cannot do this via name. The main package for windows name resolution is winbind. 

Is that installed and configured correctly?

---

### Post by Kellemora on 2008-12-10
Hi Peter

I know winbind is installed, but have no idea how to configure it, nor that I even need it.

The reason I say that is because, take today for example, all of my shares show up in Places/Network, just like they are supposed to.

WHEN shares show up in Places/Network, THEN wbinfo -u and wbinfo -g, etc. all show accurate info.  BUT when shares don't show up in Places/Network, then wbinfo shows no data found.

Another interesting note is when shares show on all the computers except perhaps one computer, that particular computer can't see itself either, but can see all the rest and they load into Places/Network just fine, just not itself.
By rebooting that computer 3 times in quick succession, it will usually correct itself, but not always.

Then some days, when we are the busiest, that's when shares won't even show up using IP numbers to get to them.  We rebooted one of the newer computers like 27 times before it decided to straighten up and run right for the rest of the day, hi hi.....

But today, and most of yesterday, all has been working well!  

I'm new to Linux and even newer to Ubuntu, only like 2-1/2 months into Ubuntu so far.  Loaded Edubuntu on a spare machine to see if I can understand some of the setting used in a server type environment, even though I doubt if I will ever use a normal server, just a file server for data files is all.
I've read more wiki's and manpages than Carter's has pills and 90% of the data presented is so far over my head its pitiful.
One of the wiki's starts out on the first line, it's assumed you have a full understanding of C++............  yeah right!

I'm one of those that needs a wiki that starts out with, Using your Mouse, left click on Applications, and if the program you are looking for is not there, right click on Edit Menu's.....etc.

One of the first things I encountered when using Ubuntu was a very simple instruction.
If it's not in Synaptic, use add/remove, you may have to install the medibuntu repository.
Uh, OK?  What's a Synaptic, what's add/remove, what's medibuntu and what's a repository.
I know now of course!  But I didn't on day 3!

And even at 2-1/2 months, I still find MOST of the directions for simple things leave out the MOST IMPORTANT DETAILS.  One word in the instructions may take 3 days to figure out what it means, and a couple of reams of paper to print it out, hi hi.....

I know every computer is different and every situation is different and one set of instructions can't cover everything that can go wrong with each installation.

Like my case, if it's set up wrong, WHY does it work some days and not others with no problems??????
If it's set up wrong, it should work at all, I would think!

FWIW:  I've tried so many different configurations and networking methods over the past couple of months, it would make your head swim.  I finally settled back down to Samba using Wicd and things seem to work more often than not.  Unless an upgrade comes down the pike, then we're back to square one again for a day and half the night to in many cases.

But on the bright side, I learn a little something new each day that I never knew before!  And am proud of my accomplishments, even though many of them required help here.  There is no local source to get help here like I had back home.  I live in East Podunk now, double taxations and little to no services.  hi hi.......

Thanks for your ideas and help!
But things like this I just need to study alternatives and basically learn more about how things work.
So, I think you can give it a rest and quit racking your brain too!

Have a Merry Christmas and/or Happy Holidays!

TTUL
Gary

---

### Post by Peter09 on 2008-12-10
make sure the line in /etc/nsswitch.conf looks like this. (Order matters)

hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4

---

### Post by Kellemora on 2008-12-11
Hi Peter

Here is a copy of my nsswitch.conf file

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

The only thing I see different is you have wins in your line!

I can try that and see what happens.

Thanks
TTUL
Gary

---

