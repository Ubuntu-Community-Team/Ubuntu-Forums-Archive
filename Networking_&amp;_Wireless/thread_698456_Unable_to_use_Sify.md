---
title: "Unable to use Sify"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Paperkraft on 2008-02-16
Hi Everyone,
I just installed Gusty in dualboot with XP and i want to install my ISP's(Sify) broadband client on ubuntu. They want me to install two files,

1. The main debian file called Sify-bbclient3.0 which i managed to install following a "readme" in that archive.
2. The second file looks like some kinda library called openssl which ive to install to get this software working. But the problem is that it is an RPM file and ubuntu doesnt allow me to install it.

I dont have internet connection in ubuntu so i cannot download packages from Synaptic. So please kindly tell me a way to install the library file. Im attaching bth the files.

---

### Post by akudewan on 2008-02-16
I'm a sify user, and I know the trouble one has to go through to get it working. Personally, I use [Antidialer]("http://linux.softpedia.com/get/Communications/Internet-Phone/AntiDialer-9741.shtml"), since the official client sucks. You can also use [SuperSify]("http://thegoan.com/supersify/"), which is a console java based program. The unofficial clients might need the "old protocol" enabled by sify. So they might not work.

In order to get the official client working, you don't need to install the openssl RPM package. It's available in the Ubuntu repositories. But even installing that will not get the client working! You will need to do some sym-linking in the terminal. I might be able to guide you through this. Try running the Sify client in a terminal, and post the error messages here.

---

### Post by Amburkar on 2008-03-29
Though I use different flavor of linux, I encountered similar problem. sifybbclient looks for the library file libssl.so. I could fix it using a softlink.

#cd /usr/lib
#ln -s libssl.so libssl.so.4
#ln -s libcrypto.so libcrypto.so.4

You may also have to do
#ln -s libssl.so.9.8b libssl.so.6
#ln -s libcrypto.so libcrypto.so.6

Since I did this quite sometime ago, I don't remember exactly whether I did the softlinking for both so.4 and so.6!

---

