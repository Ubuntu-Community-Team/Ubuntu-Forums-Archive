---
title: "NFS won't mount"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Norst on 2008-05-01
Ok I have read every article I can find and it would seem this should be real easy.

**Server (Feisty):**
Installed nfs-kernel-server and portmap
have exports file as follows:
```
/var/otherwebs/gbfile 192.168.2.1/24(rw,sync)
/home/norstrom/dvdrip-data 192.168.2.1/24(rw,sync)

```
portmap is set to not use the loopback as I have read.
[B]
Client1 (Hardy):[/B] with needed portmap and nfs-common
```
 sudo mount -v 192.168.2.80:/gbfile /media/ISO/
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Thu May  1 20:29:08 2008
mount.nfs: text-based options: 'addr=192.168.2.80'
mount.nfs: internal error

```

**Client2 (Feisty):**
```
sudo mount -v 192.168.2.80:/gbfile /media/test/
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: trying 192.168.2.80 prog 100003 vers 3 prot tcp port 2049
mount.nfs: trying 192.168.2.80 prog 100005 vers 3 prot udp port 32802
mount.nfs: mount to NFS server '192.168.2.80' failed: timed out, retrying
mount.nfs: trying 192.168.2.80 prog 100003 vers 3 prot tcp port 2049
mount.nfs: trying 192.168.2.80 prog 100005 vers 3 prot udp port 32802
***AND SO ON***

```

Server: (Try to mount to it's self at server console (not sure if this is supposed to work or not):
```
sudo mount -v -t nfs 192.168.2.80:/gbfile /media/ISO/
mount.nfs: trying 192.168.2.80 prog 100003 vers 3 prot tcp port 2049
mount.nfs: trying 192.168.2.80 prog 100005 vers 3 prot udp port 32802
mount.nfs: 192.168.2.80:/gbfile failed, reason given by server: Permission denied
```

So a Hardy client gets an internal error, and Feisty client gets time outs, and try'n to mount to it's self I get a permission denied... WTF? Anyone have any ideas?

Any help would be great, Thank you.

Norst

---

### Post by Norst on 2008-05-02
I've upgraded the server to Hardy and I still can't get either of the clients to mount. 

I also completely (as far as I know) removed nfs from the server and reinstalled.

Any ideas at all at this point are welcome.

Thanks,
Norst

---

### Post by xdice on 2008-05-02
> **Norst said:**
> I've upgraded the server to Hardy and I still can't get either of the clients to mount. 

I also completely (as far as I know) removed nfs from the server and reinstalled.

Any ideas at all at this point are welcome.

Thanks,
Norst

When you export the directories off the server, your mount command on the client has to have the full exported path.

So, for your example from your first post
```
/var/otherwebs/gbfile 192.168.2.1/24(rw,sync)
/home/norstrom/dvdrip-data 192.168.2.1/24(rw,sync)
```

Your mount command on your client should look like this:
```

sudo mount -v 192.168.2.80:/var/otherwebs/gbfile /media/ISO/

```

Try that, it should work (it's how I have my shares off my file server mounted onto my desktop box, and it works flawlessly.).

---

### Post by esekyavuz on 2008-05-02
I had this problem too. Not sure if for the same reasons.

This was a clean install on a Dell laptop of 64-bit Kubuntu KDE4.

Surfing the web and getting emails was no problem, but the router's setup page was not accessible.

Mounting a tried-and-true nfs share from a server running Gutsy gave "nfs: internal error"

In Firestarter I selected "Stop Firewall" and then in a terminal tried to ping machines on the LAN. Got "destination host unreachable" for everything, including the router.

After a lot of typing of commands I hardly understand,based on advice in forums, I decided that maybe Hardy was using the wireless card for internet, but wanted to use the ethernet connection for the LAN. And I had no cable connected.

Then I remembered that during installation, I had selected to set up the network automatically. But I had only wifi, and it was encrypted, so no way did that work. I had gotten the wireless going by clicking on the icon in the system tray and typing in the passkey.

So to fix it, I chose the brilliant and elegant solution of a clean install, and this time chose "setup network later". It all works fine now.

---

### Post by Norst on 2008-05-02
Well I tried with the full path:
```
sudo mount -t nfs -v 192.168.2.80:/var/otherwebs/gbfile/ /media/ISO/
mount.nfs: timeout set for Fri May  2 17:38:28 2008
mount.nfs: text-based options: 'addr=192.168.2.80'
mount.nfs: internal error

```

I can ping my server and also SSH into it (that's how I'm editing the exports file and any other changes).

On a whim I tried something. I made a new user on the client box and logged in to it.
I then tried the same mount command and this time I had no errors at all, it seemed to work. But upon looking in the mounted folder, there was nothing there. It did not mount, but I got no errors or any info even with the -v. I'm wondering if it might have something to do with permissions or something but I'm not sure where or what to look for.

Norst

---

### Post by nandoc on 2008-05-22
Hi all,
Same problem here until I had to install nfs-server on the client... yes on the client and portmap too. But now I am having another problem: "mount.nfs: internal error" this is only happening on my wireless connected Laptop. I am able to browse file on the server, but if I open a given file (OpenOffice programs only, gedit works fine as I can tell) and save it... Nautilus locks, OO Calc loks and the only way to get around is to "force exit" and reboot... Of course the file becomes corrupted and... empty.... What a nightmare.
Server Ubuntu 8.04 Server
Clients Ubuntu 8.04 
Hope this guides somebody...
Best wishes,
Fernando

---

### Post by MadHawk1 on 2008-10-18
nandoc, unfortunately I have exactly the same problem with NFS when I'm trying to access files through wireless connection! 
Does anyone have an advise, please?

---

### Post by doktorOblivion on 2009-03-12
I am on 

egriffin@oblivion:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  48914  status
    100024    1   tcp  48655  status
egriffin@oblivion:~$ uname -a
Linux oblivion 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

my mount cmd
mount.nfs: internal error



CAN you FIX this freakin ISSUE?

Thanks.

---

### Post by buntunub on 2009-03-12
I use nfsv4 and it works just ducky. How to [here]("https://help.ubuntu.com/community/NFSv4Howto"). Its simple, just follow that guide which has you create a /export directory on your server of the drives/partitions you are exporting and then you have to setup your fstab correctly on the client side to face the exports. Simple and works every time I setup new clients I simply copy/paste over the fstab entries. No muss no fuss.

---

