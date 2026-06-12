---
title: "Why Linux&gt;Linux sharing so bad?"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by jabeez on 2008-01-31
Why is sharing between Linux boxes so terrible? I can open shared files/folders on Windows boxes from Linux with no problem, and access Linux shares from Windows with slightly more work, but accessing Linux shares from a Linux box sucks. I can see the shares, but can't actually do anything with the files therein. Kinda pointless really. Why so complicated or am I missing something simple?

---

### Post by stalker145 on 2008-01-31
> **jabeez said:**
> Why is sharing between Linux boxes so terrible? I can open shared files/folders on Windows boxes from Linux with no problem, and access Linux shares from Windows with slightly more work, but accessing Linux shares from a Linux box sucks. I can see the shares, but can't actually do anything with the files therein. Kinda pointless really. Why so complicated or am I missing something simple?

I'm sure if you gave some specifics, someone could help you a lot better. To my knowledge there are no psychics that hang about in these forums. 

On to your problem of Linux to Linux sharing sucking: Are you using SAMBA? NFS? Have you enabled the remote user? Do you have permissions set up correctly on the shared folders? Have you followed one of the many tutorials around the forums or Google?

Let us know a little more information and we can help better.

---

### Post by jabeez on 2008-01-31
Well, wasn't looking for psychics, although if there are any around that would be pretty sweet!:) Specifics wise, I pretty much gave 'em. I've been using 'Buntu/Linux for quite a few years now, and this has always given me headaches. Sharing between Windows and Linux machines is quite easy, in whatever direction, but sharing between Linux boxes sucks in comparison. I've only ever been able to get Samba to work, even though NFS is supposedly easier. I'm using Kubuntu, and set the folders to share through both Samba and NFS, yet I can only see other networked computers through Samba.

I just set up my bro-in-laws box with Kubuntu, and had to set up sharing for his other computers which are running Vista. I got it up and running, and while in Vista I can browse the shares and open files. But when I boot into Linux. I can see the shares and have full access to them, it just doesn't work nearly as well. For example, in Vista I browse to the shared music folder, click on a file and voila, it plays. Same for documents, pictures, etc. In Linux, I browse to folder, click on file, and nada, Amarok spits out error, OpenOffice starts, but doesn't finish loading. It's not a huge deal, he's set up for what he needs, I guess I'm just curious as to why? I've gone through similar troubles on my own network, i run only Linux and the wife runs mostly Linux, and sharing between the Nix's is always worse.

---

### Post by steveneddy on 2008-01-31
I have Samba installed on both my home sever and my laptop. I have to access both Windows networks and Linux/Unix networks daily at home and at work and I have never had any issues sharing one way or the other.

Gutsy 64 bit, Core 2 Duo

******************************

Long live the magnificent admins of the Ubuntu Forums.

---

### Post by jabeez on 2008-01-31
> **steveneddy said:**
> I have Samba installed on both my home sever and my laptop. I have to access both Windows networks and Linux/Unix networks daily at home and at work and I have never had any issues sharing one way or the other.

Gutsy 64 bit, Core 2 Duo

******************************

Long live the magnificent admins of the Ubuntu Forums.


I don't really have problems sharing, per se, I only have problems accessing media from Nix to Nix. I have gotten it somewhat working in the past, just wondering why so much more difficult than Nix to windows or vice-versa.

---

