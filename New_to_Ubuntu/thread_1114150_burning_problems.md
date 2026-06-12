---
title: "burning problems"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by interceptorV8 on 2009-04-02
i have always had 2 dvd writers.  the hp that came with the machine and my pioneer that i installed and have done MOST of my burning with for the past 2 years or so.  lately the pioneer has been acting strange: spitting out bad discs or coasters.  at first i thought it was the cheap dynex dvds.  and then i thought maybe the drive is just dying since i use it for everything.  so i bought a new sata LG drive.  

the first dvd the LG made worked great. however now THIS drive doesn't seem to work right. now i'm thinking it might be something else.  i made a disc with the HP and it worked fine, but when i try it with the new LG, it does the same things the pioneer drive was doing.  is there a setting somewhere in ubuntu i can change somewhere?  i've been playing with some options like testing it with brasero and gnomebaker...  i'm going to switch to vista to see if it works in a little while.  any help would be appreciated.

---

### Post by HermanAB on 2009-04-02
Burn at low speed and see if the problem persists.  Most drives cannot work at the claimed speeds.  The full speed is just marketing guff.

---

### Post by interceptorV8 on 2009-04-02
i usually try to write at 8x and sometimes 4x.  another thing i've noticed (which might be related to cheap discs) is that when i do go to write a dvd in ubuntu, SOMETIMES the write speeds change.  USUALLY i get the typical options: 2x, 4x, 6x, 8x, and so on.  but sometimes i ONLY get 4x.

---

### Post by weedwacker on 2009-04-02
I had similar problems with a Pioneer as a second cd/dvd-rom.

As best as I can figure it had something to do with sharing the Iomega Zip drive cable. It may have been something to do with master/slave settings also. I don't really know for sure what caused the problem.

In my case I dumped the Iomega Zip drive and returned the Pioneer to NewEgg.

Good luck with your search for a solution.

---

### Post by interceptorV8 on 2009-04-02
well the drive SEEMS to work fine when i use nero on vista... however roxio just spat out a bad disc...

---

### Post by wolfen69 on 2009-04-02
a bad motherboard or ram can many problems with your system. the only way to know for sure is to run diagnostics. google for the software.

---

### Post by interceptorV8 on 2009-04-03
okay... put the pioneer back in...and with gnomebaker... in the output, i get this message as it's starting (or trying to) burn
: 
":-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms"

followed by:

":-? the LUN appears to be stuck writing LBA=30310h, keep retrying in 47ms"

and then followed by:

:-? the LUN appears to be stuck writing LBA=118310h, keep retrying in 47ms


i've been reading some things on this... some say it has something to do with the dma

---

### Post by interceptorV8 on 2009-04-03
well i think it's simply the cheap dynex dvds from best buy.  the HP writer can burn them just fine, but my ide pioneer and sata LG both do not seem to like the dynex discs... maybe it was just a bad batch since i've used dynex successfully in the past...

---

### Post by 4Foot on 2009-04-07
InterceptorV8:

Not so fast to blame the media. I have been chasing this problem for quite a while and just last week returned 200 Fuji DVD's I thought were bad because Ubu would spit them out. The replaement Memorex are not any better. Using first Ubu 8.10 and then 9.04 Beta and Brasero, KB3, XFBurn et all they will not burn to a blank DVD in my internal Sony drive nor the previous Plextor drive although they both had been working for year or morre.

I get a "SCSI" error and they choke.

However, if I plug in my old Pioneer USB external drive they will burn at 16X everytime with any of the burner software progs.

It happened to me when I changed media from an older stack of Fuji's to a new one but I am not certain it is the media change that caused this.

It is incredibly frustrating and I keep looking back hoping to find a solution but so far no joy.

I skipped over UBU 7.X as this is when the probs started, I thought it was a kernel problem but can't blame that anymore.

Hope someone a lot smarter then me can figure it out.

4Foot

---

