---
title: "need a router and what else?"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by brandon333 on 2008-01-01
I am trying to not only share my internet connection with a ps3 but also file share meaning be able to stream/import music, videos and music to my ps3 from my pc but really from my pcs external hard drive.

First off I have a mac, not sure if that matters as I mainly will be running ubuntu, in fact soon just ubuntu once I am done doing some home movie editing with mac osx.

I want to run wired not wireless but I also want to able to be on the network wireless with a psp and still have that option open for laptops etc in the future.

So what router is compatible with ubuntu that is both wired and wireless?

Will a ps3 be able to get files off of an external hard drive on my computer, or do/should I buy one that is a network one (ethernet vs firewir)

Where in ubuntu do I set up sharing for the ps3 to see these files to stream?

Thanks.

---

### Post by sonofusion82 on 2008-01-01
how about  Asus WL-700gE? it an integrated router + ext harddisk + media server. it even has built it downloader and bittorrent client. i have been wanting this but of course it is a bit pricey.

---

### Post by foolsh on 2008-01-01
If I had my choice of router it would be linksys wrt cause you can install a custom linux distro on it
check out [http://openwrt.org/](http://openwrt.org/)
and
[http://www.linuxjournal.com/article/7322](http://www.linuxjournal.com/article/7322)

---

### Post by Predator[23rd] on 2008-01-01
Hi!

> **brandon333 said:**
> So what router is compatible with ubuntu that is both wired and wireless?

The routers you can buy these days are totally independent from the hardware behind it. It is like INTERNET <> YOUR-ROUTER <> YOUR-LAN.

Your router manages your connection to the internet and handles, in most cases by using the build-in DHCP-server, your internal LAN. Router setup is being done with a webbrowser.

All you need is a running OS with a webbrowser and the ability to manually configure your network card. That's it.

> **brandon333 said:**
> Where in ubuntu do I set up sharing for the ps3 to see these files to stream?

You can install SAMBA and setup it to share folders and files in your network. But I have no idea what a PS3 requires to access files and folders in a network.

---

