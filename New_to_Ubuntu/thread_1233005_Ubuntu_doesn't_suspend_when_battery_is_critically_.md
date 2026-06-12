---
title: "Ubuntu doesn't suspend when battery is critically low"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by zorblek on 2009-08-06
I'm running Ubuntu Jaunty with the latest updates on a Dell XPS M1210 laptop. In Power Management Preferences, I have "When battery power is critically low" set to "Suspend". But when the battery gets low, the computer just powers off with no warning. As far as I can tell, there's no attempt to suspend. It doesn't have trouble suspending at other times (though occasionally it's a little slow). I don't have this problem in Windows XP (I dual-boot).

Does anyone know what might be causing this? I'd appreciate any help.

---

### Post by Bölvaður on 2009-08-06
Is the battery in a bad shape?

The only thing I can help you out with, is recommend hibernate over suspend, as hibernate doesnt use any thing from the battery at all, but may take a little longer to activate.

---

### Post by zorblek on 2009-08-06
The battery has decent capacity - not good as new, but good enough. Unfortunately hibernate has never worked with Ubuntu on this computer.

---

### Post by hibliss on 2009-08-06
> **zorblek said:**
> The battery has decent capacity - not good as new, but good enough. Unfortunately hibernate has never worked with Ubuntu on this computer.

How big is your swap partition?

---

### Post by zorblek on 2009-08-06
> **hibliss said:**
> How big is your swap partition?

I'm not sure. How would I check?

---

### Post by binbash on 2009-08-06
sudo fdisk -l

---

### Post by zorblek on 2009-08-06
Looks like it's a little over half a gig.

---

### Post by XCan on 2009-08-06
How much RAM do you have? Your swap needs to be able to contain the contents of your ram.

---

### Post by LewRockwell on 2009-08-06
it should also be noted for general reference purposes that BIOS updating has cured power management issues previously in some applications

.

---

### Post by hibliss on 2009-08-06
The amount of swap should be a bit larger. I would go with around 2gb to be safe. All of my machines running Ubuntu hibernate with no issues, each with a 2gb swap. They have varying amounts of ram, from 1-3gb.

---

### Post by zorblek on 2009-08-06
> **hibliss said:**
> The amount of swap should be a bit larger. I would go with around 2gb to be safe. All of my machines running Ubuntu hibernate with no issues, each with a 2gb swap. They have varying amounts of ram, from 1-3gb.

How would I go about increasing it? And is this likely to help with the battery warning problem? Hibernating usually takes longer than suspending, so it doesn't seem like it would be a better option.

---

### Post by hibliss on 2009-08-06
The issue here is that when you suspend to ram, you still use battery power. When you hibernate you use none. You need to change two things:

a) the setting for what is considered "critically low"

b) hibernate instead of suspend

What is happening is even if it does have time to suspend, when the battery is that low, it might suspend to ramfor a minute or less, then just shut off due to lack of power.

---

### Post by zorblek on 2009-08-06
Ah, okay. How should I go about increasing the amount of swap?

---

### Post by hibliss on 2009-08-06
Here is a tutorial on adding a swap file -- [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?") This is more like a pagefile in Windows than a traditional Swap partition.

Increasing the swap partition can be done using gparted, if you have unformatted space on the drive.

---

### Post by Paddy Landau on 2009-08-07
> **hibliss said:**
> Increasing the swap partition can be done using gparted, if you have unformatted space on the drive.
As long as you have sufficient space, you can increase the swap file even if you don't have unformatted space on the drive.

You'll need to boot off the Live CD. Using gparted, shrink the partition that comes either just before or just after your swap, then expand your swap.

Do a full backup first! As reliable as this method is, sometimes it causes data corruption.

---

### Post by zorblek on 2009-08-08
I added more swap, which sped up my computer (thanks!) but hibernate still doesn't work. I tried using a different suspend/hibernate program, uswsusp, with no luck. When I try to hibernate, it goes to a black screen with a cursor for a moment, then locks the screen.

And I still have the battery warning problem...

---

### Post by hibliss on 2009-08-09
I am at a loss here. Not too experienced with this type of issue.

---

### Post by Tishko on 2009-08-23
Hi :),

I have exactly the same problem. The computer does not shut down cleanly as the battery reaches critical level. I have tried all possible options. I understand the difference b/n hibernate and suspend and my swap file is just fine. I am running jaunty on Dell XPS m1530. It is a clean installation of Jaunty after I messed up the first one :). I did not have this problem before.
 I appreciate your help.

 Tish

---

### Post by davidryderuk on 2009-09-07
Hi,
My eeepc didn't use to shut itself down either. However I managed to get the feature to work when I did the following.

1. Open 'gconf-editor'

2. Browse to '/apps/gnome-power-manager/general/'

3. Uncheck 'use_time_for_policy'

4. Reboot and see whether the computer will now shut itself down.

---

