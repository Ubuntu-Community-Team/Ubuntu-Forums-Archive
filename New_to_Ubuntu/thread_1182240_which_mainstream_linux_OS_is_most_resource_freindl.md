---
title: "which mainstream linux OS is most resource freindly"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Meow27 on 2009-06-08
hi, i have an old think pad T22, and i want to update it with a newer version of Linux

now ill get to the point. which os would be most friendly to a 256mb machine that is a mainstream one 
ubuntu
fedora
opensuse
mandriva
pclinuxos
debian
(others that im not aware of too)
i preferably would like a distro that uses apt by default.
i would like to also mention that im not looking for damnsmall or other minimalist distros

thanks in advance

---

### Post by handydan918 on 2009-06-08
I suggest downloading a bunch and trying them out. Keep in mind that a live cd will always run slower than a hard drive install. 

Your list omits one of the best Debian/apt options...
Mepis. It WILL run on 256 megs of ram, but the truth is that nothing will be really snappy on that hardware.

---

### Post by halitech on 2009-06-08
I've beening using the info here to install lately and have had decent results even on a P300 with 192meg of ram

Debian + XFCE4 minimal install
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

if you want apt you can probably trim your list of fedora, opensuse, mandriva as they use yast, yum and others instead of apt.

---

### Post by louieb on 2009-06-08
The T22 can hold up to 512 MB of PC100 (PC133 will also work) ram.  
Check out the T22 forum at [ThinkPad Forum]("http://forum.thinkpads.com/") also check out the [T22]("http://www.thinkwiki.org/wiki/Category:T22") on [ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")

Look (PC100 or Pc133) 144 pin sodimm make sure it is low density. You want 2 x 256mb memory modules.  

Saw some 256mb modules on eBay for less that $10. You'll be a lot happier with how it runs no matter which distribution you go with.

---

### Post by Hund on 2009-06-08
I can recomend [CrunchBang Linux](http://crunchbanglinux.org/) and [U-Lite](http://u-lite.org/).

---

### Post by RedSquirrel on 2009-06-08
You can run Ubuntu on that if you install a command-line system and build up from there.

[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

That tutorial installs icewm, but you can use whatever you like. The **xfce4** meta package is handy for installing Xfce, or you can try fluxbox, openbox, etc.

---

### Post by QIII on 2009-06-08
I actually had xubuntu working on an ancient laptop with 168Mb after using the alternate install disk.

That was 7.10.

Unfortunately, I was unable to upgrade beyond that because of changes to X, which were incompatible with the graphics hardware on the machine.

---

### Post by Gen2ly on 2009-06-08
> **halitech said:**
> I've beening using the info here to install lately and have had decent results even on a P300 with 192meg of ram

Debian + XFCE4 minimal install
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

if you want apt you can probably trim your list of fedora, opensuse, mandriva as they use yast, yum and others instead of apt.

+1

Good tip.  I have a 300mhz cpu and 384MB of ram on one computer and Debian/Gnome was as far as i could go.  With that ram you got, this is a good advice.

---

### Post by powel212 on 2009-06-08
I run Ubuntu 8.10 on my old pentium 733mhz with 512m ram

you can just do the regular install and then once it's done you can disable some of the startup programs and end up with a pretty light system without a lot of trouble and have acces to a huge spectrum of mainstream features. 

Powel

---

### Post by Meow27 on 2009-06-08
> **louieb said:**
> The T22 can hold up to 512 MB of PC100 (PC133 will also work) ram.  
Check out the T22 forum at [ThinkPad Forum]("http://forum.thinkpads.com/") also check out the [T22]("http://www.thinkwiki.org/wiki/Category:T22") on [ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")

Look (PC100 or Pc133) 144 pin sodimm make sure it is low density. You want 2 x 256mb memory modules.  

Saw some 256mb modules on eBay for less that $10. You'll be a lot happier with how it runs no matter which distribution you go with.

the reason i said 256, is because 75% of the itme, the biosa doesnt recognise the other module. though i DO have two 256mb cards in there.

---
i initially asked this question because the newer versions of gnome seemingly consume ALOT less ram. is it just me?

---

### Post by fluxlizard on 2009-06-09
I have a 10 year old laptop (IBM thinkpad a21m 700 mhz, 4mb video card, 256 mb ram) that runs pclinuxos gnome edition just wonderfully. No compromises either- runs the latest softwares (firefox, open office, gimp, bluefish, etc) with a full gnome desktop and synaptic full of thousands of the latest apps available for the taking. Boots quickly and everything opens quickly too. It set up real easily too- even autodetected my wireless card and network printer.

I use ubuntu on my 3.2ghz x2 4gb ram 756 mb video card desktop because it is sort of the mainstream of linux, but I often wonder why it isn't more nimble than it is compared to my old laptop running pclinuxos gnome edition considering the huge power gap between the machines...

---

### Post by snowpine on 2009-06-09
Definitely start by trying Debian. It is the daddy of apt-based distros, and can be very friendly towards older hardware (depending on how you set it up). Debian is a more flexible distro than a lot of people think. You have your choice of stable, testing, or unstable branch and lots of windows managers to choose from. Personally I think the "sweet spot" is Debian testing (squeeze) with LXDE.

Other apt-based distros I recommend for older hardware include AntiX (mepis+icewm/fluxbox), sidux (debian unstable+xfce/fluxbox), and of course CrunchBang (ubuntu+openbox).

Good luck!

---

### Post by halitech on 2009-06-09
> **Dirk.R.Gently said:**
> +1

Good tip.  I have a 300mhz cpu and 384MB of ram on one computer and Debian/Gnome was as far as i could go.  With that ram you got, this is a good advice.

lowest I've ever gone was a tecra 550cdt with a P266 with 96meg of ram using those steps but I found it slow so installed LXDE instead and found it better. I've since dumped it and now have a Sony Viao thats a P2 500 with 128 meg and it ran much better.

---

### Post by anticapitalista on 2009-06-09
I carried out a test in VB set to 256 MB RAM comparing antiX-M8-base with the latest Ubuntu-alternative base install.

Installation time: antiX installs much, much faster.

Configuration: antiX-base comes with X and fluxbox already set up. This has the advantage of saving time, but the disadvantage of lack of choice. antiX also comes with a text editor (leafpad), 2 browsers (iceweasel and links2), epdfview, grsync, mc, rox-filer, roxterm, urxvt, gparted, ceni (networking), a meta-installer as well as the MEPIS tools. I mention this as they are not installed in the Ubuntu-alternate base install.

Boot time after install: Ubuntu-base boots faster c15 secs, antiX took about 20 secs.

RAM usage after install: antiX uses less resources even though Ubuntu-base has less apps. antiX-base idle on boot c25MB RAM, Ubuntu-base idle c35MB RAM. Once I installed the apps already in antiX-base to Ubuntu-base, Ubuntu-base RAM usage at idle was c45MB RAM.

General responsiveness: Both were snappy. No noticable difference.

Now this quick test is not conclusive and YMMV on a different box. However, it does seem that Debian base (on which antiX is built) is less RAM intensive than a Ubuntu one.

---

### Post by Bölvaður on 2009-06-09
I'd say that Arch is mainstream but you'll have to put sweat and blood into it to set it up exactly like you want it. But that might be the deal breaker for you :P  Beginning with nothing but command line and barely any programs (no user programs like firefox or opera at all) and build up from there.

But yeah Debian ftw.

---

### Post by handydan918 on 2009-06-09
> **anticapitalista said:**
> 
Now this quick test is not conclusive and YMMV on a different box. However, it does seem that Debian base (on which antiX is built) is less RAM intensive than a Ubuntu one.

Good assessment, Anti. This matches my observations of hard drive installs as well. A pure Debian base seems noticeably quicker than any Ubu install I have tried.

---

### Post by snowpine on 2009-06-09
Great post, anticapitalista! AntiX is very happy on my old 128mb laptop.

---

### Post by LewRockwell on 2009-06-09
I'm going to throw this in for our worldwide-viewing audience.

Here, we're two pages into a discussion about the various pros and cons of *nix distros. The original post suggested that they were not interested in "minimalist distros" and so the discussion has centered around other alternatives.

Personally, when you have lemons, you should at least TRY the lemonade. I have a couple dozen distros slung around here and can attest to Damn Small Linux(50mb) and Puppy Linux(100mb) running on just about anything(here I have DSL running on a 1997 gateway laptop with 150mhz processor, 224mb ram, 3gb hard drive, pcmcia lan card).

I would also recommend TinyMe(based on PCLINUXOS) except that it's broken right now(June2009) so if you're reading this sometime in the future you might want to check that distro for current availability.

Again, this post is NOT directed towards the OP, but instead seeks out future audiences.

Never give up, never surrender!

---

### Post by snowpine on 2009-06-09
I agree with LewRockwell (I am a huge SliTaz fan personally) but I limited my previous post to apt-based distros per the OP's request. If the OP is willing to look beyond apt, then Arch blows them all away obviously. ;)

---

### Post by blackxored on 2009-06-09
Well, restricting myself to your list, I'd say that debian and fedora will run pretty well with 256 MB RAM. At, until some point, ubuntu will do it fine, assuming you're not doing too-heavy tasks. And about your apt default, well use debian. Or a debian-based one. Apt has been ported to rpm quite a long time ago, and yum will be transparent to you (as opossed to me when packaging :))

---

### Post by fluxlizard on 2009-06-09
> can attest to Damn Small Linux(50mb) and Puppy Linux(100mb) running on just about anything(here I have DSL running on a 1997 gateway laptop with 150mhz processor, 224mb ram, 3gb hard drive, pcmcia lan card).


I've found that pcfluxboxos (again pclinuxos based) will run on anything that dsl or puppy will run on, and you get synaptic and can run all the latest softwares like gimp and open office on old machines as well and they run fine.

Last year I was running it on a 266 mhz 128mb ram and I had a sweet start menu bar app on top of fluxbox(can't remember the name of it now) and had a nice zooming icon dock thingie (sorry can't recall the name of that one either) going on the desktop, had bluefish, gimp, firefox, tunapie and xmms playing internet radio all at the same time while I was creating a photo heavy website for a public school system and everything ran just fine. Wasn't the fastest thing in the world, but wasn't uncomfortably slow either.

Puppy and dsl are fun to fool around with, but they aren't standard in the way they do things, and have limited softwares in their repos. pcfluxboxos or minime or tinyme are much better, pclinuxos gnome edition is best if you have 256 mb ram to play with.

---

### Post by oldos2er on 2009-06-09
Another distro to consider is Vector Linux. It is based on Slackware, which is a solidly stable distro, but Vector is much friendlier for the new (or newer) Linux user.

 They offer a few different versions, the hardware requirements of which are listed at the bottom of the page here: [http://vectorlinux.com/products](http://vectorlinux.com/products) .

 Their forums are every bit as friendly as Ubuntu's, but with much less traffic.

---

### Post by toddr on 2009-06-09
I have an old Dell laptop with a 400mhz P2 and 256mb ram. It runs puppy linux like a champ. I use this as a production machine to record with using Audacity with nary a glitch. I would also suggest VectorLite. Both of these would run very fast on your machine. It has been my experience that the heavier distros would be very slow. If you want to get dirty, try building it from scratch, using Debian or Arch.

---

### Post by Meow27 on 2009-06-09
ove tried debian lenny on my laptop. it reminds me of Hardy. just is alot more resource friendly. i dont like it for the following reason

- nautilus doesn't have a normal browser

---

### Post by louieb on 2009-06-09
> **fluxlizard said:**
> I've found that pcfluxboxos 

[PCFluxboxOS:]("http://pcfluxboxos.wikidot.com/")  +1

---

### Post by Arup on 2009-06-09
Ubuntu with PC Man as file manager instead of Nautilus reduces the mem footprint by around 80 to 130mb.

---

### Post by abn91c on 2009-06-09
try dreamlinux, here are the hardware requirements from their website [http://www.dreamlinux.com.br/download.html](http://www.dreamlinux.com.br/download.html)

System Requirements(minimal): XFCE: Pentium III 
 128 MB RAM HDD or SDD/FlashDrive 1GB free.

---

### Post by CJ Master on 2009-06-10
+1 for crunchbang linux. Seems to fit your needs fine, and it's a very sleek OS.

---

### Post by Carpentr on 2009-06-10
My uncle has been testing out a few Linux distributions and he said some good things to me about Puppy Linux. He mentioned that it ran really good on slow computers as well ; He said he installed it on a very old computer he had and it worked like a charm.

If you want to go even smaller than Puppy Linux's 90mb or so install for the OS you could try DSL which is about 50mb.

---

### Post by halitech on 2009-06-10
> **Meow27 said:**
> ove tried debian lenny on my laptop. it reminds me of Hardy. just is alot more resource friendly. i dont like it for the following reason

- nautilus doesn't have a normal browser

what do you mean it doesn't have a normal browser?

---

### Post by sudeepk on 2009-06-10
Puppy linux work's very well. It has all the features a user needs including a writer. Internet works fine on it. Its very suitable for low configuration systems. But i dont recommend it. If you want to experience the real linux go for debian or gentoo or redhat.

---

