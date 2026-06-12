---
title: "New release is not shown in my update manager"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by mmasroorali on 2009-10-29
Dear All,
The new release is out there and I can not wait to get it. But my update manager refuses to be cooperative, nothing is shown.

Then I tried, sudo do-release-upgrade -d, gksu update-manager -d again with the same result.

Please see the images.

I even tried sudo apt-get update, sudo apt-get upgrade, sudo update-manager -c, again nothing is shown.

Any advice will be appreciated.

---

### Post by tommynz1975 on 2009-10-29
a google told me 

press alt + F2
to bring up the run application
then type 

update-manager -d

and that should work.

---

### Post by dummy910 on 2009-10-29
Open Synaptic>Settings>Repositories and then click the Update Tab and make sure the Release Upgrade section at bottom of window has Normal releases selected as the option in the drop-down list(see the red point cursor in below graphic)
[ATTACH]133621[/ATTACH]

once you make the change, close that, hit the RELOAD button in Synaptic(upper left corner of program), close, then go back to your Update-Manager or terminal, and you should have the upgrade showing now.

---

### Post by mmasroorali on 2009-10-29
> **tommynz1975 said:**
> a google told me 

press alt + F2
to bring up the run application
then type 

update-manager -d

and that should work.

It did not!!!

I feel frustrated.

---

### Post by werecatomega on 2009-10-29
it should work now because for me, it didn't work until i checked at three. also, it might be easier if you use the update manager than the terminal but whichever one you want to use, you can use. hope this helped

---

### Post by coolbrook on 2009-10-29
What mirror do you have set up in your software sources?  It could be the cause of your concern.

---

### Post by running_rabbit07 on 2009-10-29
Are you using a Dell that came with Ubuntu?

A sure fire way to get the upgrade is to download the 9.10 Alternate ISO, burn it to disk. Then put the disk back in and you should get a pop-up screen offering to upgrade. That is how I installed. It goes faster that way, too. If you were to get the upgrade going without doing so, it would take forever.

---

### Post by autocrosser on 2009-10-29
> **mmasroorali said:**
> It did not!!!

I feel frustrated.

Are you using a local country mirror or the main one?  Local mirrors sometimes are as much as a day or 2 behind......

---

### Post by mmasroorali on 2009-10-29
> **dummy910 said:**
> Open Synaptic>Settings>Repositories and then click the Update Tab and make sure the Release Upgrade section at bottom of window has Normal releases selected as the option in the drop-down list(see the red point cursor in below graphic)
[ATTACH]133621[/ATTACH]

once you make the change, close that, hit the RELOAD button in Synaptic(upper left corner of program), close, then go back to your Update-Manager or terminal, and you should have the upgrade showing now.

I followed you instruction to the letter (did not have to change anything in the in Repositories though), and it did not work.

I am attaching the image.

I have upgraded my machine in the past using the same procedure without any trouble. This time the experience is frustrating for me.

---

### Post by mmasroorali on 2009-10-29
I am using the main server as software source.


I am not using a Dell that came with Ubuntu:) (Hopefully the poster meant the other way. Free computer with OS?!! May be M$ will try this someday). My Ubuntu did not come with Dell. It was downloaded from Ubuntu site.

---

### Post by running_rabbit07 on 2009-10-29
> **mmasroorali said:**
> I am using the main server as software source.


I am not using a Dell that came with Ubuntu:) (Hopefully the poster meant the other way. Free computer with OS?!! May be M$ will try this someday). My Ubuntu did not come with Dell. It was downloaded from Ubuntu site.

The only reason I asked is that I have seen a Dellbuntu system that did not have the upgrade option. 

Your best bet will be to download the alternate installer disk. 

Yes, Dell sells systems with Ubuntu instead of MS.

---

### Post by danastasio on 2009-10-29
well you dont need to do it within ubuntu itself you know, if you download the ISO and burn it to a CD, and WITHOUT shutting off your computer, stick the CD in your drive, you'll get a window that says "a volume with package information has been detected, run update manager?" click yes, and your on your way to Karmic goodness!!

also any commands that sound akin to "update-manager -d" need to be run as root

I used:
```
sudo update-manager -d
```

---

### Post by running_rabbit07 on 2009-10-29
> **danastasio said:**
> well you dont need to do it within ubuntu itself you know, if you download the ISO and burn it to a CD, and WITHOUT shutting off your computer, stick the CD in your drive, you'll get a window that says "a volume with package information has been detected, run update manager?" click yes, and your on your way to Karmic goodness!!

also any commands that sound akin to "update-manager -d" need to be run as root

I used:
```
sudo update-manager -d
```

That was probably the problem. The lack of the sudo in the earlier commend.

---

### Post by mmasroorali on 2009-10-30
> **running_rabbit07 said:**
> That was probably the problem. The lack of the sudo in the earlier commend.


I just tried sudo update-manager -d (like I tried before), without success.

Moreover, I followed more or less the same upgrade schedule for my office machine. The upgrading is happening like a charm in it.

Now I am downloading alternate iso, hope it will be of use for my home machine (the culprit).

---

### Post by danastasio on 2009-10-31
let us know how it works out for you in the end!

---

### Post by garvinrick4 on 2009-10-31
There are 325 mirrors/servers  that have updates. Some are faster than others
larger bandwidth, some are up to date some are 2 days behind some are 1 week behind.

Here is a website for you that has all the mirrors, take your pick. 

Go to Admin.  to  Software Sources  to Ubuntu software tab.  Choose other in download
from and pick the one you selected from the website you looked at that has the most
bandwidth and is up to date on the mirror. Not two days behind or a week behind. 
Hit close and should reload repositories then. 

The do your thing with control/alt/f2  and update-manager -d     

Have a nice day. 

To check your repositories  just    sudo apt-get update and will tell you name of repositories.

---

### Post by humphreybc on 2009-10-31
I had this problem at uni, basically, because I had stuff running through the uni proxy, the cdimage Ubuntu sites didn't work and never told me 9.10 was available. When I went home and disabled proxy it worked fine.

Are you behind a proxy?

---

