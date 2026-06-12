---
title: "Shared Folder Between Host and Virtual OS Running a VPN"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by ashgun on 2014-08-21
Hello All, 

I am a long time lurker and searcher for the past few years as I have worked on various personal project. 

To start I am working with Ubuntu 14.04 on a PC sitting behind my TV. OS is on SSD with two HDDs for storage, Core 2 due quad core, 6g ram. It works as a Plex media server for external network access, to watch movies on the tv, download, and a file server/backup using BitTorrent sync. If I am not home I will access it using Team Viewer 9. I recently started using Private Internet Access as a VPN service, so far so good. 

Problem is that I can't access Plex outside my network when I am connected to the VPN (tried some simple things like connecting over port 110, didn't work). I can turn it on and off using Team Viewer but then I need to wait to reconnect. I am also sure ill forget once in a while and be SOL when I can't remote in. All in all its a pain, why not make things simpler. 

My idea (not sure if its simpler really...) is to run a virtual machine with Team Viewer, torrent client, and the VPN on the host. Created a shared folder where the host can access the files (to be eventually moved and stored on the host) Or rather then a shared folder use a BitTorrent sync folder. (I feel like sync would send the data on a huge loop out and back in my network because of the VPN) 

The idea is to make a download remote into the virtual computer on VPN. Everything else would be on the host computer not on VPN. 

Will this work? Is there a simpler way? I am open for suggestions. 

I also am running folding@home on the host computer (just wondering if you think it will all blow up)

Thanks in advance

---

### Post by weatherman2 on 2014-08-21
Can you clarify exactly what you mean?

You have a machine at home you'd like to access remotely.  You've setup a VPN at home so you can access machines on your home network remotely?  Or signed up for a VPN service with some company, and when you connect to it you can't access your home server?

---

### Post by ashgun on 2014-08-22
weatherman2, 

I have a machine at home that I want to access from outside of my network. I am currently able to do this with Team Viewer 9 when I am connected to the VPN (provided by private internet access) and when I am not. The VPN is to hide my network activity. 

I can connect and disconnect the VPN remotely, but that does cause me temporary connectivity issues (ip address change). 

When I am running the VPN I am unable to access Plex (media streaming software) from outside of my network. 

I am thinking about creating an isolated machine to always be on the VPN. But I need the isolated machine to be able to move files to the host computer.

---

### Post by ashgun on 2014-08-22
My primary question is: If I have a host computer and a virtual computer, if the host computer is connected normally, and the virtual computer is on a VPN can I still create a shared folder between the two?

---

