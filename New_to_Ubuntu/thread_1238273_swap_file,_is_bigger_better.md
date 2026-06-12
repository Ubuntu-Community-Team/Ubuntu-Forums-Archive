---
title: "swap file, is bigger better?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by super kim on 2009-08-12
my swap file is tiny and all the girls laugh lol but really though my physical ram is thrice the size of the swap. does it matter:?: if so what can i do about it :?:

btw i have noticed that it is never being used, ever

---

### Post by wizard10000 on 2009-08-12
Depends.

If you have no need to hibernate the system you should be fine.  I have 6G of RAM and only a 2G swap partition.  The only time I've ever seen the swap partition used is when I open up a 4G VirtualBox session.

---

### Post by Paqman on 2009-08-12
> **super kim said:**
> 
btw i have noticed that it is never being used, ever

In that case it doesn't make any difference at all.

---

### Post by Simian Man on 2009-08-12
If you want to hibernate swap should be >= your amount of RAM.  If not, and you have enough RAM to do what you want (2 gigs is more than enough for me, but your usage may vary), then you don't need swap at all.

Then again, hdd space is so cheap there's not really much harm in having swap anyway.  And being able to hibernate is nice.

---

### Post by raymondh on 2009-08-12
Depends on your needs.  My RAM is 4GB.  My swap is 1.5Gb.  I use a video editor and hibernate ... even then, I don't get to use all the swap allocated.

I consider SWAP a spillover/catch basin for RAM.

---

### Post by colau on 2009-08-12
> **super kim said:**
> my swap file is tiny and all the girls laugh lol but really though my physical ram is thrice the size of the swap. does it matter:?: if so what can i do about it :?:

btw i have noticed that it is never being used, ever
Using top command you can check how much swap space is being used?

---

### Post by mcduck on 2009-08-12
> **raymondhenson said:**
> Depends on your needs.  My RAM is 4GB.  My swap is 1.5Gb.  I use a video editor and hibernate ... even then, I don't get to use all the swap allocated.

I consider SWAP a spillover/catch basin for RAM.

When hibernating only the actually used part of RAM is copied into swap, and that data is slightly compressed, so hibernating with less swap than RAM does usually work.

Still, in the worst-case scenario your system *will* fail to hibernate. Not very likely in normal desktop use, but it's definitely something you should keep in mind..

---

### Post by super kim on 2009-08-12
> **mcduck said:**
> When hibernating only the actually used part of RAM is copied into swap, and that data is slightly compressed, so hibernating with less swap than RAM does usually work.

Still, in the worst-case scenario your system *will* fail to hibernate. Not very likely in normal desktop use, but it's definitely something you should keep in mind..


thats ok, i don't hibernate anyway.

---

### Post by mcduck on 2009-08-12
In that case you are fine with minimum swap, or possibly with no swap at all.

---

### Post by raymondh on 2009-08-12
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by HappyFeet on 2009-08-12
Or you could be like the guy who used ***99GB*** for swap because he didn't want to "waste" the space. :rolleyes:

---

### Post by zerhacke on 2009-08-12
Swap is only used when physical RAM runs out and you need more temporary storage.  If you have multiple gigabytes of RAM and don't stress your system you can get away with no Swap at all since you'll never use it.

I don't suggest this.

I have a rule of thumb that Swap should be 1.5 times your physical RAM size, but there's no empirical data that says it should be.  It's just the guesses of an old man.

---

### Post by super kim on 2009-08-14
i have made a swap file now so my total swap is 1.5x the ram the swap is still not used at all. i even changed the swappiness to 100 and still the system monitor reports 0 bytes are being used. is this something i should be concerned about?

i tried to stress the ram by opening open office, gimp, firefox, rythmbox, totem playing a movie, 

ah hang on i added chess and it is now using 2.2mb
now inkscape pushed it up to 7mb

ok thats all the apps i have open now and it is only using 2% of the swap file.
whats going on my swappiness is 100

---

### Post by mcduck on 2009-08-14
> **super kim said:**
> i have made a swap file now so my total swap is 1.5x the ram the swap is still not used at all. i even changed the swappiness to 100 and still the system monitor reports 0 bytes are being used. is this something i should be concerned about?

i tried to stress the ram by opening open office, gimp, firefox, rythmbox, totem playing a movie, 

ah hang on i added chess and it is now using 2.2mb
now inkscape pushed it up to 7mb

ok thats all the apps i have open now and it is only using 2% of the swap file.
whats going on my swappiness is 100

swappiness isn't absolute control over how much swap is used or not, it's just one of the parameters the kernel uses for controlling swap use. So swappiness of 100 doesn't mean that your system always uses swap, it's just much more likely to do so.

Anyway, you definitely shouldn't be worried about swap being used, quite the opposite. Swapping is roughly 1000 times slower than using your RAM is, so as long as you have enough memory available the swap shouldn't be used no matter what swappiness level you set.

You can run "free -m" in a terminal, and if the amount of available swap equals the size you have configured, your swap is working perfectly fine and will be used when necessary.

 (little bit of swapping is part of normal memory management so you'll often see 1–2% of swap use even if you have plenty of free RAM available. When kernel is not quite sure if some cached data should be kept in cache or dropped completely it moves the data to swap, and drops it at later time if it wasn't needed any more)

---

### Post by uncleV on 2009-08-24
I managed to see the swap working giving Ubuntu a huge work.

Running  with Pentium 2x2.7 MHz, 4 GB RAM, 4.5 GB swap partition and swappiness=60 I didn't ever see any huge use of memory or/and swap in System Monitor. Especially the swap used was always 0% and memory use at 30% maximum when loaded all of the Applications:
GIMP with huge image opened, F-spot with huge image, OO's Presentation, and Calc, and Writer with two huge images, and  Drawer with huge image, Movie Player with mp3 playing, Mplayer with avi playing, VLC with second avi playing, YouTube clip playing in FireFox, text editor opened, Rhythmox streaming, terminal opened, Disk Usage Analyzer, Take Screenshot with a shot of the desktop copied to clipboard, Googleearth with a detailed map of Colorado, Skype, DC++ in action, Calculator, Compiz Fusion with cube rotating at 1800x1440 resolution, CompizConfig Settings Manager opened, Chess and... that's all as far as I remember.
And still memory used at max 38-39% and swap used 0%. All was not going very well was the clip from YouTube but there you could have problems even in normal situation.

So I was angry ;-) and tried to give it a real load. All other applications except DC++, Skype, Terminal and Mozilla were closed.
Then opened with OpenOffice Writer the file "pagefile.sys" from the Windows XP partition. It's a binary system file of 2 GB and as far as I know Windows uses it as a swap.
Then loaded System Monitor.

The memory started gradually filling up from 17% to 100% (3.7 GB) that I've never seen before.
AFTER THAT the swap started filling from 0% to a maximum of 40% (that's about the size of the file being opened).
After that the two processors loaded up to 99-100% and remained at that load. Evidently Writer was processing the "format" information of the file. Waited 4-5 minutes, nothing changed and the file wasn't opened yet. As I didn't need it I closed Writer. The processor load and used memory dropped immediately to normal values but the swap used space remained at about 2 GB.

During this "test" the system worked with the other opened applications but with some delay and huccups. The graphical processing remained smooth and fast.

---

