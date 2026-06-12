---
title: "Does samba work in Heron?"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by satbunny on 2008-05-31
I am in still running 7.10 Gutsy since I use samba to run shares for my OS X, Windows and Linux boxes. When I heard that Heron has problems with Samba I stayed away.

Has this been resolved? Is it safe to upgrade to Heron now?

---

### Post by jetsam on 2008-05-31
Samba works in Hardy, but there are still outstanding issues.  It's hard to say whether or not they would cause trouble for you.  It depends a little bit on how you approach using Samba to begin with.  

Most of the problems have to do with Samba's integration with the gnome desktop:
--There's a bug on first installing Samba which requires a reboot in order to use the gui to set up shares with Nautilus:
[http://ubuntuforums.org/showthread.php?t=772706]("http://ubuntuforums.org/showthread.php?t=772706")

--There's a problem with Nautilus being unable to browse password protected shares:
[http://ubuntuforums.org/showthread.php?t=784259]("http://ubuntuforums.org/showthread.php?t=784259")

--SMBFS support is deprecated and no longer available in Hardy unless you recompile Samba.  Most users will be better off using CIFS to mount shares instead, but the change is causing trouble for some people who need to mount shares from older NAS devices or older versions of Windows.  

--It's no longer possible to set your workgroup name with the standard gui configuration tool.  You have to do this manually by editing the smb.conf or install a different configuration tool.  (system-config-samba, SWAT)

--Shares configured through Nautilus work completely differently and no longer appear as regular shares in the smb.conf.  This is actually how it's supposed to work, but it is a big change so it's something to know about.   Shares that are defined in the smb.conf work as they should, but they are no longer configurable through the standard GUI.  


As far as I know there aren't any problems with the Hardy version of Samba itself as a server.  If you're used to manually editing the smb.conf, you might not even notice any of the above problems.  

Still, it's a tough call since it sounds like Samba is pretty important to your network.  If you don't need anything specific to Hardy, I think I'd hold off personally.  (My Samba server is still Gutsy, my Ubuntu desktop is now Hardy.)

---

### Post by Iowan on 2008-05-31
I set up a testbed Hardy LAMPS (threw in Samba) server.  Only client is an XP laptop via crossover cable.  I'm still having issues with it (and it's workgroup) sometimes showing up and sometimes not.  It's usable, but there are still some rough edges.

---

### Post by satbunny on 2008-06-01
Thanks for the advice so far..

I have a Xubuntu 7.10 box that is my samba share.
I am quite used to editing smb.conf by hand and always have.
There are then 2 Ububtu 7.10 boxes that connect to the shares using a permanent mount command in fstab, 1 OS X machine that just connect as and when, and a Windows XP box that has the drives permanently connected as drives under Windows.

Now I could move to CIFS, or even NFS for the Linux and OS X boxes, but is there an CIFS or NFS extension to XP that I could use.

I am not fully sure from your answer if in fact anything will stop working, save that I'd have to reinstall smbfs on the Linux boxes.

I am happy to address these issues head-on, but I may need a leetle more advice, otherwise I may be stuck on Gutsy for a long while in a kind of permanent dither..

Anyone else able to help with how-to, advice, URLs, or even a step by step guide.. or a simple statement that in fact my method will still work once I install smbfs..

---

### Post by jetsam on 2008-06-01
It sounds like you should be fine with the upgrade.  

There shouldn't be any problems mounting a share from a samba server with CIFS, though you may need to modify the commands in your fstab files.  

I was intending in the above post to just give a run down on the issues I've seen impacting people, judging mostly from the forum posts I've read.  Since you edit your smb.conf manually and mount shares manually to your Ubuntu clients, I don't think they'll have much if any impact on you.  

There's always some risk with any upgrade that an unforeseen issue will arise.  That's just kind of the nature of upgrades.  Hopefully your own resources or the forums can help you work through any difficulties.  

> is there an CIFS or NFS extension to XP that I could use?


You're essentially using Microsoft CIFS if you map network drives in Windows.  I wish there was a good free-software NFS client for Windows.  There's a sort of half supported thing that Microsoft puts out, and then there are some proprietary clients.

---

### Post by satbunny on 2008-06-01
It looks like I need to investigate CIFS and fstab then.

---

### Post by jetsam on 2008-06-01
It can be a relatively painless transition.  CIFS has been in Ubuntu for a long time.  What's new is that SMBFS has gone away.  Even if your fstab specifies a SMBFS mount, it gets translated underneath into a CIFS mount.  Here's one thread I was involved in where the fix was a few easy syntax translations:
[unable to mount samba network shares]("http://ubuntuforums.org/showthread.php?t=808554")

The best full featured CIFS how-to by Dmizer is here:
[Mount samba shares with utf8 encoding using cifs]("http://ubuntuforums.org/showthread.php?t=288534")

...and, finally, all the gory details are available from a terminal with:
```
man mount.cifs
```

**Added**: I should mention as well that the error messages you get if you do:
```
sudo mount -a
```
...are quite helpful and actually tell you how to update the syntax of your fstab mounts.

---

### Post by satbunny on 2008-06-02
I have updated my fstab. You are right, I used the other thread you had posted and read the error messages from the mount command.

So I think that my Linux client is now connecting properly using CIFS via the fstab.

Do I need to amend the samba server at all if I upgrade that to hardy?

---

### Post by jetsam on 2008-06-02
> Do I need to amend the samba server at all if I upgrade that to hardy?

As far as I know, no.  The SMBFS to CIFS transition only affects the client set-up.  

I just now upgraded my Xubuntu Gutsy server to Hardy and everything seems A-OK so far.  

I just used the distro upgrade button in update manager to do the upgrade.  It asked me at the end of the upgrade whether I wanted to keep my old smb.conf or not.  I said I did, and it seems to work without a hitch.  I'm streaming music from it now.  Even SWAT still works; I use it to manage my smb.conf.

You might want to make a backup of your smb.conf and etc/fstab file before you do the upgrade just for good measure.   

I'm not seeing the browsing problems that Iowan and some other people have reported.  That may be because I have my server set up as WINS server.  

Good luck with it.  Millage varies. ;)

