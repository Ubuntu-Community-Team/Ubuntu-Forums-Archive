---
title: "Slow network?"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by Jawshie on 2008-04-16
I am on campus and we are behind a proxy. Naturally, this is screwing everything up but I am able to host my servers for the dorms at least. I host songs from on-campus bands on it (with their permission of course) through a vsftpd server and through Samba as well on my Desktop. Anyways, last week I took my computer to a LAN party and thats when problems started occurring. I had to switch all my configurations to not use the proxy. When I then started using the other network, every time people try to access my ftp and download stuff, it goes extremely slow. Rather, it doesn't even try to download the files but it says it is downloading and gives us massive amounts of time left such as 198 hours to complete or something (both protocols). This is ridiculous for 10M songs. The odd thing is is that they seem to be able to list the contents of the server fairly quickly.  I'm back on the proxied network now and nothing has changed. I sent every proxy setting back the way it was.
Before the problem started, in Firestarter I had a network interface called "wmaste" or something like that. Now, its gone. I noticed that whenever I was uploading something, this interface would be the one uploading (according to Firestarter) in conjunction with my eth0. I also think I may be missing a vmware adapter or two because the list seemed larger than it is before. Now all I have is my wireless (wlan0), eth0, vmnet1, vmnet8.

Any ideas what I can do?

edit: Its 7.10.

---

### Post by wormser on 2008-04-28
I would like to know what that wmaste network device is.  Does anybody have an idea.  Google was no help.

---

### Post by HunterThomson on 2008-06-06
> **wormser said:**
> I would like to know what that wmaste network device is.  Does anybody have an idea.  Google was no help.

Ya, what is wmaste??

---

### Post by Sam Lars on 2008-06-06
> **HunterThomson said:**
> Ya, what is wmaste??

It's an interface set up by the driver, I think it's actually wmaster0, I guess it doesn't fit there.

Is this problem with both Ethernet and wireless?

---

### Post by HunterThomson on 2008-06-07
> **Sam Lars said:**
> It's an interface set up by the driver, I think it's actually wmaster0, I guess it doesn't fit there.

Is this problem with both Ethernet and wireless?

I don't know if it is really "problem" or not... I just want to know what it is. 

I am using a Ethernet connection and have turned of my wireless and it is still there and still using like 22KBs.

---

