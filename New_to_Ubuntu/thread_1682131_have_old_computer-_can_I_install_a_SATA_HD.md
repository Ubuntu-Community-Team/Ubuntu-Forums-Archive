---
title: "have old computer- can I install a SATA HD?"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by s1baker on 2011-02-05
hi,
I have a desktop computer with Ubuntu 10.10 installed on it.
The box is 4-1/2 years old and the hard drives in it ( I think ) are the IDE ATA type ( 3-1/2" wide with the ribbon attaching to them ). I have 2 hard drives installed in the box for XP ( one with the XP OS on it and one for a back up for XP ) and I have another 35 gig HD in the box that has Ububtu on it. Now I want to add another larger hard drive for Ubuntu.
 Question: 
 Most of the 3-1/2" inch hard drives I see that are for sale are "SATA". Will SATA hard drives work on my computer, or will it need to have another card or another type of ribbon?
 Another question:   
 Is there some command that can be put in the terminal to determine exactly what type of hard drive I have, whether IDE or ATA or whatever?

Thanks

---

### Post by Autodave on 2011-02-05
> **s1baker said:**
> hi,

 Most of the 3-1/2" inch hard drives I see that are for sale are "SATA". Will SATA hard drives work on my computer, or will it need to have another card or another type of ribbon?
 

Thanks

You will have to install an adapter to let the SATA drive hook up to an IDE interface.  You can find them on-line rather cheaply.

---

### Post by techunit on 2011-02-05
It is always a risky thing when your talking about hardware that old. I think you might consider updating the bios before you attempt anything.

If your hardware is that old you may consider purchasing a new computer. My computer is approaching three years old now and I will be getting a new one fairly soon. Now the computer is still very powerful and by ubuntu standards more than necessary.

---

### Post by josephmills on 2011-02-05
would a masscool( [http://www.masscool.com/](http://www.masscool.com/) ) device help with this?

---

### Post by Paqman on 2011-02-05
4 1/2 years is not that old, you should have SATA ports. 

The easiest way to find out would be to simply open up the case and see if you've got any on the motherboard. They look like this:
[IMG]http://www.overclock3d.net/thumb.php?id=2429[/IMG]

You'll need SATA power connectors on your power supply too:
[IMG]http://2009.hardwarezone.com/img/data/articles/2004/1192/tutorial-sata_power_conn.jpg[/IMG]

---

### Post by grahammechanical on 2011-02-05
Just google SATA to PATA adapter. Make sure that you are getting the right type. There are adapters that let you fix a PATA (IDE) drive on to a SATA connector on the motherboard. Which you do not want. You want the type that lets you fix a SATA drive on to a PATA (IDE) connector on the motherboard.

One device I have just looked at showed a little circuit board that plugged onto the back of the SATA drive to give a header that accepted the IDE cable that would plug on to the motherboard.

Regards

---

### Post by techunit on 2011-02-05
Your right it isn't that old for a desktop. With a laptop your pushing it a little. All depends on the specs of the computer when you bought it.

---

### Post by YesWeCan on 2011-02-05
> **s1baker said:**
> Another question:   
 Is there some command that can be put in the terminal to determine exactly what type of hard drive I have, whether IDE or ATA or whatever?
You can see what hardware you have on your mobo using 'lshw'
This will tell you if you have SATA interfaces.

---

### Post by walt.smith1960 on 2011-02-05
> **Paqman said:**
> 4 1/2 years is not that old, you should have SATA ports. 

The easiest way to find out would be to simply open up the case and see if you've got any on the motherboard. They look like this:
[IMG]http://www.overclock3d.net/thumb.php?id=2429[/IMG]

You'll need SATA power connectors on your power supply too:
[IMG]http://2009.hardwarezone.com/img/data/articles/2004/1192/tutorial-sata_power_conn.jpg[/IMG]

Winner.  If you don't have SATA ports, you can still buy PATA drives.  I have a PATA drive-SATA port adapter. It works but why mess with an adapter if you don't have to? Just one more thing to fail.

---

### Post by s1baker on 2011-02-05
thanks guys. Here is the listing of my HD interfaces using the command "lshw" in the terminal.
 It looks like ide:1 shows to be configured for sata, though I don't know what that means.
(sorry about the smiley faces, where there was a "=8" in the listing, for some reason, a smiley face appeared)


==============================================================
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0 (size=8) ioport:bf0(size=4) ioport:970 (size=8) ioport:b70(size=4) ioport:e000(size=16)
==============================================================

---

### Post by qyot27 on 2011-02-05
Pfft at 4½ being 'old'.  My main computer is pushing the decade marker.  Market obsolescence shouldn't be a deciding factor when the setup is still in the same general continuum (i.e. i686-lineage and whatforth), and the hardware isn't broken or breaking.


In any case, just go on Amazon or Newegg and get an actual PATA drive.  For all I know, connecting it via a SATA-to-PATA adapter will degrade performance (beyond the fact that PATA's upper limit is about 133MB/s, and you'd only approach that if you were using a 10,000rpm drive; 7200s operate somewhere around 80MB/s).  I'd use it as a last resort only.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000014&IsNodeId=1&Description=hard%20drive%20ide%203.5&name=Internal%20Hard%20Drives&Order=PRICE&Pagesize=20](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000014&IsNodeId=1&Description=hard%20drive%20ide%203.5&name=Internal%20Hard%20Drives&Order=PRICE&Pagesize=20)

[http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=%22internal+hard+drive%22+7200+ultra+-SATA&x=0&y=0](http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=%22internal+hard+drive%22+7200+ultra+-SATA&x=0&y=0)

---

### Post by DiSTORT3D on 2011-02-05
Sata is since 2001 installed on almost any mainboard 1/2 slots.

---

### Post by YesWeCan on 2011-02-05
There ya' go. You already have a serial ATA interface on your motherboard. When you pop the lid you will see the connector(s) somewhere.

The terminology is all messed up these days. IDE used to be the all encompassing term (see [http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)) which is why your SATA is listed under ide1.

The funny thing is that serial ATA is a lot faster than parallel ATA (PATA is called IDE these days). You would think a parallel bus would be faster. Well, it is in theory but the manufacturing cost of the extra wires has been saved by making super-fast chips with fewer wires. Besides, SATA is physically easier to connect and disconnect. There are several breeds of SATA now...SATA1,2 & 3 and external SATA and yet another that has integrated psu wires. When you buy a new HD it will have an internal, 1, 2 or 3 interface (increasing maximum speed). It is all backwards compatible so you can plug a SATA3 into a SATA1 connector using any internal SATA cable. Some SATA cables have retension clips which is a good idea.

> **s1baker said:**
> thanks guys. Here is the listing of my HD interfaces using the command "lshw" in the terminal.
 It looks like ide:1 shows to be configured for sata, though I don't know what that means.
(sorry about the smiley faces, where there was a "=8" in the listing, for some reason, a smiley face appeared)


==============================================================
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0 (size=8) ioport:bf0(size=4) ioport:970 (size=8) ioport:b70(size=4) ioport:e000(size=16)
==============================================================

---

### Post by s1baker on 2011-02-05
I agree with you qyot27. I've never had a board, processor chip or memory chip fail yet after years of using computers. I've replaced power supplies, fans, the old floppy drives, just put a new cd rw in, and of course, a lot of HD's, but the main boards and chips just keep on working. ( and the case's last )

---

### Post by Paqman on 2011-02-05
> **s1baker said:**
> 
(sorry about the smiley faces, where there was a "=8" in the listing, for some reason, a smiley face appeared)


Wrapping it inside [code] tags would have sorted that out. Use the little # button on the text editor when posting.

---

### Post by techunit on 2011-02-05
Good Luck! Harddrives are the one thing that scare me when it comes to doing anything with them. I ways feel like I am going to corrupt my data. You sir are a braver man than I.

---

### Post by walt.smith1960 on 2011-02-05
> **s1baker said:**
> I agree with you qyot27. I've never had a board, processor chip or memory chip fail yet after years of using computers. I've replaced power supplies, fans, the old floppy drives, just put a new cd rw in, and of course, a lot of HD's, but the main boards and chips just keep on working. ( and the case's last )

I had both SATA ports become intermittent on a Gigabyte board a couple months ago. I HATE intermittent failures:mad:.

---

