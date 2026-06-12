---
title: "Setting up 2 servers from old PCs"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by dragonpimpsta on 2010-07-13
Hey. I have two old PCs that I decided i want to setup to run as my own personal servers. There is no problem yet I'd just like advice before I waste time and money. I've never setup a server and I'm new to Linux based systems too, so I figured this forum was appropriate.

**PC #1: **I'm getting it soon from my sister, but I believe it's a Dell Dimension (maybe 3000 or lower-not sure). It runs fine so I'm sure it's memory and processor are decent for running as a server. It's harddrive has at least 20gigs which is fine for me, and i think she might have an external drive as well. **Goal:** I want it to be a File/Web server to host storage for a bunch of files for me while i'm at school and also maybe host a few personal websites?

**PC #2:** This one has been in my basement for approximately 13 years. It's a Packard Bell Platinum 2220. It has as much memory as you can possibility put in it I believe. Idk about the processor. It's harddrive is a mighty 2gb. I'm not sure if It will even be possible to install Ubuntu Server software onto it. The bios/motherboard is so old it won't let me boot from the installer disc so i'm planning on attaching the harddrive to the slave slot of the other (newer) PC to install ubuntu onto it. **Goal:** I want to use this server to run a torrent program because while i'm at school I won't be able to run them (I swear I have good intentions.) Since the drive is only 2 gb i was planning on having it save all files to a network connection to the other server. Is this is a good idea? Are there holes in my plan?

**Summary:** 
That's my plan. I haven't run into any major problems as of yet, but I'd like advice if possible or warning if something above that i'm doing is stupid/pointless etc.

Thanks.

---

### Post by mbzn on 2010-07-13
Possible, yes. You might have to look into a smaller distro for pc2, check out (damn small Linux) I've heard good thing about is. I don't get the 'running a dedicated pc for torrents with a 2gig hdd' part, but that's your baby...

Try reading up on the alternate install cd's for Ubuntu witch may be the only way on older pc's.

Good luck

---

### Post by gr4nf on 2010-07-13
For the ancient one I would recommend either a Debian install from floppy:

