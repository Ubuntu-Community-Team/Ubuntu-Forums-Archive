---
title: "Let Ubuntu use more RAM?"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-07-08
I have Ubuntu 9.04 x64, and 4GB of RAM. I noticed that Ubuntu never uses more than 400 to 600MB of RAM. It doesn't matter if I have 10 applications running. I disabled my swap file, and it seems the same. Is there any tweaks I can do to encourage Ubuntu to use more RAM and cache things for better performance?

Otherwise, having 4GB of RAM really seems useless.

---

### Post by mikewhatever on 2009-07-08
Can you post the output of **free -m** command from Terminal.

---

### Post by Sealbhach on 2009-07-08
A tweak of sorts, use preload if you're not already using it.

[http://theitreport.com/entries/linux/ubuntu-performance-tip---preload](http://theitreport.com/entries/linux/ubuntu-performance-tip---preload)

It's in Synaptic.

.

---

### Post by ubuntuforums on 2009-07-08
@mikewhatever: Here is the output of 'free -m':
```
             total       used       free     shared    buffers     cached
Mem:          3869       1164       2705          0        329        498
-/+ buffers/cache:        336       3533
Swap:            0          0          0

```
So System Monitor only shows the buffers/cache? That command seems to show I am actually using a GB of RAM.


@Sealbhach: That looks like what I want, I'll try it out. Thank you.

---

### Post by ubuntuforums on 2009-07-08
Are there any other methods of making use of my excess RAM? Seems Preload isn't using much, most likely I have to wait until it recognizes patterns. But I don't imagine it will end up using even close to my entire memory, so I'm open for any other suggestions.

---

### Post by scorp123 on 2009-07-08
> **ubuntuforums said:**
> Here is the output of 'free -m':
```
             total       used       free     shared    buffers     cached
Mem:          3869       1164       2705          0        329        498
-/+ buffers/cache:        336       3533
Swap:            0          0          0

``` Looks totally normal. Total 3869 .. that's about 4G. 1164 are used, so that's about 1.2G, leaving about 2.7G free.

You simply aren't giving your PC anything to chew on. :D  Try ripping a DVD, encoding several HD videos in parallel, or something like that. That should do the job and force your system to yearn for more RAM ...

(and no, I am not ridiculing you in any way and I am apologizing if I just sounded like that. Fact is: Linux is more efficient at using RAM than e.g. Windows. If you want Linux to start crying for more RAM you simply have to give it something to chew on ...)

---

### Post by Mornedhel on 2009-07-08
You will never, ever run out of RAM with 4 GB, except if you do one of the following :

* Video edition/encoding
* Image edition
* 3D edition/render
* Heavy scientific calculations
* 3D gaming with all bells and whistles turned on, in which case you're running your games natively under Windows anyway

Desktop usage should not even get to a single GB, without factoring caching (already enabled) in, even with multiple documents open, surfing the web with dozens of tabs, music playing in the background, etc.

---

### Post by scorp123 on 2009-07-08
> **ubuntuforums said:**
> Is there any tweaks I can do to encourage Ubuntu to use more RAM and cache things for better performance?

You could try this:
[http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

e.g. you could force Linux to use more cache and less swap by manipulating the few parameters the article mentions.

It usually works. But with modern hardware (2 GHz and beyond) the difference is barely noticeable.

---

### Post by ubuntuforums on 2009-07-08
@scorp123 & Mornedhel: Hmm. I've already tried running a ridiculous amount of applications at once, didn't see much of a difference. But you're both probably right, in that I'm not running memory intensive applications. Regularly I don't do much more than surf the internet, listen to music, write documents and spreadsheets, and burn DVDs. So nothing that requires much memory. But I thought Linux was suppose to make use of all my free RAM and cache various things.

@scorp123: I'll take a look at that page right now, thanks.

---

### Post by bear24rw on 2009-07-08
you can try changing the minsize of preload to something really low to try to get it to cache more

---

### Post by Mornedhel on 2009-07-08
> **ubuntuforums said:**
> I thought Linux was suppose to make use of all my free RAM and cache various things.

It does its best, but 1 GB is still a lot of memory. I do 3D modeling as a hobby, and I rarely get 1 GB of actual used RAM, even with large scenes (and even then the CPU is more of an issue).

Right now, the simple state of RAM memory is that it's so dirt cheap everyone has 4 GB and no one can use it all.

---

### Post by ubuntuforums on 2009-07-08
@scorp123: That page is about tweaking your swapfile, I have mine disabled altogether, that should make things faster...

@bear24rw: Oh neat, didn't know I could do that, gonna experiment with different settings. Thanks.

@Mornedhel: Yeah that makes sense.

---

### Post by bear24rw on 2009-07-08
to change the minsize

sudo gedit /etc/preload.conf

then reload preload with

sudo /etc/init.d/preload restart 

you should turn it down real low and let us know what happens, im interested lol

---

### Post by ubuntuforums on 2009-07-08
Yeah, the default was two million, I put it down ridiculously to two hundred and fifty thousand. I guess it's a waiting game now, I have to use my computer for a while until it recognizes habits.

---

### Post by Cheesemill on 2009-07-08
I've heard of people mounting /tmp as a ramdrive to increase Firefox speed (it caches things into /tmp).

I'm sure a search on the forums will bring up some results.

---

### Post by scorp123 on 2009-07-09
> **Cheesemill said:**
> I've heard of people mounting /tmp as a ramdrive to increase Firefox speed (it caches things into /tmp). Nice idea.

Here a link on how to get RAM drives working:
[http://www.linux-mag.com/cache/7388/1.html](http://www.linux-mag.com/cache/7388/1.html)

Like with everything in Linux, there is more than one correct method depending on what you want and what you need .... :)

---

### Post by unutbu on 2009-07-09
Thanks for the interesting article, scorp123. :)

---

### Post by Psyphre on 2009-07-11
ramdrive is an interesting idea.

I gave it a try but im not seeing any difference. I dont think it even works. I followed the link given by scorp which basically tells me to do this:

```
# mkdir -p /mnt/tmp

# mount -t tmpfs -o size=1000m tmpfs /mnt/tmp
```

It successfully created a folder called tmp that was 1gb in size. I filled it up and despite this gnome system monitor shows im barely using any ram. Ive got 2gb, so filling up 1gb should show at least 50% (not including normal application/system uses) of ram being used up. Yet it only shows 40%.

---

### Post by txcrackers on 2009-07-11
The only way **I** have managed to use even close 1 Gb of *active* memory was to run 3 Jetty servers, Apache TCPMon, **and** JetBrainz' IDEA (that's 5 JVMs), Outlook 2007 (via Wine), Firefox with 10 tabs (with Flash loaded because I was looking at YouTube), Okular (20-page PDF), and Word 2007 (also via Wine).

It's kinda hard to use that much memory really, using "standard" applications - there's only so many things that you can do at once... ;)

---