---

### Post by satbunny on 2008-06-03
Wish me luck. I am downloading the CD iso now, I have 3 machines so the CD route saves some bandwidth. 

Fingers crossed.

:)

---

### Post by linux6994 on 2008-06-04
Samba works just fine in Heron. This is what I have installed.

---

### Post by satbunny on 2008-06-04
I have now upgraded my server to Heron and it works fine with the existing smb.conf

I have also noted that having my samba server clearly defined as the WINS server has also helped samba stability.

I edited my client fstab files to CIFS rather than SMBFS (see above) and they work fine, in fact maybe faster (but that may be due to having a WINS server now).

My XP box hasn't noticed a difference nor have my OS X boxes.

I shall upgrade my clients to Hero now and see if I see any differences.

All going quite well.

---

### Post by jetsam on 2008-06-04
CIFS is faster and more stable than SMBFS.  A CIFS mount doesn't really need network browsing, so it's just CIFS itself that's giving you a speed boost.  

The WINS server, in my experience, does help a great deal with browsing stability.  I would recommend it more often on the forums, but it's a network service, so in order to work properly it should really be available on the network most or all of the time.  Not everybody wants to or needs to run Samba like that.  

Be sure to point your clients back at your WINS server.  You do this with Ubuntu clients in the smb.conf with the line:
```
wins server = <ip address of WINS server>
```  
On Windows XP clients, it's under Control Panel-->Network Connections--><Your connection>-->Internet Protocol (TCP/IP)-->Properties Button-->Advanced Button-->WINS tab.
I'm not sure how to set this on OSX.

Some routers let you assign the WINS server address to clients with DHCP.  The "prosumer" Netgears in the metal blue boxes seem to allow this.  It not a common feature in routers, but it's handy if you have the ability.    

Glad it's going well.  Keep us posted.

---

