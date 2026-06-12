---
title: "PSP MP3 Streaming"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by pyromanic123boom on 2008-08-12
So, on my sister's Windows laptop, I installed this easily: [http://skattertech.com/2006/04/stream-itunes-library-to-psp/](http://skattertech.com/2006/04/stream-itunes-library-to-psp/). It's very easy, with a simple executable server and a RSS stream. So naturally, I thought I'd do the same on the Ubuntu desktop with the PSP. 

I tried this: [http://gryphius.wgwh.ch/index.php?option=com_content&task=view&id=22&Itemid=42](http://gryphius.wgwh.ch/index.php?option=com_content&task=view&id=22&Itemid=42) with no success. I also tried sharing the files on an IIS server with Samba, going to the IP address on my PSP. No luck either. Then I tried PSPFTD, a file sharing program. Unfortunately, my PSP didn't run the program well. I read it was a buggy homebrew app anyway. Rhythmbox doesn't stream to my PSP either. 

So no easy luck. I cannot figure out how to stream my MP3s to my PSP. I think it would be simple, to set up a simple RSS server. Has anyone else had problems with this? Any solutions? I would just like to listen to my music and audiobooks without filling up my Memorystick. By the way, I have 3.90 M33, and my desktop is running 8.04 hardy. Thanks for any help.

---

### Post by pyromanic123boom on 2008-08-12
I'll answer my own post a little. I did this: [http://www.psp411.com/show/guide/44/0/Streaming_Music_From_Your_PC_To_Your_PSP.html](http://www.psp411.com/show/guide/44/0/Streaming_Music_From_Your_PC_To_Your_PSP.html), and am now able to access my music through typing [http://localhost:8080](http://localhost:8080) on one of the networked computers. I just can't get my PSP to work when i type in [http://ip.address:8080](http://ip.address:8080) . any ideas?

---

### Post by pyromanic123boom on 2008-08-12
Well it was a simple error- firestarter was blocking my psp traffic. So if anyone wants to get their music streamed to their PSP, following this guide: [http://www.psp411.com/show/guide/44/0/Streaming_Music_From_Your_PC_To_Your_PSP.html](http://www.psp411.com/show/guide/44/0/Streaming_Music_From_Your_PC_To_Your_PSP.html)

---

