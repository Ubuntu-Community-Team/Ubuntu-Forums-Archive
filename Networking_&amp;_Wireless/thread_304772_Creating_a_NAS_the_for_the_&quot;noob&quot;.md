---
title: "Creating a NAS the for the &quot;noob&quot;"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by Imagine3 on 2006-11-22
I will be the frist to admit, I am the biggest Ubuntu, and in general, Linux noob. I have started playing with Ubuntu 6.10 a couple weeks ago (basically when it was released). I had the previous version installed on an extra box for a month or so but didn't get a good chance to play around with it. So I have an idea, but not a really stong grasp on what I want to do.

I origionally wanted to set up a simple NAS to save files on so my laptop and desktop wont be bogged down by all those files. Also the centrally located files would be nice since I do a lot of preliminary work on my laptop and then used my desktop that is more powerful to do production work. I design webpages, do a lot of video editing, and graphic design (up to 2GB file sizes in Photoshop and Illustrator so I need a very powerful system. So setting up a NAS would be the first step. 

Then I got the idea of using it as a webserver. Not accessable to outside my LAN, but to use it as a test server. This way, I can upload sites I am designing and need to be located on a server (PHP and ASP) in order to render correctly and not have to upload them to a test server located a hundred miles away. 

Thats really all I want to do. I looked around these forums and really couldn't find what I needed. I am looking for a very specific and detailed guide as I do not really know what I am doing. I am willing to learn, but for some reason, I haven't been able to grasp the Terminal. Im sorry, but I just don't get it. What would be wonderful is if there was 1 or 2 programs out there I could just install them by double clicking and then it would be set up. 

Can anyone help me? lol :confused:

---

### Post by MiniJames on 2006-11-23
What you are trying to achieve may not be that realistic. I assume that your desktop / laptop are running Windows for Photoshop. So to setup a NAS box you will need to install and configure Samba for Windows file sharing.

As for the web server, no Linux web server will be able to offer true ASP/ASP.net support as it is a proprietry Microsoft platform.

> I haven't been able to grasp the Terminal. Im sorry, but I just don't get it. What would be wonderful is if there was 1 or 2 programs out there I could just install them by double clicking and then it would be set up.

This will make things more difficult because the best way to setup a NAS box is to install ubuntu-server which has no Desktop interface (GUI). You can install Apache (web server) and Samba (windows file sharing) from Synaptic, but I cant confirm it as I've never tried it.

I hope that this answers some of your questions.

:)

---

