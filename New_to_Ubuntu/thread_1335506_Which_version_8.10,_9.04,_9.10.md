---
title: "Which version? 8.10, 9.04, 9.10"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by fairy._.queen on 2009-11-23
Hi all!
I currently use Kubuntu Intrepid Ibex 8.10 and I'm doubtful about upgrading. In particular, I would like to know some user opinion first about certain issues.
I have already looked through the documentation, what I want is your opinion :-)

1) After upgrading from Hardy to Intrepid, my computer performanced got worse, as Intrepid requires more RAM. Is it the same for the Intrepid/Jaunty upgrading?

2) Connecting through a wireless with fixed IP required some wpa-supplicant work: is Jaunty really better on this point? Is there someone who use a fixed IP who can confirm they can just connect with NetworkManager?

3) Though I like Intrepid very much (which is the reason I kept is so far) I cant help notice it is less stable than the "unbuggable" Hardy Heron. How stable do you find Jaunty compared to Intrepid?

That's all. Thanks in advance for your replies!

---

### Post by MockY on 2009-11-23
I find Karmic (9.10) vastly more stable than the previous 2 versions. However, I DO NOT suggest that you upgrade. Do an install from scratch, just to make sure you encounter as few issues as possible. 
However, one thing to keep in mind, currently you can't share a printer with Karmic. Last time I checked, this was not fixed, but I can only hope/assume that this will be fixed with future updates.

---

### Post by fairy._.queen on 2009-11-23
Thank you very much for your reply!
Just a question, probably due to language: what do you mean with "share a printer"? Do you mean you can't print anything at all with Karmic or something else?

What about RAM? Do you find it faster or slower?

---

### Post by snowpine on 2009-11-23
Hi Fairy Queen, Intrepid 8.10 will be fully supported through April 2010, so there is no hurry to make a decision. I recommend burning a Live CD of all options you are considering, and testing each one to see which works best with your hardware.

Whichever option you choose, I always recommend a fresh install, rather than upgrading. Some Ubuntu users find reinstalling every 6 months annoying; I prefer to think of it as "housekeeping".

ps the next "long term support" release comes out in April, it might be worth waiting...

---

### Post by MockY on 2009-11-23
> **fairy._.queen said:**
> what do you mean with "share a printer"? 
You can physically install a printer just fine, but if you have multiple computers on your network that needs access to a printer as well, this becomes an issue since you can't share the installed printer with other computers.
> **fairy._.queen said:**
> What about RAM? Do you find it faster or slower?
I find it much faster. And this is both on my Core2 Duo-Intel laptops and Athlon single core desktops with GeForce.

---

### Post by james_xxx on 2009-11-23
fairy._.queen,

It might also be helpful if you could provide a rough idea of you system's specs, such as type of CPU, amount of RAM, etc.

Mocky,

Do you mind if I ask how you attempted to get printer sharing working? I have a small home network, with several Karmic machines, and 2 Jaunty machines. I have an older HP USB printer connected to a Karmic box, and all of the machines on the network are able to print to it. All I did was use the browser-based CUPS interface to configure network printing. Is this what you tried?

Thanks!

---

### Post by Old_Grey_Wolf on 2009-11-23
> **fairy._.queen said:**
> Hi all!
I currently use Kubuntu Intrepid Ibex 8.10 and I'm doubtful about upgrading. In particular, I would like to know some user opinion first about certain issues.
I have already looked through the documentation, what I want is your opinion :-)
.....

Intrepid Ibex 8.10 will continue to be supported until April 2010; therefore, you can take your time deciding on a solution. 

I have used 8.10, 9.04, and 9.10 on various computers. They all behave differently. What I experience and think about a release may vary from what you will experience.

If you had to upgrade RAM, etc. to get Intrepid Ibex to work, then your computer may be getting outdated. You could post the output of ```
sudo lshw
``` maybe someone could tell you if you would have problems with your hardware.

---

### Post by TheLions on 2009-11-23
> **MockY said:**
> You can physically install a printer just fine, but if you have multiple computers on your network that needs access to a printer as well, this becomes an issue since you can't share the installed printer with other computers.


since when?

printer sharing  is working on karmic since day one...

---

### Post by MockY on 2009-11-23
> since when?
printer sharing is working on karmic since day one...
Not for me and many others. Check out the thread below.

I have used all methods possible, but not via the web interface. I figured that would be the same as using the GUI in terms of getting it to work. I posted findings in the following thread [http://ubuntuforums.org/showthread.php?t=1313049](http://ubuntuforums.org/showthread.php?t=1313049) and saw just now that the last post addresses this. So I sure will try that when I get home. Thanks for pointing that out.

This thread turned into something else, so lets stay OT  :)

---

### Post by HeadHunter00 on 2009-11-23
get 9.10

---

### Post by Sir Jasper on 2009-11-23
Hi,

Trying out any later version you fancy, using a live CD as suggested above, is surely good advice.

I also suggest it would be ideal if you can clone your present system (say, to an external drive) so that you can clone back if you find any later version you install proves to have problems that are not readily fixable.

I use a paid cloning program after all major changes to my current version, but there are, I read in the Forum, excellent freeware alternatives. I also make backups of my Home directory using copy-and-paste, but there are also good free backup programs.

My regards

---

### Post by Zoot7 on 2009-11-23
Hardy was probably the most stable version of Ubuntu i've used in my experience, I skipped Intrepid and nearly skipped Jaunty just because it worked so well.
TBH I find Karmic just about as stable as Hardy was, plus it's a lot more snappy.

---

### Post by Cheesemill on 2009-11-23
I'd go for 8.04 or 9.10 depending on whether you want maximum stabilty (8.04) or the latest apps (9.10).

---

### Post by fairy._.queen on 2009-11-25
Thank you all guys!
Your comments were extremely useful!!!
I think I will get Karmic, after all.
Cheers!

---

