---
title: "You have 1 broken package on your system!"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by YosefKaro on 2009-12-13
Ok, I have searched through a few threads and bugs on launchpad and the solutions all seemed to be specific; not something that can be applied generally.  I get this error:

You have 1 broken package on you system!
Use the "Broken" filter to locate it.

So, I went to synaptic and chose Custom Filters, then Broken from the list.  Nothing is displayed there.  What should I do now to track down this Broken package?

-Yos

---

### Post by Zoot7 on 2009-12-13
Go into Synaptic and drop down the Edit menu and click "Fix Broken Packages", then click apply.
Most of the time broken packages are those with missing dependencies.

---

### Post by YosefKaro on 2009-12-13
It looks like the broken package has now been fixed.  Thank you.  I am having another problem that I was thinking may have been related to this one.  I will start a new thread.

-Yos

---

### Post by Zoot7 on 2009-12-13
No worries! :)

---

### Post by CeilingCrash on 2010-01-10
I had the same problem on 9.10, specifically the flash-nonfree package was broken.   The above suggestion didn't work.   But I found this on another thread and it fixed it (apologies to original poster I stole it from.)

Thought I'd repeat it here to save somebody some hunting : 

rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
dpkg --remove --force-remove-reinstreq flashplugin-nonfree
dpkg --purge --force-remove-reinstreq flashplugin-nonfree

---

### Post by CeilingCrash on 2010-01-11
Oops, let me make the above complete and correct : 

sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree

---

### Post by Zoot7 on 2010-01-11
Yeah I gather the flash .deb in the repos is broken. I installed it off the Adobe site.

---

### Post by CeilingCrash on 2010-01-11
Something messed up somewhere! :)

To be clear to others, 

my problem was the upgrade to 9.10 wouldn't complete due to broken flash package.   To get the upgrade to complete, i used the above commands to remove the bad package.

Once the upgrade to 9.10 was complete, I *avoided* the adobe site flash installation, and did it from Symantic (adobe-flash-nonfree i think.)

I expect the adobe install from the adobe site would have worked as well at this point, just giving my experience.

---

