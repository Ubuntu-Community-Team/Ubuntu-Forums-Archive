---
title: "Burnt ISO Jaunty CD gives no &quot;install&quot; option"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2009-04-25
I downloaded the Jaunty Jackalope ISO image then burned it to a CD. When I put the CD into my CD drive I get the an "autorun" error after I click the "run" button. (There's only 2 options "Run" Or "Cancel)." 

Then synaptic package manager lit up and I clicked on it to open update manager. Then when I clicked on "install updates" I got a message to insert my burned Jaunty Jackalope CD. When I inserted it and clicked the "run" option again, I got same "autorun error" as above. Then when I clicked on the distribution update to upgrade to Jaunty Jackalope I again received message to insert my Jaunty Jackalope CD. Finally I chose "cancel" rather than "run" it started the distribution upgrade as if I never needed a burned live CD in the first place. 

I remember upgrading to intrepid from Hardy without the need to insert a Hardy Heron CD. What am I doing wrong? Shouldn't I get an "install" option from the (suppose to be live) CD rather than a "run" option?

I'd prefer to do a fresh install from the CD rather than use the Distribution Upgrade method which takes much much longer. 

Thanks

p.s. also I got a message that my 3rd party entries in my sources.list were disabled and that I could use a package manager to re-enable them after upgrading to Jaunty.

---

### Post by Peter09 on 2009-04-25
Try burning a new CD, it may be that the CD is faulty (quite a common problem)

---

### Post by Brian_Newbie on 2009-04-25
Thanks Peter

I think I'll probably try a new ISO download of Jaunty then try a fresh install from that new CD.

However I see that the first few files are downloading from the distribution upgrade I selected via synaptic. It's at 14 files of 1209 in "getting new packages."

Should I let this upgrade process continue until complete then perhaps it won't any longer ask me to insert a Jaunty live CD as it does now?

If it upgrades successfully, I can always do a fresh install in a couple of days from a burnt CD anyhow. I'm just afraid it won't upgrade successfully but am reluctant to cancel something already started.

Also I should close firefox soon until the upgrade is complete. 

Brian

---

### Post by zvacet on 2009-04-25
@ **Brian_Newbie**

> Shouldn't I get an "install" option from the (suppose to be live) CD 

Only upgrade from CD is from alternate CD.Look [here.]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by Peter09 on 2009-04-25
Actually I think misunderstood you, you do not need a CD if you have an Internet connection, it will all happen over that. Just leave it - DO NOT interrupt it - that causes lots of problems.

If you want to stop it asking for a CD, when the upgrade has finished go into synaptic and uncheck the CD tick box in the sources tab.

---

### Post by Brian_Newbie on 2009-04-25
I'll just leave it be and it should upgrade ok I hope. 

zvacet: That's what confused me because I did not use the alternate CD instructions. I just downloaded the ISO image from Ubuntu.com then burnt it at the slowest speed to a blank CD. Then I thought I'd get an "install" option to do a fresh install rather than the "run" option.

Thanks for your help Peter and zvacet. I'll uncheck the CD tick box in the sources tab after the upgrade completes and try a fresh install sometime later.

---

### Post by Brian_Newbie on 2009-04-25
I just finished upgrading to Jaunty to the point of fetching all of the 1209 files. However before it went automatically to the "install upgrades" section, I again am asked to insert the Jaunty CD I burned from the ISO image at Ubuntu.com. 

Is there a way I can find all the Jaunty files I just fetched from Ubuntu's upgrade servers and are presumably on my computer somewhere? 

I'd like to continue the upgrade installation process if I can - And without being asked to "insert the Jaunty CD" which only gives me two options, "run" or "cancel" and no installation option?

---

### Post by zvacet on 2009-04-25
Every package you downloaded is in /var/cache/apt/archives .

---

### Post by oldos2er on 2009-04-25
"I remember upgrading to intrepid from Hardy without the need to insert a Hardy Heron CD. What am I doing wrong?"

 If you want to do a new install, you need to boot from the LiveCD. When you do that, make sure the first thing you run from the menu is 'Check CD for defects'.

---

### Post by Brian_Newbie on 2009-04-27
Thanks to all who responded:

I found the reason why I kept getting the "run" and "cancel" options with the live CD without an "install" option.  

While I thought there must be some complex explanation for this error, it turned out I had only **selected** to boot from the CD first - but not **changed** the boot order to boot the CD first.

Those + and - signs make a whole lot of difference. lol 

Jaunty installed perfectly from the live CD with absolutely no errors at all - and works great!!! 

Brian

---

