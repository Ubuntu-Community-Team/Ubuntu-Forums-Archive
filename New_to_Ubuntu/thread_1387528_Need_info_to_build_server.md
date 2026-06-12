---
title: "Need info to build server"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by sylvainrb on 2010-01-22
Hello,

I just need some info on building some sort of server. Here's what I want to do:

A small box (something that'll look like a Mac mini in shape) where I would store my files/media so I can access them from anywhere at anytime. I don't want to use my regular desktop since I don't want to leave it on 24/7. 

My guess is I just need a small motherboard, processor, little memory (how little can I get away with?) and big storage (from 500GB to ~1TB)... All running Ubuntu server!!

So any info is welcome! Thanks!!

---

### Post by cenzorrll on 2010-01-22
i'm using a fit-pc slim and an external two bay hard drive case.  it works amazing, except the processor is a 500mhz amd geode (SLOOOOWWW) but it does exactly what i want (file server, torrent client mainly), and the whole setup uses less than 25watts of power.  there's definitely a lot to be desired from this setup but as a file server/downloader it's perfect (i'd like to set it up as a set-top box also, but it's just way too underpowered)

pretty much anything on a mini-itx board will be low power and small, i personally think the atom is a poorly designed platform (it uses a chipset that was outdated two years ago and you can't update it) but that's pretty much all you can find these days.  the VIA nano kicked the atoms butt through better cpu design before the atom went dual core so I personally would choose the nano for progress sake if you can find a MOBO you like

if it's a server, you don't need a desktop environment (i have one just cause i blow at terminal stuff) my server uses 54mb ram with lxde (desktop environment), xdm, and deluge running, so you don't really need much ram (can you even find a stick with less than 512mb anymore?)

i use vnc when i have to get on and do desktop stuff (not very secure so i would suggest researching some other remote desktop method)

---

### Post by jimmy the saint on 2010-01-22
You might want to consider getting a wireless router that has a usb port.  You can then attach an external HD to it and acheive the same functionality without spending all that money.  Linksys and Asus have both served me well, as long as you are very careful about the version in addition to the model.  If all you want to do is serve files, there is no need to build a new machine when a <$100 router can perform the task just fine.

If you really want to go with a small, dedicated box, though, the new nettops should be ok.  Dell, Asus and a few other companies are putting them out for 3-400 bucks.

---

### Post by sylvainrb on 2010-01-22
> **jimmy the saint said:**
> You might want to consider getting a wireless router that has a usb port.  You can then attach an external HD to it and acheive the same functionality without spending all that money.  Linksys and Asus have both served me well, as long as you are very careful about the version in addition to the model.  If all you want to do is serve files, there is no need to build a new machine when a <$100 router can perform the task just fine.

If you really want to go with a small, dedicated box, though, the new nettops should be ok.  Dell, Asus and a few other companies are putting them out for 3-400 bucks.

But can I run an OS from that external HD through the router and is it as secure (meaning only I can have access to the files and not my roommates or anybody else over the internet)?

Thanks for the info!

---

### Post by steveneddy on 2010-01-22
Look at the link in my sig labeled "World's Smallest Linux Server"

Link here:

[http://www.tonidoplug.com/](http://www.tonidoplug.com/)

Just plug an external HD into this and an ethernet cable and you are ready to go.

$100 plus the HD and you are ready to go.

Easy Peasy.

---

### Post by HermanAB on 2010-01-22
Hmm, you mean something small, like my Eee PC 701 server?
:)

---

### Post by Scunnered on 2010-01-22
**jimmy the saint**

I like the look of your post.  

I want to backup info from my laptop(s) and to be able to access the info from the laptops.  If I adopt this method using an external HD will it need an OS? 

My backup needs are for photographs and OOo documents.

---

### Post by indytim on 2010-01-22
Why not just get an external hd(s)?  Solves the cost issue (vs a new box).  Solves the security - turn it on when you need it, simple... no ops  to contend with....

Just a thought...

IndyTim

---

### Post by 3rdalbum on 2010-01-22
You've got a couple of options.

1. Buy a Mini-ITX motherboard with an Atom or something similar, buy a PSU and case and a hard disk, install Ubuntu Server or Ubuntu Desktop on it and use that to serve files and do whatever you don't want your main computer to do.

2. Buy a NAS and install a hard disk in it. This will use less power, be less complicated and probably be a little cheaper. It's also less flexible - you can basically serve files and possibly download torrents on it.

3. Buy one of those little home theatre media boxes. You know the ones - they plug into your TV and can watch videos off a hard disk or from a network. Some of them have the ability to work as a NAS too, which will be much cheaper than buying a NAS. Possibly use less power and definitely take up less space. You don't have to plug it into your TV either, but it's a good idea so you can watch videos on it (assuming your TV is close to an Ethernet port, or you're willing to run Homeplug or buy a wifi adapter for it).

---

### Post by nothingspecial on 2010-01-22
You need a [[COLOR="Magenta"]dynamic ip address[/COLOR]]("http://www.dyndns.com/") and [[COLOR="Cyan"]ssh[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by sylvainrb on 2010-01-22
@nothingspecial: Doesn't a dynamic IP address come with your ISP. I thought for a server I would have to make a static IP instead.

@indytim: I want to have access 24/7 and just external HD's would rely on my desktop or laptop power and OS to run.

@scunnered: Look at jimmy the saint post. it might be useful for what you need. 

@3rdalbum: After a bit more research and thought, I think option 1 would be best for me. Having a Mini-ITX box will give me more flexibility, even if a little more expensive, I never know what I might want to do with it after...

Looking at newegg (for Mini-ITX):
  Case + PSU                 = $50
  Mobo (onboard video) + CPU = $65
  RAM (512MB)                = $15
  HD (1TB)                   = $100
  Total                      = $230

Could be cheaper with a smaller HD (can always upgrade later!)

Thanks all for info/input!!

---

### Post by fisheater on 2010-01-22
I was interested to read your post - I was also thinking of setting up a server (being linux newcomer - setting up a server seemed like a big task).

My solution was a NAS that runs linux with a great set up easy to use software solutions. Cost is ~400 CDN with 2x 1TB drives.

NAS: [http://www.dlink.ca/products/?pid=509](http://www.dlink.ca/products/?pid=509)

You can set it up as Just a bunch of disks (JOBD: [http://www.raid-data-recovery.net/bunch-of-disks.html](http://www.raid-data-recovery.net/bunch-of-disks.html)) or as a RAID. My set up is RAID 1, I know it is not a backup, but it ensures my data is safe from a disk failure (I have an offsite external HD as backup).

This link is to the big list of programs you can add to the NAS: [http://wiki.dns323.info/howto:ffp](http://wiki.dns323.info/howto:ffp)

General info: [http://wiki.dns323.info/](http://wiki.dns323.info/)

You can set the NAS to have a static IP on your intranet and use your router's DDNS service + dyndns.org (or other) to keep your internet IP up to date.

It is a good options as a headless computer, low energy draw, and can be  set up quick.

Good luck with it.

---

### Post by nothingspecial on 2010-01-22
> **sylvainrb said:**
> @nothingspecial: Doesn't a dynamic IP address come with your ISP. I thought for a server I would have to make a static IP instead.

Yes, you know what I mean. If your isp doesn`t supply you with a static ip address, the site in the link - dyndns (you see where I got confused) can get round this.

---

### Post by sylvainrb on 2010-01-22
> **fisheater said:**
> I was interested to read your post - I was also thinking of setting up a server (being linux newcomer - setting up a server seemed like a big task).

My solution was a NAS that runs linux with a great set up easy to use software solutions. Cost is ~400 CDN with 2x 1TB drives.

NAS: [http://www.dlink.ca/products/?pid=509](http://www.dlink.ca/products/?pid=509)

You can set it up as Just a bunch of disks (JOBD: [http://www.raid-data-recovery.net/bunch-of-disks.html](http://www.raid-data-recovery.net/bunch-of-disks.html)) or as a RAID. My set up is RAID 1, I know it is not a backup, but it ensures my data is safe from a disk failure (I have an offsite external HD as backup).

This link is to the big list of programs you can add to the NAS: [http://wiki.dns323.info/howto:ffp](http://wiki.dns323.info/howto:ffp)

General info: [http://wiki.dns323.info/](http://wiki.dns323.info/)

You can set the NAS to have a static IP on your intranet and use your router's DDNS service + dyndns.org (or other) to keep your internet IP up to date.

It is a good options as a headless computer, low energy draw, and can be  set up quick.

Good luck with it.

That big task of setting up a server is what I'm looking for actually haha!! But it seems that a NAS would give less flexibility than an actual computer. I don't want to be tied down with a small box that can just transfer files over the internet since building a Mini-ITX isn't that much more expensive. 

Time to start saving up some $$$!

---

### Post by earthpigg on 2010-01-22
hi,

i havent read through this whole thread, but i set up something like what you want with standard/cheap off the shelf hardware and plain old ubuntu desktop edition (because my media server is also used as a desktop...).

thread i made a while back:

[http://ubuntuforums.org/showthread.php?t=1314970](http://ubuntuforums.org/showthread.php?t=1314970)

the desktop that i use as my 'server' is nothing special. small formfactor case. another member of my household uses it as a desktop at the same time as it is serving me streaming mp3 files while i am at my girlfriends house.

sshfs means that the folder at my house appears to graphical file managers as a local folder. i can drag and drop files, and they will transfer to or from the server at my house.

---

