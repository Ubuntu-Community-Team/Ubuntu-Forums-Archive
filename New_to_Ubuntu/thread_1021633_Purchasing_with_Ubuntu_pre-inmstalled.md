---
title: "Purchasing with Ubuntu pre-inmstalled"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by echo314 on 2008-12-25
I am looking at a few vendors, such as Dell and System76, trying to determine which would get me a reliable product. Sys76 looks a bit cheaper than dell, but its also not as big, as far as I can tell. Dell also looks a bit more expensive, but I can't find a desktop with a graphics card, just in their laptop offerings...

My required system specs are not really high, I do fine on my old gateway I got over 7 years ago, which can play StarCraft with its integrated graphics, so I don't need anything amazing. Would those super-compact designs be fine for my needs? Or are we at the point laptops have pretty much replaced desktops, and the extra heat generated is not really a problem like it used to be.  

Any input is appreciated, I'm just trying to gauge what kinda of PCs i should be looking into, and where I should get them. Budget is not really a problem, but I absolutely don't need fancy features. I do just fine on the old single core...its just a bit sluggish. Even on my desktop, with an Athlon 3000+, I have an APG vid card and an 80gb HD, and I manage. Thanks!

---

### Post by jimmy the saint on 2008-12-25
system76 is pretty good and there is even a forum here specifically for supporting their products.  I had no problems with my dell leptops, although I now have a thinkpad that I like.  As far as your needs, you probably can't go wrong if you try to avoid broadcom wireless cards and ati graphics.  If you can, get a system with an atheros wireless card.  Other than that, you should be good with pretty much anything that you are looking at.  Vista pushed the hardware to a such a level that you can get a bargain basement box now and scream with linux.
Good Luck

JTS

---

### Post by tuxxy on 2008-12-25
I agree you would be good with a Dell but prefer a laptop to netbook as find them sluggish, also nVidia graphics are much better if you can find one :)

---

### Post by echo314 on 2008-12-25
Thank you for the input Jimmy and Tuxxy. I agree, I think a netbook would be a poor purchase. I'm looking for something that I will get more general purpose power out of, which I will most appreciate. I'm not upgrading for any specific purpose, but better driver support would be a huge plus.

---

### Post by cdwillis on 2008-12-25
You can get a desktop pc or a laptop with the similar specs and have the added mobility. I'd go with the laptop. Personally I'm thinking about buying a Dell Studio 15n laptop preloaded with Ubuntu.

[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs]("http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs")

---

### Post by echo314 on 2008-12-25
It terms of video memory, how much would be sufficient? I absolutely won't be playing any of the new top notch games, but I like to play ones from a few years ago that use 3d, some of which are kinda intense (ST Bridge Commander). I guess I'll want to play SC2. Would 128MB be sufficient? RIght now in my desktop i have an ATi card with 512MB, but its APG and the speeds are slow, it just had a lot of memory. I'm wary of getting less memory, what can I make do with?

---

### Post by Ng Oon-Ee on 2008-12-25
Isn't 256MB bottom-of-the-line for graphics cards these days? Just purchased my laptop a couple of months back with NVidia 9300M, 256MB discrete memory, I didn't really see any laptops offering 128MB, though of course most of them didn't even have a GC.

---

### Post by Shannon_VanWagner on 2008-12-25
I purchased the Dell Inspiron 530n Desktop and plugged in an NVIDIA GeForce 9400GT PCIe video card. This machine is plenty fast, smooth graphics, and is awesome!!

