---
title: "Need to access printers and shared files on vista pc from ubuntu 8.04 laptop"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Lori Whitty on 2008-05-17
Help!  I am brand new to ubuntu.  I installed 8.04 and have internet working after numerous attempts to get my broadband wireless card to work...lol.  Anyway...our home network is all windows machines except for mine.  The pc that has our printer connected to it uses Vista.  I need to access that printer and cannot so far.  I also need to access shared files on the vista pc to transfer files I saved from my laptop before installing ubuntu 8.04 and deleting Windows Vista.  I see the computer when I click places>network.  But when I click on the computer I see no files.  As for printing it will see the pc but no printer.  PLEASE HELP???

---

### Post by nicedude on 2008-05-17
In a case like this I would recomend you install filezilla on your ubuntu and vista machines ( There are versions for both OS's ) then configure whatever one you want to be a server and set a shared file directory with password protection. Then you can log onto that share and get files or deposit files depending on how you set it up.

Filezilla is a very popular program with millions of downloads so I am sure it can handle this with ease. It will also allow you to access your share from somewhere else through the internet if you want so you can amaze your friends at how smart you are when you visit them and log in to your own FTP file server :-)

As for the printing you have to share the printer in Vista and then configure Ubuntu to use it. I can't give exact advise on this as I kicked VISTA off my new laptop 10 minutes after turning it on and loaded XP PRO CORPORATE and then set up Dual boot with Gutsy. I have since just kicked XP off as well and now have Hardy 8.04 Ubuntu on that partition and I am trying to forget Microscum exists :-)

---

### Post by FreakTech on 2008-05-17
There is a bug in gvfsd-smb-browse file  Here's a link.  Hope this helps

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

---

### Post by Lori Whitty on 2008-05-18
I'm sorry but being brand new to ubuntu and linux, the patch info is still a little confusing.  I did get the source files again for gvfs but I don't quite understand how to get and apply the patch.  Is there a clearer explanation for those of us that are so new to all this?

---

### Post by FreakTech on 2008-05-18
Here is a link to an already compiled patch that is further down in the last post pointed to:

[http://launchpadlibrarian.net/14466364/gvfsd-smb-browse.gz](http://launchpadlibrarian.net/14466364/gvfsd-smb-browse.gz)

Just download the patch

Go to usr/lib/gvfs and make copy of gvfsd-smb-browse adding .bak to the end.

Then copy the downloaded fvfsd-smb-browse file into usr/lib/gvfs

---

### Post by Lori Whitty on 2008-05-19
Well, I did as instructed.  I copied and renamed the file, downloaded the patch, but when I tried to move the new file into /usr/lib/gvfs it won't go.  It says I don't have permission.  Do I need to do this in the terminal?  And, if I do, what commands do I use?  How do I do it?

---

### Post by Lori Whitty on 2008-05-20
Ok I have moved the file but I still have network problems seeing the other computers.  Help?

---

### Post by KawaiDon on 2008-05-24
> **Lori Whitty said:**
> Ok I have moved the file but I still have network problems seeing the other computers.  Help?

I tried this fix as well, with no change.

I read elsewhere that Vista service pack 1 might be messing with our printing.

I could access shared files and printers before Vista SP1, and using Ubuntu 7.10 (Gutsy)

Any more help coming??

---

### Post by KawaiDon on 2008-05-24
I'd like to bump this up top again - has anyone solved this printing / file sharing, or am I just being thick?

Don Mannino

---

### Post by Lori Whitty on 2008-05-24
I haven't solved it yet either and I was beginning to think no one else would post to this thread lol!  I like ubuntu but I REALLY need file and print sharing with our vista pc on our home network.  HELP???

---

### Post by Shmalignant on 2008-05-27
> **Lori Whitty said:**
> I haven't solved it yet either and I was beginning to think no one else would post to this thread lol!  I like ubuntu but I REALLY need file and print sharing with our vista pc on our home network.  HELP???

I'm new and trying to figure this out myself.  I'll let you know if I find anything that helps.:)

---

### Post by Lori Whitty on 2008-06-13
Well, I still haven't found a way to make this work in ubuntu, so I downloaded the kubuntu desktop into my ubuntu and tried konqueror.  That worked.  I can print over our home network and can share files over the network.  Nautilus must still be full of glitches.  At least I found a solution for now.  Just thought I'd post where I'm at with this right now.

---

### Post by KawaiDon on 2008-06-14
I found the answer!

Change the network name and computer name to the IP address in Samba - boom, printer works great!

Here is the format.  the Xs are for the IP address:

smb://xxx.xxx.xxx.xxx/printer%share_name

Good luck!

Don Mannino

---

### Post by ttoolin on 2008-06-24
Hi, Don-

I tried your suggestion, and it did not work for me.  I am glad that it worked for you.

I am trying to network with vista SP1 home basic.

Thanks again, for something to try.

terry

---

### Post by dtcostelloe on 2010-01-02
It's just a thought ... but you might check the Vista side of things, try disabling "require password" to log on.  (That's in Vista, under advanced networking, I think)  I've had issues with Vista / Win7 not wanting to allow remote computers (Ubuntu or XP) to access their shared folders and stuff without relaxing the security settings a little.  I'm having a somewhat similar issue getting Ubuntu to find my shared printer - but my setup is a bit different, as I'm going across subnets through a router ... but in your case I'd check the Vista side of the network setup.  I'd try adjusting that setting I mentioned, maybe even temporarily disable the Windows Firewall ... just to eliminate all possible sources of interference.

---

