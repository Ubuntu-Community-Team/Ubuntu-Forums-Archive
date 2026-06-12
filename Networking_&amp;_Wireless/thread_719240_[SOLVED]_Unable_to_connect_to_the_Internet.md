---
title: "[SOLVED] Unable to connect to the Internet"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by labinnsw on 2008-03-08
On my hard disk I have my default installation and in a separate partition a clean installation of Gutsy Gibbon which I can overwrite at will. I recently upgraded my motherboard (P5K SE with Attansic L1 Gigabit Ethernet Adapter installed) On the clean installation all is well. But that is not my default installation. On my default installation everything seems to be in order untill I try to connect to the internet. Even though the Ethernet Adapter appears to be working, Firefox always returns the error "Firefox can't find the server at URL" (where URL is whatever URL I try to access)

The forums I have fount in Linux, Debian and Ubuntu deal with situations where either the appropriate drivers have not been installed or the user does not know how to set up the internet connection. In my case the Adapter is installed and connection is set up. For some strange reason I am still not able to connect to the internet. If this can be solved I would like to attempt it. Any assistance would be much appreciated.

---

### Post by Eiríkr on 2008-03-09
Did you install your default installation before, or after, upgrading your motherboard?

---

### Post by labinnsw on 2008-03-09
Thanks for responding Eiríkr

Another way of describing the default installation is to say that it is the permanent installation. The installation that I cannot afford to lose. As such it has been there (upgraded from time to time of course) since I started using Ubuntu about a year ago and definitely before the motherboard upgrade.

---

### Post by Eiríkr on 2008-03-09
Okay.  That means it's *highly* likely that the installed drivers and configurations no longer sufficiently correlate to your new hardware.  I would *strongly* suggest finding a way to migrate all your data and using a fresh install.  I commonly keep a separate partition just for user data (not the /home/*** folders, as these contain far too much distro-specific config data, which can be a chore when jumping to a different ship; I use my /data partition mount more like the Windows "My Documents" setup).  Anyway, chances are very high that the stumbling block you're running into is some low-level and exceedingly obscure setting.  Hunting it down might well take more time and effort than figuring out how to migrate your data.  But I could certainly be wrong.  :D

Good luck,

Eiríkr

---

### Post by labinnsw on 2008-03-09
I was thinking along exactly those lines. I know the fresh install will import my bookmarks. Do you know if there is a way I can do a simple import of everything I have in Evolution and my "Todo List"? I did not ask this in the original post because I was thinking it should be a separate thread.

---

### Post by Eiríkr on 2008-03-09
By your "Todo List" I presume you mean in Evolution?  I'm not 100% sure, but I'd start out by copying anything that looks like a [font=courier].evolution[/font] directory in your home, since I think that's where Evo stores everything.  Since you've got parallel installations, I'd try copying over from your "default" to your "fresh", boot into the "fresh", and make sure things work.  

HTH,

Eiríkr

---

### Post by labinnsw on 2008-03-10
Thanks again Eiríkr

I did eventually make the decision to migrate to a fresh installation. I will gradually move stuff over. My "Todo" list is referring to Gtodo, a standalone application. Anyway I have figured out how to retrieve my tasks.

---

### Post by Eiríkr on 2008-03-10
Excellent, good news.  I hope your migration goes smoothly; it can certainly be complicated.  If this pretty much resolves your internet connectivity issues, please also remember to mark this thread as SOLVED in the Thread Tools dropdown at the top of the page.  

Good luck with the move,

Eiríkr

---

### Post by labinnsw on 2008-03-16
Thanks for your efforts Eiríkr. Since the Ethernet adapter worked on a fresh install and since I also was having problems installing a High Point Rocket Raid 454 PCI card, (which also works perfectly on the fresh install) I figured it would probably be easier if I could find an easy way to migrate my treasured information to the fresh install.

When I tried it I was surprised at how easy it was. It was done with no loss of data, bookmarks, contacts or emails. I did not even lose my tasks list from gtodo. Since it is a fresh install, not a restoration, I had to reinstall such things as my printer, firestarter, and a few other applications. But it was an unbelievably painless experience. I am sure I will be less hesitant to go through it again if need be in the future.

For those people who are sometimes critical of Ubuntu, Mandriva could only recognize the drive it was installed on. Suse would not install and instead kept asking for a CD (obviously some other CD than the installation CD), Knoppix would not boot up because it could not find any Knoppix files. Ubuntu just installed and worked, and the live Ubuntu disk worked as well.

If anyone is interested, feel free to contact me by Email, and I will be happy to post a how to for migrating to a fresh install quickly, easily and without any loss of data.

Ubuntu, don't know how I ever lived without it.

---

