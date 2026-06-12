---
title: "Where is the bottleneck??"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by madu on 2009-01-18
Hey guys...

I just built a new system and quite dissapointed that I cant get what I wanted.

So I do quite a lot of file copying/extracting/encoding and I used to have a single core processor. Whenever I am doing an extraction or an encoding, I couldnt pretty much do anything else, even browsing. Firefox would blackout from time to time until the file processing is finished.

So thinking that it is the cpu, I bought a new quad core (Q9550) and an additional hard disk and did clean Ubuntu install. This time, I installed the root(/) in one hdd and the home(/home) in the other. Thinking that all the file operations will be isolated in /home hdd so I wont have problems in multitasking. But to my greatest disappointment I find that the situation is still the same. I still cannot do browsing when I am doing some file processing, although quad cores are for multitasking.

SO where is the bottleneck? Is there anything I can do rather than maybe having a Raid setup?

Thanks a lot.

---

### Post by stefangr1 on 2009-01-18
This is indeed strange. I have also multiple disks, only a 2.67Ghz c2d, and I don't have this problem when I'm doing something on a disk that isn't affected by large read/write operations on another disk.

You can use the command "top", followed by "1" (to show different cores seperately) to see what's happening with your CPU. Can you post your output when you're doing whatever you're doing that blocks the system?

Can you also post the output of the command "df" ?

How much RAM do you have (I suppoze more then enough, but just to be sure)?

And last but not least: what is the disk operations that causes the trauble?

---

### Post by sadaruwan12 on 2009-01-18
> **madu said:**
> Hey guys...

I just built a new system and quite dissapointed that I cant get what I wanted.

So I do quite a lot of file copying/extracting/encoding and I used to have a single core processor. Whenever I am doing an extraction or an encoding, I couldnt pretty much do anything else, even browsing. Firefox would blackout from time to time until the file processing is finished.

So thinking that it is the cpu, I bought a new quad core (Q9550) and an additional hard disk and did clean Ubuntu install. This time, I installed the root(/) in one hdd and the home(/home) in the other. Thinking that all the file operations will be isolated in /home hdd so I wont have problems in multitasking. But to my greatest disappointment I find that the situation is still the same. I still cannot do browsing when I am doing some file processing, although quad cores are for multitasking.

SO where is the bottleneck? Is there anything I can do rather than maybe having a Raid setup?

Thanks a lot.

Hi,
Well you've a very strange case it's very hard to tell whats wrong any way I run Ubuntu on a AMD atjlon64 3200+ (2.02Ghz) processor and I also do lot of multitasking but I'd never come a cross a problem like this even in this time I'm writing a DVD while doing a big backup on my system.
Also I've two HDD's and they are very old never give any trouble as you've mentioned. OK Can you post how much memory you've on your PC.

---

### Post by madu on 2009-01-18
Thanks for the replies guys.
I have 4GB memory installed in this pc.

I checked top (although could figure out how to get 'top 1' to work) and during the file extraction, the top 3 processes were unrar, firefox and Xorg. And each of them were taking a cpu load of about 10%~15%.

The 'df' is:
[B]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5             50949016   3370128  44990820   7% /
tmpfs                  1685712         0   1685712   0% /lib/init/rw
varrun                 1685712       108   1685604   1% /var/run
varlock                1685712         0   1685712   0% /var/lock
procbususb             1685712      2808   1682904   1% /proc/bus/usb
udev                   1685712      2808   1682904   1% /dev
tmpfs                  1685712       712   1685000   1% /dev/shm
lrm                    1685712      2000   1683712   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda5             71087008  29073504  38402496  44% /home[/B]

When I say Firefox hangs, its not like it hangs completely until the file operation is finished. There are lapses.. it freezes for a couple of seconds and works for a while and then hangs again.. and most of the time it blacks out (I think you guys know what I mean by 'black out')...

Am I doing something wrong? This is a standard install.. I didnt change or add anything...

Any help is appreciated guys.. 

Thanks.

---

### Post by HavocXphere on 2009-01-18
Try reducing the thread priority on the encoding thread & see if that helps.

If you have the time&patience do a clean install on only the new hdd. A flakey hdd can cause symptoms like this...so that would eliminate that possibility.

Double check you graphics drivers. Black screens are often cause by bad drivers. That or 100% cpu utilization.

And finally: Many encoding apps are *designed* to max out system resources to get the work done asap. That doesn't count for copying though...

---

