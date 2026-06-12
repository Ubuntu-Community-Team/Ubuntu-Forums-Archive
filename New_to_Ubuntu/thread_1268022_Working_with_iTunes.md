---
title: "Working with iTunes"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Scunnered on 2009-09-16
As I wish to totally work in Ubuntu and and am not prepared to dual boot at any cost I have been attempting to load iTunes but keep experiencing problems when doing so.

It has been an uphill struggle getting things to work. The first suggestion was that I should use Wine but when I downloaded it from synaptic and loaded iTunes the following was displayed:

 "***Itunes was not properly installed. If you wish to import or burn CDs, you need to reinstall iTunes***."

so I did as I was told but the message kept repeating no matter what I tried.

Another suggestion was that it might be better if I tried VirtualBox so round I went again only to have the same message displayed.

I am wondering if, as Wine & iTunes are still on the system, that asking VirtualBox to load iTunes into its set up it was receiving what was already stored on the physical hard drive. What happens is that an audio book that was loaded in Wine displays exactly the same in VirtualBox. 

Should I attempt to totally remove Wine, iTunes & VirtualBox and start all over again or can anyone please offer a better solution.  

It looks like I am very close to having iTunes working for me and hope that with your assistance eliminate this error message. Everything that I have seen so far will not imitate the audio book functions in iTunes so I am praying that the age of miracles is not past. 

Thanking you in anticipation

I have been unable to have anything work therefore have abandoned this in favour of dual booting very much against my wishes.  I have marked the post as abandoned

---

### Post by Simian Man on 2009-09-16
Why do you want to use iTunes?

---

### Post by QIII on 2009-09-16
You might look into Yamipod...

[http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/)

---

### Post by SunnyRabbiera on 2009-09-16
Need a CD importer and Burner?
Brasero and Banshee are viable alternatives to iTunes.

---

### Post by Inferiority Complex on 2009-09-16
> **SunnyRabbiera said:**
> Need a CD importer and Burner?
Brasero and Banshee are viable alternatives to iTunes.

They're good for dealing with music cd's but not for Audiobooks where tracks 1-7 might be chapter 1 and iTunes has the ability to rip these as 1 file.  Tracks 2-12 might be chapter 2 and I prefer them ripped to 1 file... etc.

Are there any programs that can rip selected tracks like this?

---

