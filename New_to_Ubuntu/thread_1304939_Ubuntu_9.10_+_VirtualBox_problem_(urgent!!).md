---
title: "Ubuntu 9.10 + VirtualBox problem (urgent!!)"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by akiratheoni on 2009-10-29
I have a project due in an hour and I need to be able to access my Windows .vdi so I can grab my project.

But I have no internet connection on my new 9.10 install and I need to install VirtualBox. I downloaded the .deb but it still requires the "libq4-network" dependency. I don't want to go into a dependency hell and install thirty different libraries. What I need is a .deb or a package that contains all of the dependencies since I don't have time to search for everything that VirtualBox needs. Or the other solution is to fix my internet connection (not going to happen)

Remember I have no internet connection so Synaptic is not an option for me. Thanks!

---

### Post by Temposs on 2009-10-29
I think you're gonna be out of luck in this case, my friend.

With such an important production-level need you have right now, you should have waited to upgrade until after your assignment was due.

It's well known that new versions of massively complex software often have critical bugs that were uncaught before release, as in your case. So, in the future, wait until you have nothing better to do than possibly fix stuff in Ubuntu, or wait until it gets more stable(like in a week, or a month, depending on your willingness to take a risk).

---

### Post by akiratheoni on 2009-10-29
Yeah it was a mistake but I assumed that Ubuntu 9.10 would be agreeable with my wireless card (I was wrong) especially since it worked in Jaunty.

So there's no way to get VirtualBox installed on my system without an internet connection? That's all I need since the .vdi is still there on my hard drive, I just need to be able to read it.

The funniest part is that this was an essay about open source software... haha. I still have a bit of time so I guess I'll just rewrite my essay really fast.

---

### Post by Temposs on 2009-10-29
> **akiratheoni said:**
> Yeah it was a mistake but I assumed that Ubuntu 9.10 would be agreeable with my wireless card (I was wrong) especially since it worked in Jaunty.

So there's no way to get VirtualBox installed on my system without an internet connection? That's all I need since the .vdi is still there on my hard drive, I just need to be able to read it.

Well, you can go through "dependency hell" if you'd like. I'm not sure what all the dependencies are for Virtualbox. But yeah, that's the way you can get it installed.

---

### Post by KIAaze on 2009-10-29
> **akiratheoni said:**
> 
But I have no internet connection on my new 9.10 install and I need to install VirtualBox. I downloaded the .deb but it still requires the "libq4-network" dependency. I don't want to go into a dependency hell and install thirty different libraries. What I need is a .deb or a package that contains all of the dependencies since I don't have time to search for everything that VirtualBox needs.

