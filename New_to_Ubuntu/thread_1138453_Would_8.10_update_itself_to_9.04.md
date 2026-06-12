---
title: "Would 8.10 update itself to 9.04?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by mrapoc on 2009-04-26
If I installed 8.10 onto my computer, would it be able to update to 9.04 from within ubuntu?

Also if yes, would it save more bandwidth than downloading a 9.04 release anyway?

Cheers
mrapoc

---

### Post by mikewhatever on 2009-04-26
No, it wouldn't update, but you'll be offered an option to upgrade, and I very much doubt it will same bandwidth.

---

### Post by Didius Falco on 2009-04-26
Yes, it would update to 9.04 from 8.10. I think on the bandwidth question, I'd go with downloading and burning the iso file. That way you have it handy for reinstalls, etc.

Check with your ISP - a lot of them have a "Free Zone" with files available that don't count against your account. You may be able to get the iso from them. If you are really lucky, they may even mirror the repositories....

I hope this helps...

---

### Post by D1ZZ4ZZT3R on 2009-04-26
yes, through the update manager you can upgrade to jaunty (9.04) from intrepid (8.1). if you had hardy (8.04), you would first have to first upgrade to intrepid then, jaunty. either way, depending on your connection speed and the speed at which the servers are able to download to you, it's going to take a little time. either way, it shouldn't take much.

there's always the possibility that something might go wrong so, make sure you've got all your stuff backed up.

---

### Post by D1ZZ4ZZT3R on 2009-04-26
> **Didius Falco said:**
> Check with your ISP - a lot of them have a "Free Zone" with files available that don't count against your account. You may be able to get the iso from them. If you are really lucky, they may even mirror the repositories....


wat!? i don't get what you're saying there. a 'free zone' that doesn't count against your account? are you talking an isp that limits bandwidth? i ask because mine doesn't. are some isp's doing that now? if so, aren't there other isp's you can use instead?

---

### Post by johnwillis on 2009-04-26
My previous experience has been to always keep your /home directory on a different partition and then generate an auto download list using Synaptic (the package manager) that way you get all your additional install apps re-installed quickly.

And I would ALWAYS advise on a complete reinstall from the latest CD. Anything I have done through APT (Update Manager) has always ended up with niggles further down the line...

-J

---

### Post by Didius Falco on 2009-04-26
> **D1ZZ4ZZT3R said:**
> wat!? i don't get what you're saying there. a 'free zone' that doesn't count against your account? are you talking an isp that limits bandwidth? i ask because mine doesn't. are some isp's doing that now? if so, aren't there other isp's you can use instead?

Here in Oz (Australia) there are two kinds of broadband accounts available to people who don't have a rich, dead uncle or a winning lottery ticket:

1. Accounts that allot a certain amount of bandwidth and then charge you through the nose for overages.

2. Accounts that allot a certain amount of bandwidth and then throttle your speed way back.

I have account type 2 - I get 12 Gigs a month. If I exceed the 12 gigs, my download speed drops to a measly 64kbs.

We have the worst internet service of any industrialized country at present. The Labor government is now getting ready to build a new network, that is supposed to be operational by 2012.

---

### Post by mrapoc on 2009-04-26
So its pretty much worth reinstalling from disk then?

Lots of setting up over and over for ubuntu users then?

Now iv just gotta get some instructions on setting it up either on my raid0 or to dual boot it 

[http://ubuntuforums.org/showthread.php?p=7152140#post7152140](http://ubuntuforums.org/showthread.php?p=7152140#post7152140)

Thanks all

---

### Post by D1ZZ4ZZT3R on 2009-04-26
didius - that's messed up. also, what's a labor government?

mrapoc - just be careful. i had intrepid set up with  / (root), swap, and home partitions. after installing jaunty from disk, when i go to places and (let's say) pictures, there's nothing in there. same with videos etc. my previous home partition needs a password to access so it can get mounted and then, i can access all my files. they don't show up where they're supposed to. i think i messed up during install because i'd like to think ubuntu is smarter than that. now, i have to figure out how to repartition it so everything shows where it's supposed to. i got gparted, now i have to learn how to use it.

be careful, back everything up.

---

### Post by mrapoc on 2009-04-26
Sounds similar to the UK

You get really crappy service with "unlimited" providers with throttling and the like

Or what iv done

Go with a decent one which sets out say 30gb a month, its yours no throttling

And anywhere inbetween

2012 we are "supposed" to all have at least 2mbps which is pretty shoddy. Im lucky, i can get 8mbps which is only just becoming average where i live

---

### Post by johnwillis on 2009-04-26
It is worth noting that although it is good to reinstall from the disc it is not essential. However experience will probably teach you a clean install is best...

I always ask myself this... when can you remember a Windows upgrade going well....

There's your answer...

As for you RAID, be very careful I have used that under 8.10 and had some issues...

Also if you want to stop reinstalls then you can always stick with the LTS version (currently Hardy) - however I prefer to be with the current stable version on all my desktops... Hardy only sits on my server...

-J

---

### Post by Didius Falco on 2009-04-26
> **mrapoc said:**
> So its pretty much worth reinstalling from disk then?

Lots of setting up over and over for ubuntu users then?

I'd say it was worth it. Back up your data and you can skip right over 8.10 to 9.04. Lots of Ubuntu veterans swear by fresh installs - then again, others aren't fussed with the upgrade path. Ultimately, it's down to what you are comfortable with.

I suggested the disk because I like to have a copy of it handy for troubleshooting. By using a disk and AptOnCD (an app that will save all the packages you download to cd/dvd or can even save it as an iso file you cab burn when/if needed)  you can save yourself a lot of updating time. 

As for the "lots of reinstalls", that depends on the user. I like to get into the "engine" and start pulling parts out and looking at them closely. That's how I learn the best, by doing, sometimes repeatedly. Sometimes, I have parts left over or broken, and have to replace the "engine". YMMV.<G>

> **D1ZZ4ZZT3R said:**
> didius - that's messed up. also, what's a labor government?

It's a political party - the Labour Party, to use the Aussie spelling. They are currently in power, so they control the government.

---

### Post by mrapoc on 2009-04-26
IS there a way to install ubuntu on one of the single disks then somehow get GRUB to "see" my raid0 partition with vista on it and be able to boot to that?

Or perhaps make it so if i dont select anything in Grub it bypasses grub and goes onto the normal windows boot sector?

---

