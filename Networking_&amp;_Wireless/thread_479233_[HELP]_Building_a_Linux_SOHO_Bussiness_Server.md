---
title: "[HELP] Building a Linux SOHO Bussiness Server"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by low man on 2007-06-20
Hi guys,

I am new to Linux.
I want to build a computer server based on linux for my SOHO based on approximately 5 desktop(wired LAN) and 5 laptop(wireless LAN).

At the moment i am using Linksys Wireless Router(4 LAN Port) and wireless print server from Linksys as well. Connected to ADSL connection through a wireless ADSL modem, even though the connection from the modem to my router is on RJ45(can't trust wireless in this yet.....)

Here's what i need on the new Linux server:
1. File storage for the business application
2. Mail server (to serve internally and as a gateway mail server, checks for antivirus, spam and malicious softwares)
3. VPN connection (available to seeks data and print from remote location)
4. Printing service (this is for LAN service, wired and wireless)
5. Bandwith limiter for designated IP's, whereas clients will have less speed than admin IP's (some staff get's me headache since they are using loads of bandwidth for downloading softwares on working hour).

Here's my question:
1. What hardware should i use for this matter? The newest or what? Is there any key point i should check on buying hardwares for linux server.
2. One big capacity HD or multiple HD for each clients for convenient access?
3. Does KVM switch works under linux as well? (Don't want to but extra monitor and kerboard+mouse..... Hehe)
4. What Linux should i use? Is there any one solution linux to all this? (By using linux here, i mean coz it's free.....)
5. What to do and how to setup.
6. Cheers for the help.

---

### Post by hartz on 2007-06-20
Hi Low man,

I think you need to take this problem one step at a time.  Your questions are broad and open, so they are difficult to answer.

Maybe break up the problem into smaller pieces and ask pointed questions in separate threads.  That way you will find many people who have knowledge of each single item, and will get many useful answers.

---

### Post by tturrisi on 2007-06-20
> **low man said:**
> 

Here's my question:
1. What hardware should i use for this matter? The newest or what? Is there any key point i should check on buying hardwares for linux server.
2. One big capacity HD or multiple HD for each clients for convenient access?
3. Does KVM switch works under linux as well? (Don't want to but extra monitor and kerboard+mouse..... Hehe)
4. What Linux should i use? Is there any one solution linux to all this? (By using linux here, i mean coz it's free.....)
5. What to do and how to setup.
6. Cheers for the help.
1. No need for the "newest" hardware, but a newer system will perform better if server under heavy load.  I recommend a P4 2 GHz minimum & at least 512 ram.  This would be the base for a great system.

2.  One large hd partitioned neatly will suffice.

3. Yes, kvm switches will work, they are OS independant.

4.  My preference would be do a Debian net install of base system only, then add desired packages.

5. post this in the servers forum.

6. smilies here.

---

### Post by jdbg on 2007-06-27
> **low man said:**
> ...
At the moment i am using Linksys Wireless Router(4 LAN Port) 
......
3. VPN connection (available to seeks data and print from remote location)

if I may add something to this question - how can I do a VPN setup on my server?

---

### Post by t4thfavor on 2007-06-27
Plenty of info on this forum for server setup. Though I would be glad to help you, your questions are much to broad for one thread. First you are going to have to ask what services you will need for each one of those questions. i.e nfs, or samba for shares.  When you figure out what you want to use, you can start asking about how to set them up.

I happen to like Ubuntu server if your a newbie, since its rediculously easy to install and configure the things you are looking for.

As for hardware, for 5 users, you really dont need anything special. You can probably use an old pIII500 with 512MB ram. I personally use a Dual PIII 600 with 640MB ram to do all that +more.

And at home I use a single PIII600 with 128MB ram and that is perfect for about 6 users.

---