=> [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

If you have a separate home partition, you could also quickly reinstall an older version of ubuntu with which your wireless card worked out of the box (if that ever was the case).

Or you can install it on another partition if you have a free one.

What wireless card do you have anyway? Maybe someone knows how to get it to work under Karmic.

---

### Post by tacantara on 2009-10-29
I feel your pain, akiratheoni.  I too upgraded to Karmic, only to find my wireless no longer worked.  I was, however, able to connect directly to my router via my ethernet card.  If you're at home and have a CAT5 cable handy, you can try that.

---

### Post by KIAaze on 2009-10-29
Quick google result:
[http://www.raiden.net/?cat=2&aid=461](http://www.raiden.net/?cat=2&aid=461)
[http://forums.virtualbox.org/viewtopic.php?t=4748](http://forums.virtualbox.org/viewtopic.php?t=4748)
:)

edit: Mmh, nope, first one requires VirtualBox to find an offset number and second one only offers Windows installer... :/

---

### Post by akiratheoni on 2009-10-29
Hey guys thanks for the help :) I'm rewriting my essay, but I still need the help to reinstall VirtualBox without an internet connection, but it's not as urgent as before.

> **KIAaze said:**
> => [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

If you have a separate home partition, you could also quickly reinstall an older version of ubuntu with which your wireless card worked out of the box (if that ever was the case).

Or you can install it on another partition if you have a free one.

What wireless card do you have anyway? Maybe someone knows how to get it to work under Karmic.
Yeah Jaunty recognized my wireless card but since I'm no longer in a super urgent situation I think I can wait for a fix. My wireless card is a Belkin N1 Wireless USB Adapter; I posted a topic about it about an hour ago but no one's replied.

> **tacantara said:**
> I feel your pain, akiratheoni.  I too upgraded to Karmic, only to find my wireless no longer worked.  I was, however, able to connect directly to my router via my ethernet card.  If you're at home and have a CAT5 cable handy, you can try that.
Unfortunately I'm living in my dorm right now. The reason why I got the wireless card was because the ethernet jack in my dorm isn't functional haha.

---

### Post by anewguy on 2009-10-29
I had the same dependency problem when I installed in 9.04.  Fortunately, that actually was the only dependency I needed.  Since you obviously have access to the net, you should download the .deb for the lib, copy it to a transferable media like a USB stick, and load it on your Ubuntu box.

Also note, I don't know what specific wireless you may have, but there are a couple of added files in the blacklist folder - 1 is for Atheros PCI.  For that one you need to comment out the ath-pci line and reboot.  Don't know if that will help you or not.

Hopefully, more people reading this contemplating moving to 9.10 will also consider things like having a back up plan for wireless drivers, video drivers, etc., before installing, so they can always get their network and video back up if the new release doesn't support it out of the box correctly.

Dave :)

---

### Post by cariboo on 2009-10-29
Wouldn't be easier to give us the details of your wireless card, then to try to install virtualbox with out a network connection? If I remember correctly there are about 5 dependencies you need before you can install virtualbox.

If worse comes to worse you could always connect directly to your router with a network cable. To help get things working.

---

### Post by anewguy on 2009-10-29
BTW - the link for libqt4-network for karmic is:

[http://packages.ubuntu.com/karmic/libqt4-network]("http://packages.ubuntu.com/karmic/libqt4-network")

Dave :)

---

### Post by akiratheoni on 2009-10-29
> **cariboo907 said:**
> Wouldn't be easier to give us the details of your wireless card, then to try to install virtualbox with out a network connection? If I remember correctly there are about 5 dependencies you need before you can install virtualbox.

If worse comes to worse you could always connect directly to your router with a network cable. To help get things working.
Well I posted a topic about the wireless card first (ok let me correct myself, it's actually a USB adapter) several hours ago and no one responded. And unfortunately I'm on my university's connection and the ethernet jack in my room is broken so I have no option for a wired connection short of moving my desktop computer to someone's room.

I have a Belkin N1 Wireless USB Adapter which can be found here (if you want a picture and more details): [http://www.amazon.com/Belkin-Wireless-Network-USB-Adapter/dp/B000JHMJE4](http://www.amazon.com/Belkin-Wireless-Network-USB-Adapter/dp/B000JHMJE4)

And it DID work with Jaunty, though I can't remember if I had to do anything special to get it to work. I don't think I did, since the wireless adapter was why I started to use Ubuntu over Vista since Vista took awhile for the adapter to work.

Thanks for the help guys, I appreciate it.

---

### Post by cariboo on 2009-10-29
How about a link to the other thread. If your paying for a dorm room, shouldn't they fix anything that is broken?

---

### Post by akiratheoni on 2009-10-29
> **cariboo907 said:**
> How about a link to the other thread. If your paying for a dorm room, shouldn't they fix anything that is broken?
[http://ubuntuforums.org/showthread.php?t=1304892](http://ubuntuforums.org/showthread.php?t=1304892)

Yeah, they should. When I started school, I told one of the front desk people about it and they told me to file a report with the technician, then I was later told that it generally takes them three weeks to fix it, so I ended up buying a wireless adapter because I didn't want to wait the three weeks. Then the wireless adapter worked without much problems so I never bothered to get the ethernet jack fixed. Recently I was planning to finally file that report but now I have even a stronger reason to do so.

---

