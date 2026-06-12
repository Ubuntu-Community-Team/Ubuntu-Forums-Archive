---
title: "Installing &quot;unsupported&quot; drivers"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by gersa on 2010-11-25
Hi all

Don't really know if I'am posting this in the right place or not, but here we go.

I'am trying to install drivers for this card:

03:07.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)

The installation info says:

make

sudo make install

When I first run the make command there where some quick errors so I now have spent a week of searching different forums for ideas.


I tried downloded the driver pakage as a Tarball, get anb hg, and they all works. So get hold of the diver pakage works fine whatever  method I use.



I then tried to copy the driver pagage to differnt location in the file system like root and home directories, I don't thinK I seen any differs in the result of this thou.


While browsing different forums i found a lot of usefull commands to run like:

apt-get install linux-headers-$(uname -r) build-essential

make release VER=`uname -r`

And a lot more, got the error, among others:

***WARNING:*** You do not have the full kernel sources installed.


Went hunting in all the forums again and found that one probeble sollution was to install a bunch of different headers, installed all the haders that I reference to, but got the same error.

My conclusion of all this is that I have to use git and make the installation in a mirror kernal. But for ones I realy hoping I'm wrong...


Can it really be that hard to install a driver pakage?


I've tried to install "http://www.linuxtv.org/repo/#mercurial" with the same result so I think there must be some copability probs or?


By the way the pakage I want to install can be found here:
[http://jusst.de/hg/mantis/summary](http://jusst.de/hg/mantis/summary)


Would realy apreciate  a clue if the "Git" trail is the way to go, before iI put on the efford to learn all that.  Hate to go to MS crap just becouse of this.


Othervwise the 10.10 realy rules, never seen this computer so fast....

Regards

Gersa

---

### Post by Daveth on 2010-11-25
this explains the process fairly clearly

[HTML]http://maketecheasier.com/install-software-from-a-tarball-in-linux/2009/06/25?doing_wp_cron[/HTML]

Compiling programs requires some packages that are not installed by default. You can install these all at once by installing the build-essential package.

Let us know how you get on with that. By the way, I assume you have tried this device and it is not supported by the kernel???

---

### Post by gersa on 2010-11-25
Thanks, but I've tried that before and there isn't any config file in the driver package.

The files in there are:

/home/dvd/mantis-5292a47772ad/COPYING
/home/dvd/mantis-5292a47772ad/hgimport
/home/dvd/mantis-5292a47772ad/INSTALL
/home/dvd/mantis-5292a47772ad/mailimport
/home/dvd/mantis-5292a47772ad/Makefile
/home/dvd/mantis-5292a47772ad/README
/home/dvd/mantis-5292a47772ad/README.patches


The readme says:

make

sudo make install

And the make resault is:
#= My translations

root@dvd-GA-MA78GM-S2H:/home/dvd/mantis-5292a47772ad# make all
make -C /home/dvd/mantis-5292a47772ad/v4l all
make[1]: Går till katalogen #(go to directory) "/home/dvd/mantis-5292a47772ad/v4l"
scripts/make_makefile.pl
make[1]: execvp: scripts/make_makefile.pl: Åtkomst #(Access) root@dvd-GA-MA78GM-S2H:/home/dvd/mantis-5292a47772ad# make all
make -C /home/dvd/mantis-5292a47772ad/v4l all
make[1]: Går till katalogen #(go to directory)"/home/dvd/mantis-5292a47772ad/v4l"
scripts/make_makefile.pl
make[1]: execvp: scripts/make_makefile.pl: Åtkomst nekas #(Access denied)
Updating/Creating .config
/bin/sh: ./scripts/make_kconfig.pl: Permission denied
make[1]: *** Ingen regel för att skapa målet #(no rule to create target) ".myconfig", som behövs till #(needed for) "config-compat.h".  Stannar. # (stops)
make[1]: Lämnar katalogen #(Leave directort) "/home/dvd/mantis-5292a47772ad/v4l"
make: *** [all] Fel # Error) 2

Earlier I tried to install a bunch of headers and the make longer but with the same errors ay the end as now. It was then I got the "***WARNING:*** You do not have the full kernel sources installed." at the top.

Thats why the kernel mirror git track opend up... ;)

but I can't bellive it can be than much work just to install a driver...


Regards


****

---

### Post by gersa on 2010-11-25
And theese drivers are not in the linuxTv driver packages but they are in the same format.