### Post by stefangr1 on 2009-01-18
Maybe the problem is related to firefox caching in ~/.mozilla/firefox/ .

It is possible to change this, as far as I remember, but I'm not 100% sure.

Maybe: type in your browser bar "about:config"
Right-click, choose new string, enter as a name "browser.cache.disk.parent_directory"
and then enter the full path to a caching directory on your root disk (you could make a folder owned by you in /tmp).

---

### Post by madu on 2009-01-18
> **HavocXphere said:**
> 

Double check you graphics drivers. Black screens are often cause by bad drivers. That or 100% cpu utilization.



I am using the 177 Nvidia drivers. And these are not 'black screens'.. The Firefox (transparently) black out its browser window to indicate that the system is not responding or something.. I  don't think it is video driver related.

So you guys are saying that it shouldn't be so?

I'm more inclined to think it should be because ~/.mozilla like stefangr1 said.. because even the VirtualBox hangs the same way.. looks like I need another a seperate hdd for my file extraction/encodings...

Thanks guys.

---

### Post by linuxisevolution on 2009-01-18
> **madu said:**
> I am using the 177 Nvidia drivers. And these are not 'black screens'.. The Firefox (transparently) black out its browser window to indicate that the system is not responding or something.. I  don't think it is video driver related.

So you guys are saying that it shouldn't be so?

I'm more inclined to think it should be because ~/.mozilla like stefangr1 said.. because even the VirtualBox hangs the same way.. looks like I need another a seperate hdd for my file extraction/encodings...

Thanks guys.

I had the same problem. It had to do with too many i/o wait requests so firefox basically can't get it's "stuff" -like chache, through. I fixed this by disabling Compiz. Right click desktop, click Change Desktop Background, click the Visual Effects tab, and turn it off. Try updating firefox, too. My hard drive is 7200 RPM single platter 250gb 16mb cache, but it used to go into 100% utilization randomly because of this. Try updating firefox, too. Good luck :guitar:

---

### Post by madu on 2009-01-18
> **linuxisevolution said:**
> I had the same problem. It had to do with too many i/o wait requests so firefox basically can't get it's "stuff" -like chache, through. I fixed this by disabling Compiz. Right click desktop, click Change Desktop Background, click the Visual Effects tab, and turn it off. Try updating firefox, too. My hard drive is 7200 RPM single platter 250gb 16mb cache, but it used to go into 100% utilization randomly because of this. Try updating firefox, too. Good luck :guitar:

Thanks man.
Really.. Compiz? It's a difficult feature to give up man.. I'm so used to some of its features now..
anyway will give it a shot and see..

P.S: just tried extracting a file with no bling.. but still no luck :(

---

### Post by linuxisevolution on 2009-01-18
> **madu said:**
> Thanks man.
Really.. Compiz? It's a difficult feature to give up man.. I'm so used to some of its features now..
anyway will give it a shot and see..

Yeah... I gave it up for a while until the update was released. The problem doesn't seem to happen as much in LXDE as it does in Gnome. Do the updates first, and try messing around with the Compiz settings. I only have it on beceause I like emerald themes :lolflag: . The themes help set a mood when I work on authoring :P

EDIT: Try a different browser. It does NOT happen in Seamonkey ( hehe, funny name ) Epiphany ( spelled it wrong.. ) and Konqueror. Konqueror I use when I need to do something fast because it launches quick. Seamonkey is for those who Firefox has gone cannibalistic.

---

### Post by theozzlives on 2009-01-18
> **madu said:**
> I am using the 177 Nvidia drivers. And these are not 'black screens'.. The Firefox (transparently) black out its browser window to indicate that the system is not responding or something.. I  don't think it is video driver related.

So you guys are saying that it shouldn't be so?

I'm more inclined to think it should be because ~/.mozilla like stefangr1 said.. because even the VirtualBox hangs the same way.. looks like I need another a seperate hdd for my file extraction/encodings...

Thanks guys.

The window turnes greyish. I've had that in Audacity but it was the Audacity window that gets greyed out not FireFox. hmmmm....

---

### Post by madu on 2009-01-18
Yeap.. greys out.. that should be the right word I guess.. :)

Thanks.. I will try a different browser.. pretty strange using something other than FF in Linux.. although I was used to using a couple when I XP :confused:
it will really difficult without the add-ons.. :(

---

### Post by HavocXphere on 2009-01-18
> **linuxisevolution said:**
> Try a different browser.
Blasphemy!;)

I can't really imagine using anything besides FF...maybe minefield.

---

