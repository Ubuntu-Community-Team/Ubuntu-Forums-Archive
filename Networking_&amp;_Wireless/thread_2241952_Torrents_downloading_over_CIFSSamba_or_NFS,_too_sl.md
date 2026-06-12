---
title: "Torrents downloading over CIFS/Samba or NFS, too slow"
date: 2014-08-29
forum: Networking &amp; Wireless
---

### Post by toshko3 on 2014-08-29
Hi, I'm unable to find a way to use the full network speed when downloading torrents, although I searched Google hardly.
I have a file server, with a shared HDD and a client, downloading torrents on it, through CIFS or NFS. All ubuntu.
In both of the cases (with Samba sharing and NFS sharing on the server) the maximum average speed of torrents downloading is about 2MB/s, also the client PC and server are struggling with very high CPU loads.
If I download locally it is about 6MB/s and no such CPU loading.
If anyone is using this scenario, please help me make a file server for media downloads through the network and viewing them later on clients!
:)

---

### Post by ian-weisser on 2014-08-29
> **toshko3 said:**
> In both of the cases (with Samba sharing and NFS sharing on the server) the maximum average speed of torrents downloading is about 2MB, also the client PC and server are struggling with very high CPU loads.

Are you sharing the downloading (incomplete) files?
That would explain some of the CPU load.

---

### Post by toshko3 on 2014-08-29
I don't understand your question. Do you mean, "is the torrent client seeding files, before they are downloaded completely"?

---

### Post by ian-weisser on 2014-08-29
Are you sharing a file (via Samba or CIFS) that is constantly changing because the torrent client is still downloading it?
Or are you sharing only complete (fully downloaded) files?

Torrent uploads should not affect Samba/CIFS, and should have only a moderate impact on your CPU load. On most machines, torrent uploads will exhaust typical bandwidth capacity before you notice lag or excessive CPU load.

---

### Post by toshko3 on 2014-08-30
Well, yes, I'm sharing the file, while it is still downloading, but it is not accessed by anyone, because it is still not downloaded :)
It couldn't be otherwise, because I'm downloading the torrent from my PC to the shared server folder. I just want to use my file server as a shared media folder, too.

The strange thing is that when I'm copying a file from my PC to the shared server folder it is copying with average speed of about 10MB/s. When I'm downloading the same file with torrent, it downloads with no more than 2MB/s and the PC is loaded and unusable. So there must be something in the torrent technology that doesn't work well with CIFS/Samba.

---

### Post by toshko3 on 2014-08-30
Well, yes, I'm sharing the file, while it is still downloading, but it is not accessed by anyone, because it is still not downloaded :)
It couldn't be otherwise, because I'm downloading the torrent from my PC to the shared server folder. I just want to use my file server as a shared media folder, too.

The strange thing is that when I'm copying a file from my PC to the shared server folder it is copying with average speed of about 10MB/s. When I'm downloading the same file with torrent, it downloads with no more than 2MB/s and the PC is loaded and unusable. So there must be something in the torrent technology that doesn't work well with CIFS/Samba.

---

### Post by SeijiSensei on 2014-08-30
> **toshko3 said:**
> The strange thing is that when I'm copying a file from my PC to the shared server folder it is copying with average speed of about 10MB/s. When I'm downloading the same file with torrent, it downloads with no more than 2MB/s and the PC is loaded and unusable. So there must be something in the torrent technology that doesn't work well with CIFS/Samba.

First, you cannot compare the speed of a transfer over your internal network with a torrent download.  That will be limited by the maximum speed of your Internet connection.  2 Mbit isn't especially slow if you are in the US.  Try visiting [http://speedtest.net](http://speedtest.net) and see what your maximum speed is.  Torrents won't download more quickly than that.  Often a good torrent with a lot of peers can max out your connection or come close to it.

As for the PC being overloaded, I've found that different torrent clients can put different amounts of load on the machine. KTorrent is especially problematic; Transmission seems better.  For the ultimate in lightweight clients, you can use ctorrent from the command line.  It's in the Ubuntu repositories.

On the machine running torrents, use the command "top" to monitor the performance of the programs you are running.  I can pretty much guarantee that any performance issues concerning torrents have nothing to do with Samba.

---

### Post by toshko3 on 2014-08-30
Thanks SeijiSensei, but I think you overlooked my explanation. The problem is exactly with the Samba sharing. I am downloading the same torrent with 6MB/s locally on the PC, but when downloading on the shared folder, the speed is about 2MB/s.

---

### Post by ian-weisser on 2014-08-30
> **toshko3 said:**
> The problem is exactly with the Samba sharing. I am downloading the same torrent with 6MB/s locally on the PC, but when downloading on the shared folder, the speed is about 2MB/s.

Ooh. That's very confusing. You seem to be using 'downloading' and 'sharing' interchangeably for two different methods, and we're not psychic.

Please use different, consistent terms to be clear when you mean 'Sharing a file on a LAN' (a client retrieving files from a server using Samba) or 'Downloading a file from the internet using a torrent client'. Or simply say 'Samba-ing' and 'Torrent-ing'

It's making my head hurt.

---

### Post by toshko3 on 2014-08-31
OK, let me explain it simple:
I have a File server and a PC.
1. The File server shares a folder with Samba (192.168.13.252/Folder).

2. The PC doesn't have free space on itself. It downloads torrents directly on the server's shared folder. This is accomplished by mounting the server's shared folder through CIFS. The fstab entry is like this:

```
//192.168.13.252/Folder /media/maps/Folder cifs credentials=/root/.smbcredentials,uid=user,gid=group,noperm,iocharset=utf8,soft 0 0
```

3. Then the PC uses the downloaded files, again directly from the server's folder (/media/maps/Folder).

I hope it's clear now. After all it's pretty standard usage, right? A file server and a mapped folder on a client PC.

---

### Post by SeijiSensei on 2014-08-31
When your machine running the torrent client saves the file to the server, it has to use the same bandwidth that you are using to download the file.  So each packet is downloaded temporarily to the client machine, then copied back across the wire to the server.  The resulting slowdown is especially noticeable on wifi networks.  Wifi is a "half-duplex" technology which means data cannot be simultaneously sent in both directions, making reading and writing back much slower.  You'd get much better results if you first downloaded the file to the client machine, then copied it to the server when it is complete.  Many torrent clients will let you specify a final destination to which the file is copied when finished.

Why not run the torrent client on the server?  Most torrent software lets you set up the client as a web server that you can access over the network.

---

### Post by toshko3 on 2014-08-31
Thanks Seiji, this is a good idea, but not so convenient.
By the way, I tested the speed of downloading a regular file from a webserver from Internet. It's downloading with about 7-8MB/s again. And you are right, the LAN card is one and only. Take a look:

[ATTACH=CONFIG]255997[/ATTACH]

---

