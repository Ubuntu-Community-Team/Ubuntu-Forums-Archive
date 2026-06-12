---
title: "Home network shares: NFS or Samba?"
date: 2020-04-12
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2020-04-12
I haven't been in this forum for quite some time. It feels good to be back.

I haven't used Ubuntu since v.9.xx... so please indulge me.

I'm trying to do some reading on the subject but posts on this are fairly disjointed and mostly biased, both ways. So I'm looking for an educated answer. Here's my situation.

I have been running everything I own at home on a Mac Mini (2011... yeah, it's old. High Sierra for those who know it.) I have a Plex Server in that Mac, and the shared folders are all on 2 drives connected to the Mac by USB. So far, I can connect to Plex from my phone when I'm away on another continent and everything works just fine.

I also have a Windows 10 machine. That one doesn't interact much with the rest of the network, but... recently, I was introduced to Minecraft by my son. And he wants to play with me, so I installed a minecraft server on the Windows machine. Works out of the box with very little config needed. At least inside my LAN.

I want to shut down the Win10 pc once in a while, so I struck a deal and bought this nice little PC perfect for a home server. To keep thing reliable, I installed Ubuntu 18.04 LTS. Minimal install, hooked up to Teamviewer to I can remote control from anywhere.

I am planning on disconnecting the USB hard drives from my Mac and connecting them USB to the Ubuntu server, then run a Plex Server from that server. But the server must not do a lot of heavy lifting (conversion jobs and downloading will be remanded to the Mac), so I need a way to take files from my Mac or my Win10 and write those files to the server, so we can watch movies and listen to music through Plex on this server.

From what I am reading, Samba is completely cross-platform. However, I have tried several times to install Samba on the server, and NOTHING connects. Also form what I read, NFS is native to the Mac AND to Ubuntu, and after a small test (browsing the network on my Mac and connecting as guest to the Ub box), it seems to be WAY WAY easier to deal with.

So what should I do? Should I config NFS on both machines and try to install NFS on the Win 10 machine? Or should I keep going trying to install Samba? Which is best? Which is more reliable? Which is easiest?

---

### Post by couzin2000 on 2020-04-12
OK... I guess I have to say "never mind"... just went into Ubuntu and used the current user GUI to open a Local network share as guest... and then accessed it from my mac, copied a file, everything works right out the box.

so never mind.:p

---

### Post by TheFu on 2020-04-12
NFS for unix. That **is** the native network file system for Unix - like Linux and OSX or any other Unix.
Use samba for Windows.

Samba drops permissions and doesn't allow for fine grain permissions control.  Whether that is important or not is a personal decision.

For moving files around a few times, i wouldn't use either.  I&#8217;d use rsync or scp.  ssh is how unix systems communicate.

As to which is "best", that depends on your understanding.  All are reliable provided the configurations are correct and the network underneath is reliable.  No file transfers are solid on a crap network.

BTW, you can use both, concurrently.

Plex does have fewer issues streaming when NFS is used according to the Kodi and OSMC teams.  That has been my experience too. Many people do not have issues streaming using samba.  Probably depends on the client hardware and network.

i don't know of any quality, easy to use sub-$100 NFS implementation for Windows.  i prefer NFS and use it extensively.  i use samba only when necessary and sftp/scp from Windows doesn't work sufficiently.

i stream plex media from around the world without any plex clients or even a plex login. Run a VPN server at home (openvpn or wireguard) or just use an ssh-tunnel for that access.  A secured ssh connection can provide all sorts of access so that no 3rd parties are involved to provide access to your LAN.  To me, using a cloudy service just feels wrong when i know it can be done without needing to trust some external company that has no financial connection to me.  You probably have different sensibilities.

BTW, if the partitions use NTFS, the default settings can provide poor performance. Test and see if you see that or not.

---

### Post by Morbius1 on 2020-04-12
There is someone in this forum that has waited a lifetime for your question so I won't deny him his moment but .....
> Also form what I read, NFS is native to the Mac AND to Ubuntu, and after  a small test (browsing the network on my Mac and connecting as guest to  the Ub box), it seems to be WAY WAY easier to deal with.

Browsing? Connect as Guest? 

Are you talking about seeing the Ubuntu machine under **Shared** in Finder and once selected using **Connect as: Guest** ?

That sounds a lot like Samba to me.

---

### Post by webaake on 2020-04-13
I stopped using nfs in my local network many years ago, since at that time there was a long standing bug which they wouldn't fix. It might be fixed now, so this got me interested and I found this article, comparing performance: [https://ferhatakgun.com/network-share-performance-differences-between-nfs-smb/](https://ferhatakgun.com/network-share-performance-differences-between-nfs-smb/) It seems to favour Nfs, and as said, you can have both in your network. I will try and setup an Nfs share and see for myself.

But I think there are some advantages with Samba;
* There are apps easily available for Android phones and tablets which makes Samba file sharing a breeze between your Ubuntu PC and mobiles/tablets. This can be nice as most Android brands comes with Windows support, not Linux support.
* On the rare occasion I get a guest Windows machine in my network, Samba is already installed and ready to go.

But now; on to Nfs....  :)

---

