---
title: "Salutis Connect where did it go ? E220 thread"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by dickmorrell on 2008-10-21
I wonder if anyone can help. I've been using Rudolf Adamkovic's brilliant Salutis Connect on two of my laptops, built another couple to use Huawei e220 modems with. I have no issue getting connection without Salutis Connect but it's just very "grown up" to have a nice gui and icon to do it with. 

My issue is I grabbed the old version from a repository which now 404s to a site on Apple.com using:

sudo sh -c "echo deb [http://repository.salutis.sk/production](http://repository.salutis.sk/production) ./ >> /etc/apt/sources.list"
sudo sh -c "aptitude update && aptitude install salutis-connect"

Does anyone know (and I have trawled the forums and Google till my fingers bled before posting) where I can get the latest .deb file from ?

Any answers greatly appreciated.

---

### Post by salutis on 2008-10-22
Hello! **Salutis Connect is moved from my own repository to PPA.** Here:

```

sudo -s
echo deb http://ppa.launchpad.net/salutis/ubuntu hardy main >> /etc/apt/sources.list
aptitude update && aptitude install salutis-connect

```

---

### Post by dickmorrell on 2008-11-01
Thanks, now are you going to compile a version for Ibex ? Would be really helpful.

---

### Post by salutis on 2008-11-03
Hm. And is Salutis Connect from Hardy working with Ibex? If yes, then I can move it to Ibex repository.

---

### Post by salutis on 2008-11-25
Salutis Connect is not supported anymore. Use Network Manager instead.

---

### Post by dickmorrell on 2008-11-25
When you say not supported - does this mean no further security revisions or patches for current version for 8.04LTS ? 

I've rolled back 32 of my laptops/PCs from Intrepid to 8.04 because of issues with 8.10 kernel being a piece of crap and also because the new network manager (although impressive and works fine with rndis and e220 devices) doesnt support the e169 dongle that I need to support. The new network manager in Intrepid sees the fact that the e169 is attached and mounted (simple dmesg output) but refuses to connect to the ISP. 

Roll back to 8.04, install Salutis Connect and bingo - just works. 

Can't afford the instability of the 2.4.27 kernel and the non DMA crap that seems to affect slightly older (2005/6) Thinkpads. Need stability and rely on Salutis which to me is hugely important.

Please therefore let me know if you are going to consider fixes/patches if required in the future for Connect or I'll have to stop using that too and just script ppp stuff manually.

As it is it's one of THE most useful tools I've ever used within Ubuntu and a godsend and I thank you for writing it and sharing it with the community.

---

### Post by salutis on 2008-11-25
Thanks for reply. I made Salutis Connect originally for couple of my friends with LTS and they are using it daily. So, it will stay fully functional under LTS as long as possible. Personally I don't own neither E220 nor E169, so I can't develop anything else. Have nice day!

---