[http://linux.simple.be/debian/etch/floppy](http://linux.simple.be/debian/etch/floppy)

or, for a fun and really very educational experience, try for a Gentoo install. That would make a good day-long project.

As for the torrent, I would recommend just doing it on that newer machine, as the 2220 has 32 megs of memory in it, if my research is correct, and that will just be painful for doing long downloads and file transfers, or anything, really.

Ubuntu server edition will run very well on that dimension of yours. Be sure to get an ftp package of your choice for file serving and apache2 web server for personal web sites.

---

### Post by dragonpimpsta on 2010-07-13
Yeah i know my dedicated torrent downloading server sounds kinda strange. See my school will disable my internet connection if i even run P2P programs nomatter what the purpose. I also might get an incidental fee. Since It's a 2 day drive home from school where I can safely torrent i thought It'd be a good idea to be able to remotely use torrent programs.

I chose to use PC2 for this because I didn't want to hog resources on the file/web server for such a low priority task. Since there isn't enough room to store downloads that will be bigger than the capacity of the HD I was hoping i could download to PC1, but using the torrent software from PC2... Maybe I just don't want to waste PC2. lol.

GR4NF: I think the Pl 2220 has more memory than that. I saw all 4 slots were full. I guess i shouldn't be shocked if each one is only 8mb and it totals 32mb. 

Thanks mbzn & gr4nf for your suggestions. I will look into this smaller size software. 
__

---

### Post by mbzn on 2010-07-13
That makes sense, be sure to read through the Ubuntu server guide
here[http://www.google.com/url?sa=t&source=web&cd=2&ved=0CBkQFjAB&url=https%3A%2F%2Fhelp.ubuntu.com%2F9.04%2Fserverguide%2FC%2Fserverguide.pdf&ei=tug8TKL8GIGclgezw5iJAw&usg=AFQjCNHHiygn5_2a3DJ7OhOmUfMC7f_lkw]("http://www.google.com/url?sa=t&source=web&cd=2&ved=0CBkQFjAB&url=https%3A%2F%2Fhelp.ubuntu.com%2F9.04%2Fserverguide%2FC%2Fserverguide.pdf&ei=tug8TKL8GIGclgezw5iJAw&usg=AFQjCNHHiygn5_2a3DJ7OhOmUfMC7f_lkw")

---

### Post by lkraemer on 2010-07-14
Another option that you might want to check out is FreeNAS.
While it's based on FreeBSD, it works great.  It can even boot from
USB, CDROM & Floppy for Configuration storage, or Compact Flash by
using it as an Embedded system (IDE to CF Adapter is needed = $3.xx).

[http://www.freenas.org](http://www.freenas.org)
[http://freenas.org/documentation:setup_and_user_guide](http://freenas.org/documentation:setup_and_user_guide)
[http://sourceforge.net/apps/phpbb/freenas/index.php](http://sourceforge.net/apps/phpbb/freenas/index.php)

lk

---

### Post by zaphod777 on 2010-07-14
for pc2 just connect a USB HDD or buy a cheap large HDD you should be able to find a 40 or 80 GB drive cheap 1TB drives are not too expensive either. unless you are running a high traffic web site you can run it all from pc1. Your ISP will probably be your bottle neck.

---

### Post by tarps87 on 2010-07-14
I can't find the full specs for the Packard Bell Platinum 2220 but here are the requirements for the server install
[https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html](https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html)

I would recommend a server install on both and you will probably get away with it on the second PC due to the small amount number of processes required for a dedicated torrent server, although disabling other non-required processes would be a good idea.

In my opinion it's not work installing something like DSL (Damn Small Linux) as you will spend more time customising it to become a efficient server and there is no need for a GUI on a server.

On thing you will need to work out is were the resource limitations lie, now depending on the spec of PC1 I am willing to bet that it will be the network that is the limiting resource, keep in mind that copying files across the network form the torrent server to the file share will also effect the file shares performance (network traffic and drive activity).

You can always migrate the torrent services to a second pc if you find connection issues.

Also you will what to check about a fixed IP or a domain name company that can cope with dynamic IP's, fixed IP will more than likely be the cheapest

---

### Post by dragonpimpsta on 2010-08-14
Maybe I should have started a new thread, but I just ran into a problem/question.

My ubuntu server is setup as dhcp and i can connect to it from my laptop running ubuntu, so i've been putting files on it, and organizing them.

I should setup static though right? Once i leave for school and my server is here in this different city will i still be able to connect to it? I was looking at guides for setting up static ip, and the ip I would use is 192.168.0.103 which is how my linksys router had it setup. That only works inside of my house though right? I want to be able to connect to it from school (a different city) so how should I do that?

I'd  also like to be able to connect to it from windows xp as well if possible :-o

I'm a complete ip noob. lol. Thanks for any help in advance

---

### Post by Jazzy_Jeff on 2010-08-14
Looks like the maximum memory for that Packard Bell is 128 mb. As for getting a bigger hard drive, I don't know how big you can go on it since it is so old.

---

### Post by zaphod777 on 2010-08-14
> **dragonpimpsta said:**
> Maybe I should have started a new thread, but I just ran into a problem/question.

My ubuntu server is setup as dhcp and i can connect to it from my laptop running ubuntu, so i've been putting files on it, and organizing them.

I should setup static though right? Once i leave for school and my server is here in this different city will i still be able to connect to it? I was looking at guides for setting up static ip, and the ip I would use is 192.168.0.103 which is how my linksys router had it setup. That only works inside of my house though right? I want to be able to connect to it from school (a different city) so how should I do that?

I'd  also like to be able to connect to it from windows xp as well if possible :-o

I'm a complete ip noob. lol. Thanks for any help in advance

here is a lot of the official server documentation 
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

you will need to set a static ip here is the info here
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

To access the server outside of your network you will need to configure a vpn server. 
[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

however your ip scheme is pretty common and you can't vpn to a server if both networks have the same ip scheme so you might want to change yours on your router to 192.168.8.x or somthing like that.

see what you can do then post if you have trouble.

---

