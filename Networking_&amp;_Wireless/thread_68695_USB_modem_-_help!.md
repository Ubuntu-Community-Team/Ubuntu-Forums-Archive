---
title: "USB modem - help!"
date: 2005-09-24
forum: Networking &amp; Wireless
---

### Post by predator on 2005-09-24
Hi everybody,

Well 2 days ago I installed Ubantu "badger release" 5.10 preview or whatever it is.. now I wish to setup my modem. Unfortunately it's a USB modem, a D-LINK DSL200 (rev B1). 

I *know* that usb modems are a pain to setup under linux, and would be better off with a "real" DSL modem, but I would like to give it a try before giving up and throwing away $100 for a new modem. 

I know a few small things about Linux, but really a n00b when it comes down to it. 

Now I've read a few things on how to fix it, but they're all saying "use apt-get to get such and such" .. This is all nice and fine, but slight problem, if your internet connection is not working - how do you download software or drivers  :???:

Thankfully though, I can use XP to download things, and I've worked out to share my NTFS partitions in Ubuntu.. so i can at least transfer things across doing that.  

so ok, I have done some reading around, and I realise I need the eci-adsl drivers. I have downloaded these.. extracted eciadsl-usermode-0.10-nortek-alpha.tar.gz to a directory, and it says to run "eciadsl-config-tk".. so I do this, and it comes up with errors..  ](*,) 

it talks about typing "make" and "configure" in the INSTALL doc but i don't seem to have any of those tools installed. Nor can I download them without an internet connection  ](*,) .

So how do I install the damn things, so i can go through the rest of a guide I have on how to get it working with my ISP ? 

Help!

---

### Post by GTvulse on 2005-09-24
[BTW, this posting of yours belongs to the Breezy Badger's Development forum, or in the worse case the Hoary Hedgehog Hardware support forum, Warty is old, old, old. Please check the forum your posting in next time  :-P ]

Here's a rundown:

[list]
[*]You must install the "build-essentials" package from the installation CD. It is not installed by default.

[*] Go to the project site: [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/) and grab the **latest** version, v0.11 and the firmware files. Make sure to examine the modem database to know the precise firmware file needed for your particular modem model. Copy them to your Linux partition.

[*] Unpack the sources: ```
tar zxf eciadsl-blah.tar.gz
```

[*] Compile and install it: 
```
cd eciadsl-blah
 ./configure --prefix=/usr
make
sudo make install
```

[*] Copy the firmware file to its place: ```
sudo cp fimware_file.bin /etc/eciadsl
```

[*] Configure the driver as you described in your post.

[*] Start the driver: ```
sudo eciadsl-start
``` If you are connected, then you can go to the advanced part.

[*] Copy rc.adsl to the init scripts directory: ```
sudo cp rc.adsl /etc/init.d/eciadsl
```

[*] Install in the boot up process: 
```
sudo update-rc.d eciadsl defaults 8 90
```

[/list] 

And you are done. Mind you, the boot up code is not particularly clean. One should rather install the init script in the rcS.d directory but I haven't bothered to figure out how to do it with the debian system maintenance scripts yet. :roll:

---

### Post by predator on 2005-09-24
Thank you *so* much.. 

I'll just give it all a try now... and post up how I go


and mods can move this if they need.. I just realised that I am talking about 5.10  NOT 4.10 \\:D/

---

### Post by predator on 2005-09-25
ALL done! Posting this thru firefox running on unbuntu itself.. 

I had to go download r-pppoe and install that, but that wasn't too much of a drama. 

sweet!

now time to get everything else setup and try and say goodbye to xp forever.

---

### Post by Mustard on 2005-09-25
Good luck in your endeavour.  I've recently formatted over my windows partition myself.

---

### Post by GTvulse on 2005-09-25
[QUOTE=predator]ALL done! Posting this thru firefox running on unbuntu itself.. 

I had to go download r-pppoe and install that, but that wasn't too much of a drama. 

sweet!

now time to get everything else setup and try and say goodbye to xp forever.[/QUOTE]
Hmm... I wonder why.. I've never needed to use rp-pppoe with the eciadsl drivers. I guess you downloaded the deb package from Universe, that has that bogus dependency... Anyway. I'm happy to be of help.  ;-)

---