### Post by ainsworth_t on 2009-09-16
Also check out Songbird ([http://www.getsongbird.com](http://www.getsongbird.com)). It has a plug-in for iPod support and should be getting CD ripping support in the October release. Until then you can use Sound Juicer.

---

### Post by Paqman on 2009-09-16
> **Scunnered said:**
> 
I am wondering if, as Wine & iTunes are still on the system, that asking VirtualBox to load iTunes into its set up it was receiving what was already stored on the physical hard drive. 

Nope. Virtualbox creates it's own virtual hard drive (which is really just a file on your regular hard drive). It can't see anything on the rest of your hard drive by default.

To be honest, iTunes doesn't work well in Wine. If you reeeeeaaally need iTunes, then a dual-boot or virtualisation are your best bet. If you have hardware that requires iTunes then make sure you use the full version of Virtualbox available from their site, not the one from the repos, which lacks USB support.

If it's not an issue of supporting locked-down Apple hardware, then you'll find all the suggestions of a native Linux app to be a much easier solution in the long run.

---

### Post by Simian Man on 2009-09-16
Almost any Linux media player will support most ipods (Rhythmbox, Banshee, Exaile...), you don't need to install iTunes or one of its clones.

---

### Post by bigboy7foru on 2009-09-16
So i have a question i am wanting to install linux on my home computer as well
 
I do like itunes
 
whats the best all around media player on linux and how do you get it
 
ill probally be running Ubuntu 8.10 at home?

---

### Post by Scunnered on 2009-09-16
My thanks to you all for your contributions.

**Bigboy**

There is a very large shopping list provided by everyone above and no doubt you should find something to meet your needs.  I use Rythmbox myself and find that it does all that I want.

**Inferiority Complex**

It is reassuring that someone reads the post properly and can comment constructivly on the subject.  I much prefer just to join all the tracks on each CD and then listen from CD1 tract 1 to CD11 track 25 starting and stopping at will.  I have just finished listening to a book over a couple of days just by starting and stopping as and when I wished. Each time I was able to pick up from where I left off just like using a bookmark when reading a paperback. 

Have you looked at aldoblog.com where there is a section on downloading audiobooks. You may find this of assistance.  This is my preferred method.

If anyone knows of any program that will replicate the audio book functions in iTunes it will be most appreciated

**Paqman**

So far I am stuck with iTunes.  It looks very much like the way that Apple are delivering the download that is the problem as changing e-mail addresses does not seem to let me download a completely clean iTunes.

I thing I will start asking questions of Apple.  They are pushing like mad to get me to buy their latest Nano but unless I can get it to work properly in Linux there is no way that I will buy.

I will keep looking and praying as I am totally fed up with having to borrow someones Windows system just to load audio books 

Again my thanks to all

---

### Post by Simian Man on 2009-09-16
> **Scunnered said:**
> It is reassuring that someone reads the post properly and can comment constructivly on the subject.  I much prefer just to join all the tracks on each CD and then listen from CD1 tract 1 to CD11 track 25 starting and stopping at will.  I have just finished listening to a book over a couple of days just by starting and stopping as and when I wished. Each time I was able to pick up from where I left off just like using a bookmark when reading a paperback.
Sorry I did miss that from your post :/

> **Scunnered said:**
> I thing I will start asking questions of Apple.  They are pushing like mad to get me to buy their latest Nano but unless I can get it to work properly in Linux there is no way that I will buy.

My 4th gen Nano works perfectly with Rhythmbox.  No problems at all.  Unless you mean the as-yet unreleased 5th gen model.

---

### Post by LowSky on 2009-09-16
> **Scunnered said:**
> 

It has been an uphill struggle getting things to work. The first suggestion was that I should use Wine but when I downloaded it from synaptic 
You cant download or install iTunes from synaptic, its not in the Ubuntu repos
> 
and loaded iTunes the following was displayed:

 "***Itunes was not properly installed. If you wish to import or burn CDs, you need to reinstall iTunes***."

so I did as I was told but the message kept repeating no matter what I tried.
What version of iTunes?
> 
Another suggestion was that it might be better if I tried VirtualBox so round I went again only to have the same message displayed. What version of Windows did you install into VB?
> 
I am wondering if, as Wine & iTunes are still on the system, that asking VirtualBox to load iTunes into its set up it was receiving what was already stored on the physical hard drive. What happens is that an audio book that was loaded in Wine displays exactly the same in VirtualBox.  Huh? Virtual machines are sandboxed, in other words your data on your normal OS wont be touched by the VM

> 
Should I attempt to totally remove Wine, iTunes & VirtualBox and start all over again or can anyone please offer a better solution.  
Uninstall iTunes from Wine, and since I have no idea what OS your trying to run VM with, start from scratch there too


> 
It looks like I am very close to having iTunes working for me and hope that with your assistance eliminate this error message. Everything that I have seen so far will not imitate the audio book functions in iTunes so I am praying that the age of miracles is not past. 

Thanking you in anticipation


Look on the WineHQ website, itunes barely works. Its a POS of a program and has many issues. 

see the comments made about the last three versions, 7,8,and 9
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

also make sure Wine and Virtual box has access to your optical drive. its in there settings I believe to give access to these things.

---

### Post by bigboy7foru on 2009-09-16
yes i read them all i just want the basic rip and burn type player with a nice looking libary and easy to navigate.

---

### Post by SunnyRabbiera on 2009-09-16
> **bigboy7foru said:**
> So i have a question i am wanting to install linux on my home computer as well
 
I do like itunes
 
whats the best all around media player on linux and how do you get it
 
ill probally be running Ubuntu 8.10 at home?

Well opinions will vary on what is truly the best media player for linux.
Personally for a iTunes user I suggest Banshee or even Exaile, both provide decent interfaces to work with and are simular to iTunes.
Songbird is good too, its a little heavy but it is cross platform.

> **bigboy7foru said:**
> yes i read them all i just want the basic rip and burn type player with a nice looking libary and easy to navigate.

For rip and burn, Banshee, nice clean interface and easy to use.

---

### Post by bigboy7foru on 2009-09-16
Thanks Banshee it is lol
 
 
> **SunnyRabbiera said:**
> Well opinions will vary on what is truly the best media player for linux.
Personally for a iTunes user I suggest Banshee or even Exaile, both provide decent interfaces to work with and are simular to iTunes.
Songbird is good too, its a little heavy but it is cross platform.
 
 
 
For rip and burn, Banshee, nice clean interface and easy to use.

---

### Post by Scunnered on 2009-09-16
**LowSky**

I used Synaptic for the Wine and then loaded iTunes 9 into it. Subsequent enquiries proved Wine to be totally useless when attempting to work with iTunes.

Totally gave up on Wine. Uninstalled the lot.

I am using Ubuntu 9.04 and to that I downloaded VirtualBox 3.0.6 from their site and once that was done used an XP Home with SP2 CD to load Windows.  Then went to Apple and downloaded iTunes 9.

From what I can see it would appear to me that Apple are providing me with the package that I had earlier used when working with Wine.  What I see when I open it is the old audio book that I downloaded but would not work.  I have had a look at Apple to see what contacts can be made but it looks like I may have to try their forum. 

Accepting that I am really new to this particularly the Virtual Box I could be getting things wrong but it would appear that other than downloading iTunes and it not working I think that I am getting it right.

I will try Apple forum and see if anything develops from there although I am not holding my breath.

My thanks for your kind assistance

---

### Post by tacantara on 2009-09-16
> **Scunnered said:**
> **LowSky**

 I am using Ubuntu 9.04 and to that I downloaded VirtualBox 3.0.6 from their site and once that was done used an XP Home with SP2 CD to load Windows.  Then went to Apple and downloaded iTunes 9.

As VirtualBox was my suggestion, hopefully I can get you through this.  My installation of XP included SP3.  Every bit of software that I've added to my Windows virtual machine since has gone smoothly, including iTunes.  I'd recommend installing SP3 then try to install iTunes.  Unless, of course, there's something documented that states iTunes 9.0 will work with XP/SP2.

I hope you find this advice useful.  :)

---

### Post by Scunnered on 2009-09-16
**tacantara**

Many thanks for your reply.  I will have a look at Windows and see what I can do to get SP3.

I feel that I am very close and think if I can get a fresh iTunes download that everything might work.  Will see what comes from Apple.

---

### Post by Scunnered on 2009-09-16
Just had a look at Apple forum and find that with iTunes 9 they are attempting to out perform Microsoft Vista.  There is a lot of weeping, wailing and gnashing of teeth over there.

Looks like all of us who were forced to accept the new download are up to the neck in the odure and will have to await Apples pleasure.

Will report back when ever I have anything positive

---

### Post by Paqman on 2009-09-17
> **Scunnered said:**
> **LowSky**

I used Synaptic for the Wine and then loaded iTunes 9 into it. Subsequent enquiries proved Wine to be totally useless when attempting to work with iTunes.

Totally gave up on Wine. Uninstalled the lot.


For future reference: the [Wine App DB]("http://appdb.winehq.org/") is great. It can tell you ahead of time whether it's even worth trying to install something in Wine.

---

### Post by Scunnered on 2009-09-17
**Paqman**

There may be some merit in the Wine App DB if you are looking for a game to play. As to its predictability it is a bit hit and miss.  I initially downloaded iTunes 8.2 on the basis that it was in the top 10 silver list only to find that it did not work.

After a bit of check & double check I removed everything out from Ubuntu and restarted the whole sequence only to find that iTunes was 9 and it would not work either.

I think that iTunes and Wine are very hit and miss and can only hope that something better can be done with both.

---

### Post by Paqman on 2009-09-17
> **Scunnered said:**
> 
I think that iTunes and Wine are very hit and miss and can only hope that something better can be done with both.

Agreed. Wine is a fudge. To be honest it's amazing that it works at all, and is a testament to a lot of hard work and brilliance from the Wine devs. However, it should be viewed as a replacement for decent Linux apps. It's nice to have, but very much a last-ditch solution IMO.

To be honest, if iTunes ever did work properly on Wine, Apple would probably modify it to break it again anyway. Luckily there's very little you actually *need* iTunes for (really just certain Apple hardware).

---

### Post by Scunnered on 2009-09-17
**Paqman**

If it were not for the fact that the one major thing that I seek from the iPod can only be achieved by iTunes I would be very happy to totally ignore things.

I have been round the houses asking questions of all and sundry and it appears that there may be something being looked at with Rythmbox which if it comes to fruition will make my day.

I keep flitting back and forth to see if luck is in.

I can't see the logic of Apple opening up some of their software but keeping iTunes out of the mix. I would have thought that as the iPod is so good they would want to keep all options open to sell product.

Again my thanks for your assistance

---

### Post by R_U_Q_R_U on 2009-09-17
Is there anything that runs native linux that allows you to sync your **iPhone**? It seems that iTunes is the only software that works with the app store etc.

Thanks.

---

### Post by Paqman on 2009-09-17
> **Scunnered said:**
> 
I can't see the logic of Apple opening up some of their software but keeping iTunes out of the mix. I would have thought that as the iPod is so good they would want to keep all options open to sell product.


Apple's whole business model is built around getting the consumer to use a completely Apple-branded ecosystem. They're happiest if you're using an iPod with iTunes running on OSX on a Mac. And to be honest, if you did that i'm sure it would indeed work flawlessly.

---

### Post by 3rdalbum on 2009-09-17
> **Inferiority Complex said:**
> They're good for dealing with music cd's but not for Audiobooks where tracks 1-7 might be chapter 1 and iTunes has the ability to rip these as 1 file.  Tracks 2-12 might be chapter 2 and I prefer them ripped to 1 file... etc.

Are there any programs that can rip selected tracks like this?

Not as far as I know (I didn't know iTunes could do that either), but you can "cat" MP3s together:

```
cat track1.mp3 track2.mp3 track3.mp3 > chapter1.mp3
```

---

### Post by Simian Man on 2009-09-17
> **3rdalbum said:**
> Not as far as I know (I didn't know iTunes could do that either), but you can "cat" MP3s together:

```
cat track1.mp3 track2.mp3 track3.mp3 > chapter1.mp3
```

Wow, does that actually work??

---

### Post by SuperSonic4 on 2009-09-17
> **Simian Man said:**
> Wow, does that actually work??

Yes it does, I've done it myself.

cdparanoia can also rip multiple tracks as on. It's already very likely you have it installed too but it can be quite hard to learn.

k3b can I think but it would take a while

---

### Post by Paqman on 2009-09-17
> **Simian Man said:**
> Wow, does that actually work??

It will play, but it'll have completely messed up metadata. Works for video files too, btw.

---

### Post by achase79 on 2009-09-17
mp3wrap works better because it merges them together and fixes the metadata.

---

### Post by Iksf on 2009-09-17
I do have to agree with everyone here, unless you REALLY need to use iTunes, for some annoying rare type of iPod or something, the Linux ones pwn iTunes into the dust

---

### Post by JugglinPhil on 2009-10-03
Songbird is doing quite a good job syncing ipods, however I'm not sure about the Iphone appstore.. Another flaw is that it can't rip cds, but there are plenty of other programs out there that do the job (I use GRip).

---

