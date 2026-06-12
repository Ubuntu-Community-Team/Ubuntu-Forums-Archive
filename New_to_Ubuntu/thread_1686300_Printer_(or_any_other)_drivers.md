---
title: "Printer (or any other) drivers"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by spacefrog on 2011-02-12
Hi, I've just bought a samsung scx 4600 printer and I would like to installit. My disc drive doesn't work, but I have downloaded the linux drivers from samsung. My problem is that I have no idea how about what to do with them.

Thanks.:confused:

---

### Post by robsoles on 2011-02-12
Welcome to UF!

Sorry to start out ultra basic but you don't say much you've tried:


Have you looked in 'System'->'Administration'->'Printing' yet?

Have a poke through that and let us know if you get it or how we can really help ;)

---

### Post by spacefrog on 2011-02-12
I have delved further, and been led to the Samsung repository page: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) but I can't see light at the end of the tunnel.I have tried copying and pasting different command lines to no effect and am lost in all this.

Perhaps it would be best if I posted again to find a recommendation for a different printer, I just need a reliable b&w laser printer that doesn't give me these problems.

Thanks anyway.

---

### Post by robsoles on 2011-02-12
Please look at the picture in my attachment, look at the dialog boxes I have open over my browser

Have you tried the 'add' button in the "System"->"Administration"->"Printing" dialog box?


Have you seen: [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers) and [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/SamsungPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/SamsungPrinters) linked from it?


If you could tell me what blocked you from getting it set up using the regular mechanism for setting up printers then I might be able to see/find the way around that for you.


<edited-in>Note: My screenshot is from after selecting how the printer was attached after pressing the '+ add' button...</edited-in>

---

### Post by spacefrog on 2011-02-14
The regular mechanism for adding a new printer has the SCX 4500 model but not the SCX 4600 model I've got. So I tried to add the samsung drivers to the repository by following the instructions in [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/), which I find terribly complex and it didn't work either. 

So I went back to disc supplied by the manufacturer but it failed to mount. Installing a further two disk drives from previous PCs down in the cellar revealed the same, so there is also a problem with the PC failing to read from any CD/DVD disk drives.

Thanks for your help.

---

### Post by robsoles on 2011-02-14
After adding his ("suldr") repositories to your /etc/apt/sources.list file did you search synaptic for 'samsungmfp-driver' and 'samsungmfp-data'? If not then I reckon you can get them slightly quicker via terminal (unless you are the 'fastest mouse in the west' :lol:)```
sudo apt-get install samsungmfp-driver samsungmfp-data
```I found that information in the post I am going to quote - if you haven't seen a very full tutorial for installing the Samsung Unfied Printer Driver then click the arrow after tweedledee. > **tweedledee said:**
> ...

**Using a scanner:** if you are trying to use your printer as a  scanner, you will need to add yourself to the "lp" group after  installing the appropriate packages.  You will then to log out and back  in for the change to take effect.  If you still have trouble scanning,  see the repository website *before* posting for help; many common  questions are addressed there.  See also the note on USB scanners below  (#9 under other Closing Tips).

...



Re optical drive: If you installed using optical media and now optical drives don't work then I wish I could hold some confidence the cables aren't plugged in properly anymore, but if you've been changing drives then you've been looking close enough at the cables. Did you try a different sata port or IDE configuration? I'm sorta betting you tried both/'all sorts' but worth the prompt if you haven't...

---

### Post by robsoles on 2011-02-14
When I posed my first reply I looked at your post count and welcomed you! #-o:lolflag:

---

### Post by spacefrog on 2011-02-14
I followed the indications from the Tweedledee page you referred me to and the printer started working after I updated libpng12 and deleted all the previous installation attempts, so I assume that was the solution.

The other problem with the disc drive remains a mystery. I have unplugged it and plugged it in again a few times, but I haven't tried changing the IDE configuration....I might break something!

Thanks again!

---