### Post by Morbius1 on 2020-04-13
> It might be fixed now, so this got me interested and I found this article, comparing performance: [https://ferhatakgun.com/network-shar...tween-nfs-smb/]("https://ferhatakgun.com/network-share-performance-differences-between-nfs-smb/") It seems to favour Nfs, and as said, you can have both in your network.
There is a teensie little problem with the analysis in your link.

The author:

** Set the synology to enable SMB2

** Connected to it from Kubuntu 15.04

** Using a cifs mount: sudo mount -t cifs //IP-OF-YOUR-NAS/NAME-OF-SHARE /mnt/smb/ -o user=YourUserName

CIFS - as in mount.cifs - is controlled by the Linux kernel and the Linux kernel back then was 3.19. By default the Linux kernel would have accessed that server / share using SMB1 not SMB2. 

Today the Linux kernel ( since 4.13.5 or so ) would negotiate the best smb dialect to use so if the Synology today was set to allow SMB3 cifs would have connected with SMB3. SMB1 was slow. SMB2 was faster, SMB2.1 slightly faster, and SMB3 the fastest.

It may very well be that NFS is still faster but the test should be redone with settings that makes sense today.

---

### Post by TheFu on 2020-04-13
These days, samba and NFS are a toss up for performance on solid networks.  I see very similar results with both.

If I had a bad network with any packet errors, I'd be certain to use only TCP connections with NFS as read-only connection to prevent data corruption. The default for NFS is to use UDP, but for 100+ Mbps networks, just add the TCP option to the client-side connections and that solves that. It is a good idea regardless.

---

### Post by webaake on 2020-04-13
Yes, I know that the article is a bit old unfortunately. And this moment I've installed an nfs mount on one machine and a client on another. I can definitely say one thing; there are more files for setting up an nfs share on the server. Seems, to me anyway, more complicated than setting up s samba share.

---

### Post by couzin2000 on 2020-04-13
> **TheFu said:**
> 

i stream plex media from around the world without any plex clients or even a plex login. Run a VPN server at home (openvpn or wireguard) or just use an ssh-tunnel for that access.  A secured ssh connection can provide all sorts of access so that no 3rd parties are involved to provide access to your LAN.  To me, using a cloudy service just feels wrong when i know it can be done without needing to trust some external company that has no financial connection to me.  You probably have different sensibilities.

BTW, if the partitions use NTFS, the default settings can provide poor performance. Test and see if you see that or not.

Well, I wholeheartedly agree with connecting to my home without needing someone else's service to piggyback on. BUT, I do share some Plex media with other people (my band shares our own recordings) and some are pretty far away, so we use Plex for that. I'd rather have them use Plex Media Server account instead of calling 1-800-Couzin2000 for me to help them at 2AM ;-)

That said, yes, I have also been future-proofing my installation, and the drives serving our stuff are actually ExFAT. I would have preferred to go ZFS, but the documentation is sparse for now, so I'll wait for more widespread implementation before signing up for it.


As far as my original post, I was able to run NFS straight from the box by clicking "Share" in my UB box, then accessed it from my Mac Mini as if it had been the local hard drive. So easy.
So I installed NFS Client on my Windows 10 box, that also works pretty seamlessly. 
Thank you so much for the insight, I appreciate it a lot!

---

### Post by TheFu on 2020-04-13
> **webaake said:**
> Yes, I know that the article is a bit old unfortunately. And this moment I've installed an nfs mount on one machine and a client on another. I can definitely say one thing; there are more files for setting up an nfs share on the server. Seems, to me anyway, more complicated than setting up s samba share.

```
$ sudoedit /etc/exports
```
for example:
```
/D/ebooks/Library       nextcloud(ro,async,root_squash) 
```
Seems pretty trivial to me.  No wondering which version, or how users can access the storage or what guests can use or not.  Normal Unix permissions rule.
On the client-side, the fstab gets 1 line if you don't want any advanced features like automounting only when needed. it is pretty simple, like a normal mount, just use "nfs" as the mount type, not ext4 or some other type of file system.

NFS needs 2 lines. 1 each on the server and the client.  Not a 64 line smb.conf file, as one of my samba servers has.

nfs is a kernel module, which is partially why the performance is good.

---

### Post by Morbius1 on 2020-04-13
> As far as my original post, I was able to run NFS straight from the box  by clicking "Share" in my UB box, then accessed it from my Mac Mini as  if it had been the local hard drive. So easy.

OK folks. I admit that the last time I used NFS Richard Nixon was still the senator from California so can somebody please explain the above observation to me. There is a way use NFS from some "Share" setting in Ubuntu?

Or are we talking about Local Network Share:
[ATTACH=CONFIG]285511[/ATTACH]
That ain't NFS that be Samba.

---

### Post by DuckHook on 2020-04-13
> **Morbius1 said:**
> OK folks. I admit that the last time I used NFS Richard Nixon was still the senator from California…
That…

…dates you. It really does. :p

---

### Post by webaake on 2020-04-25
So I've done some small time testing now with Samba and Nfs in parallell. Seems that Nfs with async is faster. And setting up Nfs isn't that much more difficult than Samba. It is kinda neat to set up a per client share scheme, but you can also chose to set up shares for your whole local network. Yes, you can do that too in smb.conf but as said, with many more lines of configuration.

Now I'll look for some Android filemanagers that do Nfs. Guess they're few and far between.

---

### Post by SeijiSensei on 2020-04-25
You can run NFS and Samba servers in parallel on the same machine. I do it all the time.

---

