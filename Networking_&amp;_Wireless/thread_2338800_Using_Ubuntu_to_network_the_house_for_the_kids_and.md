---
title: "Using Ubuntu to network the house for the kids and wife."
date: 2016-10-02
forum: Networking &amp; Wireless
---

### Post by Mark_McDonald on 2016-10-02
Home office desktop PC is a HP Elite Desk 800 G1 in SFF and has a i5-4570 with 500GB HDD and OEM W7 Pro 64 bit.
2nd custom PC is an ASUS P6T X58 LGA-1366 with an i7-920 and GTX-650 and  2x 500GB HDD that has a M.A.K. W7 Pro 64 bit. Those two PC's sit  side-by-side in the office.

I want to use the custom PC as a MS Windows 7 gaming PC (World of Tanks and simple  Steam games) 
I also want to use it as a downloading PC (music, videos, games, programs) and  a home server and NAS.
We currently have a cloud, 1TB that we use to casually back up stuff. Like on our phones.

House - 2 floors, main and basement. Basement has a TV in the living  room with a PS4 and the office where both computers are. Also iPad and  iPhone used in WiFi mode by a family member downstairs that sits on the  couch in front of the TV downstairs.
I am on the computer in the office downstairs, playing games, watching  Youtube, generally multi-tasking. Tons and tons of websites open, no  multiple video just one video if that.
Upstairs - TV in the living room upstairs, and an iPad used by another family member via WiFi in front of that TV.
Planning on buying an Android Shield for the basement TV, either with the existing TV in the living room, or buy a TV for the office. 
We also have Netflix on the TV's, and a SONO's wireless music box  attached to our private router, which is hooked up to the cable ISP  router. The ISP router's WiFi is turned off because its just so old and poor, I dont even think it has 5Ghz.

I have used Ubuntu in the past, which I didnt like the interface much. I then tried XUbuntu which I liked more.
I think what I want to do is have a VM on the custom PC (I will call it PC-2), whether the VM is Linux, or Windows I do not know. But I'd like to be able to play games on PC-2 because it has the GPU along with downloading, server, and nas as mentioned above.

With all that said, I'd probably just go with another mainstream linux. I dont really know if I need a low resource Linux or not. I will end up buying a X56?? Xeon chip for PC-2, 3.3GHz or higher, but I havent decided on 4C/8T or 6C/12T. Plus of course OC it, with a cooling system. The games I will be playing on it arent really CPU instensive, its more of an interest for me or shall I say hobby.

My questions are 
1) Which O/S do I put in VM?
2) What Linux Server program is easiest to use?
3) Do I need a low resource Linux?
4) Comment not a Q - We really dont "need" a server, but I just want to give it a go. The cloud works fine. But I'd like to stream some stuff, maybe World of Tanks to the TV, Android to the main level TV. And of course I will be downloading a lot of Movies and Tunes, so storage of that I will need, and I want to stream the movies to all the TV's. I can hardwire the office to the PS4 and downstairs TV.
5) Cant think of it right now.

---

### Post by ajgreeny on 2016-10-02
1). If you want the best performance for the games, for which you will need the best direct access to the graphic card, you should definitely use Windows as the host on your custom PC2 machine; VMs, though good will never be as good as a hard-metal installation.

2/3). I'm not completely sure what the server will be used for but it would appear that it is most likely just a file server for the other computers around the house, or maybe a media-server, neither of which need a high-resource machine; some people even manage those two server needs with Raspberry-Pi hardware I believe.

I have both Plexmedia-server and minidlna running on my main desktop computer and it serves all my media needs to both a smart TV (an LG model with web-os2) which can play files from both Plex and minidlna, and also to Now-TV set-top boxes with Plex client software side-loaded which are attached to old, non-smart TVs which can not use minidlna.

I am able to record TV programmes onto a USB drive from the non-smart TVs as .ts mpeg files, copy them to my main desktop drive, and then serve them to the clients using either Plex or minidlna with no major problems.  I can also use the unofficial PlexHomeTheatre package which is available from a PPA repo to play the media files on other computers in the house.

All the above is entirely using Wifi except the main desktop machine which is ethernet attached to the router; all clients are Wifi.

I hope that helps a bit; I'm not a gamer so can not help with that part of your query at all.

---

