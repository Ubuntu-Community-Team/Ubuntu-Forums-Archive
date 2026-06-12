---
title: "BitTorrent Client that can search in online repositories"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by flylehe on 2009-05-28
Hi,
I was wondering how you guys search for a specific file for BitTorrent download? And if there is some nice BitTorrent Client that provides the ability to search for a file in online repositories, just as AMULE does? I am now using Transmission BitTorrent Client,which seems not have the function.
Thanks

---

### Post by ssdt on 2009-05-28
Not that i know of. you will have to go to specific sites and search manually.

---

### Post by kamitsukai on 2009-05-28
> **flylehe said:**
> Hi,
I was wondering how you guys search for a specific file for BitTorrent download? And if there is some nice BitTorrent Client that provides the ability to search for a file in online repositories, just as AMULE does? I am now using Transmission BitTorrent Client,which seems not have the function.
Thanks

That's not a particularly good function one of the major advantages of Bittorrent is actually going to the site and seeing how many seeds there are and looking at comments and ratings this gives you an idea of the quality of the download

are you relative new to Bittorrent? (Sorry if I've come across rather condescending but I don't know whether you new user or not =])

---

### Post by flylehe on 2009-05-28
Thank you both!
Yes, to BitTorrent, I am relatively new, compared to emule/amule. What nice sites do you frequently visit for various purposes? e.g. for ebooks, movie, software,...

---

### Post by lovinglinux on 2009-05-28
With BitTorrent you do not share folders and do not have a central server to search for files, you have .torrent files and trackers. Torrent files are like recipes that contain embedded information (metadata) about a single content file being shared (the file you actually want)  and one or more trackers (servers) that are responsible for listing which peers (users IPs) have it.

When you download and start a torrent file, your torrent client communicates with the tracker specified in the torrent metadata and downloads the list of of peer IPs sharing the same file. Then your torrent clients communicates directly with these peers to exchange pieces of the file you want. So while eMule servers stores information of all files being shared by all users in the network, the torrent tracker only stores information about a single file being shared. Additionally, the same torrent file can be tracked by different tracker servers, without knowing about the users of other trackers. For example, there are private trackers that requires invitation. While the users sharing the file "ubuntu-9.04.iso" on a private tracker see each other, they are not listed on the peers list being tracked by a public tracker. So the information about what and where to find who is sharing the file is compartmentalized within the torrent file itself and the tracker responsible for tracking it.

When someone wants to share a file from his computer, he creates a torrent file containing the information about the content he wants to share, then he adds a tracker address that will be responsible for listing/tracking the users sharing it and then distributes this torrent to other people. He doesn't necessarily have to upload this to a web site. He could for example send the torrent file to his friends by e-mail. Nevertheless, there are several web sites that allows you to share torrent files with other users. These sites are not necessarily the ones who provide the tracker server. For example, the site Mininova only functions as a central repository of torrent files, but it is not responsible for tracking them. Each file uploaded to Mininova can have a different tracker address. Nevertheless, there are some sites that functions as a directory of torrent files and also as tracker. 

Sites like Mininova also offers a way to search for torrents. While some torrent clients provides a search function that grabs information from popular torrent sites like Mininova, this feature is merely a web search tool, since there is no way to search the users folders or identify what files the users are sharing if you don't download the torrent and join the tracker. This might sound restrictive, but is actually much more secure, because other peers connected to you can only see the single file you both are sharing using the same tracker. Nobody has access to your folders and they cannot know which other files you are sharing.

There are other sites like Torrentz that do not store torrent files and do not act as a tracker. They are search engines, specialized on listing only torrent files from other sites like Mininova, usually organizing them by categories.

You can also use Google to search for torrents, by appending the string *filetype:torrent* to your search. For example try searching Google for "[ubuntu filetype:torrent](http://www.google.com.br/search?q=ubuntu+filetype%3Atorrent&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)". 

While searching with Google might sound practical, is not necessarily the best method. Mosts sites that offers a repository of torrent files have moderators that try to remove fake files or a system to identify trusted uploaders. Torrentz for example have a green icon next to files from trusted sources and each user registered on Mininova has it's own page directory, so other users know who created the torrent. As already commented on previous posts, these sites also offers a way to check if the torrent file is healthy, by listing the numbers of seeds/peers and offering a feature to comment about the torrent quality. The bigger the number of seeders sharing the file, the fast will be the download speed. Seeders are those who already have the file you want and are just uploading to others, while peers refers to users uploading/downloading it.

There are several torrent clients that you can use. Ubuntu comes with Transmission installed by default and it might be enough for you since you don't have much experience with torrents. If you like a more powerful torrent client then I recommend Deluge. It is also in the repositories, so you can install it using the "Add/Remove" manager.

---

### Post by flylehe on 2009-05-28
Thanks lovinglinux!
That's very informative.

---

