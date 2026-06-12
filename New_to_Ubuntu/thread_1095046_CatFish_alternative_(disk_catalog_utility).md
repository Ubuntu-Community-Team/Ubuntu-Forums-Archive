---
title: "CatFish alternative (disk catalog utility)"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Lawand on 2009-03-13
I used to use [CatFish]("http://www.equi4.com/catfish/index.html") as disk catalog utility in Windows (stores indexes of CDs/DVDs contents on the HDD so that I can search for something on all the discs that I have)

Now I am looking for an alternative in GNU/Linux, any ideas?

---

### Post by mister_pink on 2009-03-13
How about catfish? (theres a linux search program by the same name!) I only suggest it because its got the same name though.

In reality its built in. Go to system, preferences, search and indexing to tweak it. You can add a search applet to the panel if you want, or use the aforementioned catfish as a front end to it.

Edit: Ignore me, just reread your post and I didn't help at all. I was too keen to point out the existance of another catfish.

Edit2: Might be more useful: [http://ubuntuforums.org/showthread.php?t=342762](http://ubuntuforums.org/showthread.php?t=342762)

---

### Post by Lawand on 2009-03-13
Thanks for your help, I'm gonna try CdCat and report back.

---

### Post by mikechant on 2009-03-13
If you've got the disc space and the time to spare, a different approach is to actually rip and store all your CDs. The ripper will (typically) use freedb.org to correctly label all the CDs and tracks, so you can then search the 'catalog' just using the normal Ubuntu file search facility, but you also have all your CDs handy to play on your PC or transcode for your mp3 player etc.
I've just ripped my entire CD collection of about 250-300 discs and ripped to flac format it takes up just about 100Gb, which is not a lot these days. If you're not familiar with it, flac is the 'free lossless audio codec' which gets nearly 50% compression from raw CD/wav format with no loss of detail, and also stores ID3 tags compatable with mp3 files.
Some CDs do 'rot' eventually (about 1 in 100 in my case so far) so it is good to have an exact backup.
I use rubyripper to rip most CDs (quite fast and very accurate for CDs which don't give errors) or grip with maximum paranoia for dodgy CDs - both use cdparanoia under the hood but in different ways.

---

### Post by Lawand on 2009-03-13
That's a nice idea but as you said, it takes time and space, so I guess I'm gonna stick with using a catalog software for now, and of course I'll backup any sensitive data to be safe of disc faultiness.

BTW CdCat works good (I'm testing it on Windows currently, but I'll be the same on Linux since it's based on Qt), and my problem is solved :)

Thanks everyone!

---

### Post by binbash on 2009-03-13
I am using gnome catalog and it is awesome :)

---

### Post by meho_r on 2009-03-17
> **binbash said:**
> I am using gnome catalog and it is awesome :)

One of the buggiest apps I've ever seen :( Too bad...

---

### Post by binbash on 2009-03-17
> **meho_r said:**
> One of the buggiest apps I've ever seen :( Too bad...

I made a catalog over 400 dvds and i did not see anything annoying or a bug.

---

### Post by meho_r on 2009-03-18
> **binbash said:**
> I made a catalog over 400 dvds and i did not see anything annoying or a bug.

I'm glad for you. Here are couple of them:

1. From time to time (not long time) it simply ignores my cd drive and add my hard disk partition to catalog instead. I can't do anything to fix it, preferences although set right don't change anything. Even restart of gnome catalog almost never helps. It's stuck.

2. When doing "Add > Catalog", you get a new folder. You click on name to rename it -- OK. But if you try to click again to rename it, doesn't work sometimes. And when you use the window "Disk or catalog information", set name there, try to click on OK, nothing happens. All you can do is click on "Cancel" to close the window (yes, I am aware of "Right Click > Rename")

3. When after doing above (adding a catalog/folder) you add a new disk, misteriously, your folder gets renamed to "No name". If you have more folders inside one another, all pop out and all have "No name" label. Same for disks in folders -- they get out too.

4. Sometimes gnome catalog refuses to even do the scan of CD/DVD. It spins it and happens -- nothing.

5. "Delete" from menu doesn't work at all. Only the button "Delete" can do what it's intended to do.

Those are some of bugs I can recall. I'm using Ubuntu 8.10 64bit, Gnome Catalog from repos v.0.3.4. Still, I really like this app although simple operation of adding a disk can be tedious. Hope authors would improve it in future...

BTW, please if you have time try doing abovementioned steps to see if you can reproduce any of bugs. If not, it is then possible that they appear on my system only (maybe something is messed up without me being aware of it).

---