[Here's the writeup]("http://healthysystem.blogspot.com/2008/11/dell-inspiron-530n-nvidia-9400gt-ubuntu.html") with pictures that I made on my blog.

I appreciate that system76 sells mainly GNU/Linux machines, I've just never purchased from there yet.

As for my new Dellbuntu machine, I ended up installing Ubuntu 8.10 fresh because I didn't like the way Dell partitioned the hard drive(/home directory not separate), and I bungled up the video drivers at first by installing from a script instead of doing it the easy way and using the restricted drivers utility.

Once I installed Ubuntu 8.10, the nvidia graphics drivers showed up in the restricted drivers manager - it's been smooth sailing from there.

Something else I had to do was install DVD/Multimedia support - [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid") made that easy though.

I am currently as happy as a clam with our new Dell GNU/Linux machine!!!

Congratulations on your freedom!!

Go GNU/Linux!!!
Shannon VanWagner

---

### Post by mkvnmtr on 2008-12-25
I have an old laptop that came with 256Mb and I added another Gig. I run HTop a lot and I run between 275 MB and 350 Mb on my normal usage. Thats 2 or 3 browsers, a torrent, a game, and a couple of other things. If I also use Gimp I will go up to 775 or 800 Mb.I don't think I will ever need 2GB on Ubuntu. I have never used my swap partition. Maybe there is some other heavy memory using apps that I don't use.

---

### Post by tuxxy on 2008-12-25
> **Shannon_VanWagner said:**
> I purchased the Dell Inspiron 530n Desktop and plugged in an NVIDIA GeForce 9400GT PCIe video card. This machine is plenty fast, smooth graphics, and is awesome!!

As for my new Dellbuntu machine, I ended up installing Ubuntu 8.10 fresh because I didn't like the way Dell partitioned the hard drive(/home directory not separate), and I bungled up the video drivers at first by installing from a script instead of doing it the easy way and using the restricted drivers utility.

Once I installed Ubuntu 8.10, the nvidia graphics drivers showed up in the restricted drivers manager - it's been smooth sailing from there.


Thats a nice laptop and what else do expect from nvidia :p btw your other option to installing fresh 8.04 would be to shrink the Dell partition and create and assign a new one to /home but would probably be quicker with fresh install anyway :)

> **mkvnmtr said:**
> I have an old laptop that came with 256Mb and I added another Gig. I run HTop a lot and I run between 275 MB and 350 Mb on my normal usage. Thats 2 or 3 browsers, a torrent, a game, and a couple of other things. If I also use Gimp I will go up to 775 or 800 Mb.I don't think I will ever need 2GB on Ubuntu. I have never used my swap partition. Maybe there is some other heavy memory using apps that I don't use.

I agree you wont need 2GB for them activities you listed I think you would get away with 1GB however if you decided in the future you wish to use some virtualisation software for example then you would be thanking yourself later on for getting 2GB ;)

---

### Post by echo314 on 2008-12-25
The best laptop I can see from Dell only has 256mb graphics memory. I'm just worried this won't be enough if I ever decide I want to play a modern game such as SC2. Should I be worried? Should I find a 512?

---

### Post by oldos2er on 2008-12-25
I bought a Dell XPS 410 desktop in summer of '07, not long after Dell first began selling Ubuntu preloads (it came with 7.04 installed). Since then I've upgraded through each new version of Ubuntu, and a few other distros too. It came with an Nvidia GeForce 7300 LE with 512MB, and I've never had problems with getting the Nvidia drivers working. I just recently flashed the BIOS with a Dell-provided Linux program, and it worked fine. Overall, I'm happy with my purchase.

---

### Post by echo314 on 2008-12-27
Any more input to be had? I'm still curious about why I can only get 256mb video memory tops, is that really all thats required newer games?

---

### Post by jimmy the saint on 2008-12-27
The thing is, Dell is not looking to make screaming Linux desk/laptops.  They want to get the linux market, but not piss of MS by switching too many people.  You will likely get general usage laptop preloaded with Ubuntu, but not a screaming fast high end one.  One reason for that is they figure if someone is so cheap as to prefer linux over MS they must be too cheap to spend $$$ on a super capable machine.  

Also, most linux boxes are geared more towards general/work use ayway.  Let's be honest here, if you are buying a gaming rig, you use windows.  There are more/better games to be had.  That will change as time goes on, but from a sellers perspective, you don't sell now based on what will be usefull in three or four years, especially not if you are selling computers.

If you do want a screaming laptop, buy one and then install Ubuntu.  That said, I have an nvidi quadro nvs140.  That's pretty bottom of the line as far as mobile processors go and I do just fine with most linux games.  It won't play any of the modern games, but then I didn't buy it to be a super gaming rig.

Now I'm just rambling.  I hope that helped a little.

JTS

---

### Post by SamNSane on 2008-12-27
> **echo314 said:**
> Any more input to be had? I'm still curious about why I can only get 256mb video memory tops, is that really all thats required newer games?

It seems that Dell tries to steer potential customers toward particular types of systems they think the customers need. If you click home/home-office I think you are shown consumer-grade systems. Try clicking the small business link. If you look at Latitudes and Precision workstations you're going to have lots of options for more capable graphics subsystems -- up to 2 gigabyte graphics subsystems for graphics workstation class notebooks.

Of course the types of cards that are engineered for heavy OpenGL type graphics work are more expensive. But you'll also find that Latitudes and Precisions are, by and large, more sturdily built than the consumer grade notebooks. In general the business class desktops are also better built and easier to service than the consumer grade desktops.

There's not always a huge price differential. If you choose carefully you can sometimes get a much "better" system for roughly the same money or only slightly more.

When I say "better" I'm obviously talking about a value judgment that is going to be seen differently by different people. So what I really mean is that looking at the business options just gives you some more choices so that you have a better chance of coming up with a solution that's more narrowly tailored to your wants.

---