The package I try to install are linuxTv package but with added support for Mantis (2033).

Regards

Gersan

---

### Post by gersa on 2010-11-26
Could someone please just tell me if the Git mirror kernal way is the way to go.
Or if there are other easier way to get this done...

Regards

Gersan

---

### Post by gersa on 2010-11-26
More info on HW:

03:07.0 Multimedia controller [0480]: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] [1822:4e35] (rev 01)
    Subsystem: Twinhan Technology Co. Ltd Device [1822:0008]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min, 63750ns max)
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fdbff000 (32-bit, prefetchable) [size=4K]

regards

Gersa

---

### Post by gersa on 2010-12-02
Hi all

Sorry to say after trying to make a Linux installation to work for weeks, I just made MS Windows7 installation in under two hours. Everything up and running whith Media Portal and XP-Drivers for the Mantis 2033 card.

Hate to give up but I really gave Ubuntu and a bunch of other linux dists. With the same problem.

But I find it a bit confusing thoug that installing a driver should be that much harder in "the open" plattform than W7.

Really love the 10.10, the Ubuntu version seams more ready than the Kubuntu releas.

As long as you don't have to go "outside the box" the Ubuntu 10.10 realy rules. But to intstall a driver you have to be a semi pro or maybe pro programmer to make it work.

The total lack of responce from here I take as a proof of that.


So over and out, for now. Runnning the 10.10 on my laptop and it works great.

Are there realy no kind of diver install wisard in Ubuntu???

Iam willing to make a go at again if anyone have any ideas.

Regards

Gersa

---

### Post by madjr on 2010-12-02
> **gersa said:**
> Hi all

Sorry to say after trying to make a Linux installation to work for weeks, I just made MS Windows7 installation in under two hours. Everything up and running whith Media Portal and XP-Drivers for the Mantis 2033 card.

Hate to give up but I really gave Ubuntu and a bunch of other linux dists. With the same problem.

But I find it a bit confusing thoug that installing a driver should be that much harder in "the open" plattform than W7.

Really love the 10.10, the Ubuntu version seams more ready than the Kubuntu releas.

As long as you don't have to go "outside the box" the Ubuntu 10.10 realy rules. But to intstall a driver you have to be a semi pro or maybe pro programmer to make it work.

The total lack of responce from here I take as a proof of that.


So over and out, for now. Runnning the 10.10 on my laptop and it works great.

Are there realy no kind of diver install wisard in Ubuntu???

Iam willing to make a go at again if anyone have any ideas.

Regards

Gersa

weird i haven't seen this thread. I've been browsing this forum quite frequently lately.

what card are you trying to install?

Usually most drivers are added directly to the kernel.

so yes, some extra peripherals can be tricky to install. Macs have this problem too and thats why they dont let others open, modify, install anything "unsupported" to their computers. 

linux does allow the freedom for this and supports a lot more hardware.

The best thing you can ask for, to your manufacturer is to release a **binary driver installer** (.deb) for ubuntu, instead of making the user compile it themselves.

The good thing about linux guys is that even if the manufacturers dont do the work, they usually try to do it for them anyway. So your card may not be working now out of the box, but in a future release a driver may be added to the kernel if the company is willing.

3 years ago i had to install many drivers or add fixes, now i barely have to it anymore.

Well at least this card seems to have a driver, so i'll give them some credit for that.

If you're still trying to get it installed, we might check the process and see where the errors are.

Its still going to be a bit tricky and i cant guarantee anything, but we could try and do what the manufacturer should had done in the first place.

---

### Post by madjr on 2010-12-02
umm, i found these discussions about it that might be of help:

[http://www.linuxtv.org/pipermail/linux-dvb/2008-October/029925.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-October/029925.html)

[http://www.backports.ubuntuforums.org/showthread.php?t=450761](http://www.backports.ubuntuforums.org/showthread.php?t=450761)

[http://www.freak-search.com/de/thread/332251/linux-dvb_problem_with_mantis_drivers_for_terratec_cinergy](http://www.freak-search.com/de/thread/332251/linux-dvb_problem_with_mantis_drivers_for_terratec_cinergy)

---

### Post by gersa on 2010-12-02
More info on HW:

03:07.0 Multimedia controller [0480]: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] [1822:4e35] (rev 01)
    Subsystem: Twinhan Technology Co. Ltd Device [1822:0008]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min, 63750ns max)
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fdbff000 (32-bit, prefetchable) [size=4K]

And theese drivers are not in the linuxTv driver packages but they are in the same format.
The package I try to install are linuxTv package but with added support for Mantis (2033).

The drivers are fetched from

[http://jusst.de/hg/mantis/summary](http://jusst.de/hg/mantis/summary)

With "hg" Mercurial.

The files in the pakage are:

/home/dvd/mantis-5292a47772ad/COPYING
/home/dvd/mantis-5292a47772ad/hgimport
/home/dvd/mantis-5292a47772ad/INSTALL
/home/dvd/mantis-5292a47772ad/mailimport
/home/dvd/mantis-5292a47772ad/Makefile
/home/dvd/mantis-5292a47772ad/README
/home/dvd/mantis-5292a47772ad/README.patches


And the some of the errors can be found above. "***WARNING:*** You do not have the full kernel sources installed.". Tried to install all the headers I could find. But I think the main problem are rights to whrite to some kernel libs. I've tried to make a mirror kernel whit Git and succeded with that but when trying to install the driver in the mirror kernel I got the same error. Then I gave in and went MS way... Made me quite low but I've to get working before the end of januari, and now I know that I can get it to work in W7 in a coule of hours. So now I have some time to try Linux again. 

My belivef was that I would find some kind of Hardware Wisard or drivers Wisard.
But it seems like It's just synaptics that got kernel rights.

As said above I tried to install the "standard" linuxtv package but with the same errors, thats why I thougt it was a common known problem.



regards

Gersa

---

### Post by gersa on 2010-12-02
Thanks for your answer I read the info in thoose links. I belive I've tried all the tips there, at least as far I get it. But I'm am not an Linux expert so what I'm trying to say is that I think I'm missing something that everyone take for granted you know or??

Regards

Gersa

---

### Post by madjr on 2010-12-03
Is hard to get a wizard for these drivers because they are not binaries.

binaries install in 10 seconds, even windows needs them or you would be having the same problems there.

since the manufacturer wrote the drivers mainly for "windows" it also included the binaries. So it's their fault and responsability. I would send them an email and see if they can fix my problem.

If not, next time, i would avoid these kind of manufacturers and support the vendors that really make sure their hardware works correctly on other platforms.

prior to the purchase, a quick google would tell me if the hardware i want works ok or not.

now, am not sure where the problem lies with the drivers you got at hand. if i had your same card i would had tried a few things.

What i would do for now is test another distro like **fedora, mandriva or pclinuxOS** and try to install the drivers there.

it may take a bit longer, but you'll find out where the problem is.

This may be a positive learning experience if you have some time, but if not, then it would be better in the mean time to just use the card in its supported platform: windows.

---

### Post by gersa on 2010-12-03
Thanks agian.

The manufactir are gone since a couple of years. And I only bought the card couse it was the only one I could afford.
Before I bought it I checked theire website and they had drivers there for MS and linux.
This was like a couple of years ago, and I tried to make it work in 8.04 but I failed.
So then again the easy way out was Vista, but at that time it was a hole lot tweaking to get it to work in Media Portal but at least I got it to work ok.
And now I was thinking maybe it's easier to install drivers in 10.10 than in 8.04. So I gave it another try as discribed above.
Meantime I've seen that I guy named Manu has remade the Linux drivers and they are at:
[http://jusst.de/hg/mantis/summary](http://jusst.de/hg/mantis/summary)

This time I've tried install this drivers in: Ubuntu 10.10, 10.04 and 8.04, Kubuntu 10.10, pclinux and feodora, all whitout making it work.

So thats why I'm thinking I'm missing something basic.


Regards

Gersa

Real name is Di_ck but for some reason it get censured ...;-)

---

### Post by gersa on 2010-12-03
Hi again

I guess the answers are to find here:
[http://www.linuxtv.org/downloads/legacy/video4linux/v4l2dwgNew.html](http://www.linuxtv.org/downloads/legacy/video4linux/v4l2dwgNew.html)

But thats way over my head...


So as the noob I an I might better hang on to the hell of gates.


Thanks for trying!!


Regards

Gersa

---

### Post by madjr on 2010-12-03
no problem, i love helping whenever i can.

sorry i could not be of further help.

too bad the manufacturer is gone. It just makes it harder for us and for nice guys like Manu that are trying to "reverse" engineer it.

anyway, thanks for doing all you can. I hope to see you around in the cafe sometime, and dont hesitate to keep asking if you need help with anything else ;)

---

