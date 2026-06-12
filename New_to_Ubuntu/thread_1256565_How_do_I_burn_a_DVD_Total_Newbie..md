---
title: "How do I burn a DVD? Total Newbie."
date: 2009-09-02
forum: New to Ubuntu
---

### Post by brentdavis29 on 2009-09-02
Ok. So, I am a complete newbie. I just installed Ubuntu on a computer that was gifted to me, because I wanted to start transitioning over to open-source.

There is a DVD burner already in the box that was given to me. But, I have to admit, Ubuntu isn't as easy to figure out as I thought. Maybe you could help me out? 

The drive is an HP DVD Writer 400i:

1) Do I need to install the driver or does Ubuntu have some sort of self discovery for that? If I need to install one, how do I do it?

2) From there, what do I do? Do I need take the files and create an ISO out of them? Do I just drag the files to the DVD drive icon and it will guide me? 

I swear, it shouldn't be this difficult. Thanks for the help!!!

---

### Post by oldos2er on 2009-09-02
Have you tried putting a blank DVD in the drive? Does anything happen then?

---

### Post by QIII on 2009-09-02
HP's website specifies Windows XP and 2000 SP3 (Vista would probably work, too), but does not mention Linux.

Don't worry at this point, though.  A lot of hardware works in Linux even though the OEMs don't list the OS.

As for how to burn a disk, I'd find a DVD burning app in Synaptic, read up on how it works and install it.  You might go through a few before you find one that you are comfortable with.

---

### Post by Gen2ly on 2009-09-02
Doesn't Ubuntu install Brasero? (totally unhelpful not using Ubuntu right now) :)

---

### Post by championboxes on 2009-09-02
> **Gen2ly said:**
> Doesn't Ubuntu install Brasero? (totally unhelpful not using Ubuntu right now) :)

Ubuntu comes with Brasero which is a good program also another one that I like is k3b ```
sudo aptitude install k3b
```

---

### Post by kevinatkins on 2009-09-02
Hi,

We were all newbies once, so don't worry about asking questions! I've been using Ubuntu / Windows for years, but I recently had to do some work on a Mac - and I can tell you, I was straight on the web asking for help!!

Anyway, to address your question. During installation, Ubuntu should have set everything up for your DVD writer. You don't need to install any driver software.

The next issue is what you want to do with your DVD writer. If all you want to do is write data files to DVD, simply pop a blank DVD into the drive; you'll then be asked what to do next - choose 'Open CD/DVD Creator'. A window will appear into which you can drag files, then click 'Write To Disc' and you're good to go.

If you're wanting to author video DVD's, a number of options are available, but I've got to confess I haven't tried them. I think the 'Brasero' disc burning application will do video DVDs, but I can't offer further help in that respect.

The main thing is, your burner should work fine - it's now a case of selecting the best software to accomplish what you want, and it's all available no problem.

Hope this helps!

---

### Post by brentdavis29 on 2009-09-02
Thanks for the help everybody. It's not working yet, but here's some more info in response to some of your questions:

1) When I insert a blank DVD, nothing happens at all. I've tried to put in an entirely new DVD, and still nothing happens. 

2) I'm not sure if the computer is recognizing the drive at all. When I use the File Browser, the icon of the optical drives both appear to be grey. Do you know what this means? Here's a screenshot ([link]("http://i84.photobucket.com/albums/k27/brentdavis29/Screenshot.png"))

Any more ideas?

Thanks again.

---

### Post by blackened on 2009-09-03
Try putting in a DVD that you know has data on it, like maybe a game, then go to "Computer" and see if you can browse the disk.

As for the content that you're wanting to burn: if it's just raw data files, then any old software can do that, k3b, brasero (is already installed), gnomebaker (my favorite); but if you're wanting to author video then you will need to know quite a bit about a/v editing and authoring. There's no software (except maybe DVDFab in Windows) that will hold your hand all the way through the process and let you get by without having to learn some of the intricacies of a/v. That's just the way it is.

---

### Post by brentdavis29 on 2009-09-03
Blackened

I put in my Ubuntu install disc, and it seemed to recognize it just fine. Then I put in the blank DVD, and.... nothing again. I have another piece of info though. I double clicked the DVD drive icon, and got the following message: "Unable to Mount Drive. No Media in the Drive." Here's a screenshot ([link]("http://i84.photobucket.com/albums/k27/brentdavis29/AfterInsertingBlankDVD.png")). 

So the drive seems to work (using the Ubuntu disk). But, I can't get it to work.

:(

---

### Post by oldos2er on 2009-09-03
> **brentdavis29 said:**
> Blackened

I put in my Ubuntu install disc, and it seemed to recognize it just fine. Then I put in the blank DVD, and.... nothing again. I have another piece of info though. I double clicked the DVD drive icon, and got the following message: "Unable to Mount Drive. No Media in the Drive." Here's a screenshot ([link]("http://i84.photobucket.com/albums/k27/brentdavis29/AfterInsertingBlankDVD.png")). 

So the drive seems to work (using the Ubuntu disk). But, I can't get it to work.

:(

 If you go to menus Places, Home folder, Edit, Preferences, Media, under Other media, Type:, choose blank DVD disk, Action:, Open CD/DVD creator, does it work?

---

### Post by blackened on 2009-09-03
> **brentdavis29 said:**
> Blackened

I put in my Ubuntu install disc, and it seemed to recognize it just fine. Then I put in the blank DVD, and.... nothing again. I have another piece of info though. I double clicked the DVD drive icon, and got the following message: "Unable to Mount Drive. No Media in the Drive." Here's a screenshot ([link]("http://i84.photobucket.com/albums/k27/brentdavis29/AfterInsertingBlankDVD.png")). 

So the drive seems to work (using the Ubuntu disk). But, I can't get it to work.

:(

It says that because the media that you inserted is in fact...(wait for it)... blank. It contains no data or filesystem information and so cannot be mounted.

Your drive seems to be working just fine. Try going to Accessories -> CD/DVD Creator and using that to burn some good hard data to your blank disk and see how that works out for you.

---

### Post by kansasnoob on 2009-09-03
If you're trying to create a video DVD I'd give devede a try:

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

It's in the repos:

```
sudo apt-get install devede
```

---

### Post by eddski on 2009-09-06
For oldos2
I'm having the exact same problem, and I tried your suggestion and again nothing happened. Any other way to get my writer to be recognized?

---

### Post by pi.boy.travis on 2009-09-06
> **kansasnoob said:**
> If you're trying to create a video DVD I'd give devede a try:

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

It's in the repos:

```
sudo apt-get install devede
```


+1 for DeVeDe

A customer of mine had the same drive, and it worked out of the box with Ubuntu 8.10.  You don't need to make an ISO, just use Brasero.

---

