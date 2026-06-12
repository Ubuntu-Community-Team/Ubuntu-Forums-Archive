---
title: "Gibberish when distributing files on cluster using torrents"
date: 2017-10-05
forum: Networking &amp; Wireless
---

### Post by ohanoch on 2017-10-05
Hi all,
I am running Ubuntu 16.04.1 LTS 64bit on a cluster and I need to be able  to distribute large files on that cluster. My idea was to distribute  through torrents.
I tried creating a torrent and manage to get a torrent file, but when  trying to seed them with one node and download them with another the the  second node seems to download in a few seconds and creates the folders  and files with correct names and all, but the files themselves appear as  unreadable gibberish  when I look inside them.

I tried creating the torrent file both with ctorrent and with  transmission-create and seeding and downloading both with ctorrent and  qbittorent and with all combinations I get the same results.

Is there something I'm understanding/doing wrong?

Thanks in advance for any help available.

---

### Post by ohanoch on 2017-10-06
So this is embarrassing, I might have had it working all along. I just re-checked and the files I was transferring were corrupted on one of my earlier tries and I have been using them since.

So to sum up this is what worked for me if anybody else ends up needing the same setup:
I create torrents using "transmission-create /path/to/file/or/directory/to/be/torrented -o /path/to/output/directory/output_file_name.torrent" (this is because qbittorrent-nox doesn't provide a tool that I could find to create torrents) 
I run the torrent on the computer with the actual files so it will seed using "qbittorrent-nox ~/path/to/torrent/file/name_of_file.torrent"
I copy the .torrent file to all nodes and run "qbittorrent-nox ~/path/to/torrent/file/name_of_file.torrent" to start downloading

qbittorrent settings I needed to configure:
In "Downloads" change "Save files to location" to the location of the data in the node that is going to be seeding #otherwise that node wont know it has the files specified in the torrent and wont seed them.

In "Speed" tab uncheck "Enable bandwidth management (uTP)"     #
                     uncheck "Apply rate limit to uTP connections"         #This is to avoid issues with the torrents sometimes starting as
                                                                                                #queued and requiring a "force resume"
In "BitTorrent" tab uncheck "Torrent Queueing"                            #This doesn't appear to have fixed the problem 100% though

Thanks for all the help and Im sorry I hassled people for no reason..

---

