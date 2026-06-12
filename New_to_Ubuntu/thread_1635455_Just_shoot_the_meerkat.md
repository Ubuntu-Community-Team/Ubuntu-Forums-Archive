---
title: "Just shoot the meerkat"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by thereid on 2010-12-01
[B]There seem to be a lot of people having a similar problem to mine, with NO good answers posted  I think someone should put the meerkat to sleep, and move on to whatever is next.

Can anyone PLEASE tell me how to re-install either Hardy or karmic in my Ubuntu partition without disrupting my Win XP partition??  Anyone?[/B]



> **thereid said:**
> I posted this problem weeks ago, but I haven't got an answer that works yet...
This forum has SOOOO much information that I'm whelmed, and don't know  where to look anymore.  Hope not to waste your time if I'm in the wrong  place.

Running an IBM laptop with a P4 on a dual-boot partition with Win XP.

Ran 8.04 Hardy just fine for months.  Upgraded to 9.10 karmic with no problems.
Attempted to upgrade online to 10.10 maverick, and system now fails to boot.
I get the "circles" logo for a few seconds then a blank screen.

Would like to get back to ANY version of Ubuntu that runs; WITHOUT  corrupting my XP partition.  I have my Hardy CD, and can boot to see  (and modify?) files on the Linux partition.

Attached is my "Boot_info_script results.

Sorry to be such a noob that I need my hand held through this.  My next  system will be 100% Ubuntu, and I won't fear experimenting.

---

### Post by cariboo on 2010-12-01
I would suggest you install what ever version works for you. When you get to the partitioning stage, select the manual partitioning option, and set the partitions you want Ubuntu installed to.

As for your black screen problem, you probably need to install the restricted drivers for your graphics card. The easy way is to start in recovery mode, then at the menu select netroot. Once at the prompt type:

```
jockey-text -l
```

The above command will return a list of recommended drivers for your graphics card. To install the driver, type:

```
sudo jockey-text -e <driver>
``` 

where driver = the driver suggested by jockey-text.

---

### Post by Maelzel on 2010-12-02
Wubi makes a virtual partition for Ubuntu. Can be uninstalled through add/remove programs in Windows.

 [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by juancarlospaco on 2010-12-02
Dont kill animals unless necessary.
Dont use all Bold letters.

---

### Post by mastablasta on 2010-12-02
how did you upgrade? if you had any proprietary drivers installed you should have removed them first then upgrade then install them again if even necessary.
 
EDIT: it's alo best to first test the new system via liveCD or USB before doing the upgrade. that way you can spot possible problems and issues.

---

### Post by thereid on 2010-12-02
> **cariboo907 said:**
> I would suggest you install what ever version works for you. When you get to the partitioning stage, select the manual partitioning option, and set the partitions you want Ubuntu installed to.

As for your black screen problem, you probably need to install the restricted drivers for your graphics card. The easy way is to start in recovery mode, then at the menu select netroot. Once at the prompt type:

```
jockey-text -l
```The above command will return a list of recommended drivers for your graphics card. To install the driver, type:

```
sudo jockey-text -e <driver>
```where driver = the driver suggested by jockey-text.

[FONT=System]First: Thanks to all who replied. 

Cariboo907:
Restricted drivers for my graphics card??  Not sure what that means. I have an on-board Intel "stock" graphics driver that worked in both Hardy and karmic.  I thought that each iteration of Ubuntu would build on the last, so why would my need for graphics driver change?
Anyway; I can't even boot in recovery mode because it can't seem to find the root...it just "drops to a shell" and offers "help" commands that I don't know how to use.
(BTW: Where can I find that information?)

I will try re-installing Hardy from my original ISO disk onto the Linux partition.[/FONT]

---

### Post by thereid on 2010-12-02
> **juancarlospaco said:**
> Dont kill animals unless necessary.
Dont use all Bold letters.


I don't kill animals...I'm a vegetarian (Apparently I'm NOT a programmer).
I might make an exception for this "Malicious Meerkat" though.

The use of bold letters simply reflected my severe and utter *Frustration*.
I'm usually quite Zenful.

---

### Post by TBABill on 2010-12-02
When you select the manual partition option mentioned above, just reinstall on the SAME partition where you see Linux currently installed. It should be the one labeled as EXT3 or EXT4, depending on what you chose when you installed it. Just mark it for formatting and select to mount at / and you should be good. Just do NOT mark any others for formatting or installing!!

---

### Post by thereid on 2010-12-02
> **mastablasta said:**
> how did you upgrade? if you had any proprietary drivers installed you should have removed them first then upgrade then install them again if even necessary.
 
EDIT: it's alo best to first test the new system via liveCD or USB before doing the upgrade. that way you can spot possible problems and issues.


I upgraded online through the Ubuntu menu; first from Hardy to karmic, then (attemped) to Meerkat. I (foolishly) thought it would just give me the latest and greatest security patches and bug fixes, like a Windows update.  I didn't realize that upgrading to a newer iteration was different enough to crash my system.

If I go back and install Hardy Heron, how do I know I'm getting the latest security and bug fixes?

Where else can an "Ultra-noob" go for a primer on this stuff?

Thanks.

---

### Post by bjje on 2011-04-20
> I would suggest you install what ever version works for you. When you  get to the partitioning stage, select the manual partitioning option,  and set the partitions you want Ubuntu installed to.Is this the point where I would preserve my /home partition? (not that I don't love the meerkat but must meet natty)

---

### Post by nothingspecial on 2011-04-20
No, you need to do that first. Before you start the install process.

And you are supposed to start up a new thread.

---

