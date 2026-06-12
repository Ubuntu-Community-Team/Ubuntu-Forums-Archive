---
title: "Detailed Hardware Listing"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by zer010 on 2009-08-16
Is there any way I can get a detailed account of my hardware, such as mobo model, version, and a detailed list of all the hardware that is connected.  I have a few hardware issues, and I believe getting all the pertinate info about exactly what I have would be the first step towards troubleshooting the few issues I have.  Is there also something that can tell me if there is something not working properly?  I am asking this for all hardware in general, before I start to get into more specific, part based listings.  Any help is greatly appreciated! :)

---

### Post by bluelamp999 on 2009-08-16
Sysinfo (available in Synaptic) is a nice GUI app which should give you all your hardware info...

---

### Post by zer010 on 2009-08-16
Sysinfo is ok, but i want A LOT MORE info than what I saw in that app.  I need a good rundown of all PCI cards, in what slot.  Versions, model numbers, vendors, manufacturers, etc.  CPUz and GPUz for Win had most of what I was looking for.  I need it also for PCI slots as well.  Thanks for the suggestion though! I'll be keeping it around for what it does do well. Thanks!  Any other suggestions?  :)

---

### Post by sandyd on 2009-08-16
this is classic.
```

lspci

```

---

### Post by zer010 on 2009-08-17
Thanks! That was quite helpful! I did ask for a LOT more info, and with the  -vv option, it gave me just that.  A LOT MORE.  Thanks!  Any other suggestions like this for the rest of the hardware?

---

### Post by tarps87 on 2009-08-17
```
lshw
```

list hardware ;)

This command piped through grep can be very usefull

e.g
```
lshw | grep cpu
```
or
```
lshw | grep cpu -A 10
```

Note: you may get more info if you run it as root

---

### Post by zer010 on 2009-09-14
It's been a while since I posted to this thread, but good thing I left it unsolved.  I need detailed info on my RAM.  Someone had said that the BIOS will tell me what I need to know, but my BIOS sucks.  I need to find out what RAM is in what slot, and the type that's in my machine.  I've already tried using the solutions from previous posts in this thread, to no avail.  Thanks for any help that ya'll can give me.

---

### Post by OffAxis on 2009-09-14
Have you cracked open your case?
There's usually a sticker on the RAM sticks that specifies what they are.

If those specs on your signature are the system in question (P3 500MHz) then it's probably some variation of SD RAM; PC100 most likely. If you're looking at the sticks then they should have 2 notches in the interface side.

If there's no sticker on the RAM then you can always check the manual from the mobo manufacturer. They'll list the maximum speed of the RAM in there.

You could try this application,
[http://www.overclock.net/2837226-post91.html](http://www.overclock.net/2837226-post91.html)

(the newer version is here:
[http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html](http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html)
but you may have to jump through some hoops to get it to work)

I'd also like to mention (just because I didn't see it previously in this thread) that the /proc folder has some very good hardware information.
Something like
```
less /proc/cpuinfo
```
will list your CPU specs.

Good luck.

---

### Post by Nburnes on 2009-09-14
I would just do
 
```
sudo lshw
``` 
 
In Terminal.

---

### Post by gordintoronto on 2009-09-14
> **zer010 said:**
> It's been a while since I posted to this thread, but good thing I left it unsolved.  I need detailed info on my RAM.  Someone had said that the BIOS will tell me what I need to know, but my BIOS sucks.  I need to find out what RAM is in what slot, and the type that's in my machine.  I've already tried using the solutions from previous posts in this thread, to no avail.  Thanks for any help that ya'll can give me.

sudo lshw 

tells me how much RAM is in each slot, and how fast it is.

Beyond that, your best bet is physical inspection.

---

### Post by oldfred on 2009-09-14
Variation on previous comments to just get memory. I copied this from some previous post

sudo lshw | grep -m 1 -A 25 "*-memory"

For explanation, lshw stands for list hardware, and spits out page after page of information on all the hardware in your machine, this information is then sent to grep, which searches for a key word. I have set a few flags for it, -m 1 which limits the search results to one, saving some time finding additional results when there is only ever going to be one in the hardware output, and -A 25 which sets the number of lines of output after finding the search term to 25(default 0, which wouldn't help here). "*-memory" is there because this is our search term.

---

