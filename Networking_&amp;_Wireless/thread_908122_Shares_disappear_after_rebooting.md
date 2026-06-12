---
title: "Shares disappear after rebooting"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by armyturtle on 2008-09-02
Hi,

I really like Hardy Heron and how easy it is to set a share up by right clicking a folder.  I do so and can easily access the files over my network from any computer. 

The problem is when I reboot Hardy Heron, all my shares disappear until I manually set them up again.

I've searched and searched this forum (specifically the networking & wireless forum) for this particular issue but cannot find anything like this.

What's going on here and how do I make my network shares STICK?

Thanks in advance!

---

### Post by Iowan on 2008-09-02
Depending on what kind of shares you mean, try [this]("http://ubuntuforums.org/showthread.php?t=288534") one.  Otherwise, while there, check some of the other links in **dmizer**'s signature.

---

### Post by armyturtle on 2008-09-02
Hey thanks for the post, thoughts, & links.  I will definitely check them out: IF I can't find an easier solution here.

What I'm interested in is the nice new feature included in Hardy Heron that allows you to RIGHT CLICK just about ANY folder and choose to SHARE it on your local network.  

I don't mind CLI if I have to, but if there's a nice GUI that let's me say, "SHARE THIS FOLDER ON NETWORK" then I'd rather take that route.  It does work, very well indeed too!  That is until I reboot my machine.  When Ubuntu Hardy Heron starts back up the folders I've right-clicked on and chose to share on the network have all returned to UNSHARED status.  

So the feature is cool, but it doesn't make a whole hell of a lot of sense to include this feature if it's only good until my machine loses power or gets rebooted.

So anyone have any ideas why this is happening?  I can't imagine this is what they intended to do when they wanted to simplify sharing folders in the properties tab.???

---

### Post by armyturtle on 2008-09-04
Hello?  Anyone out there have any ideas?  I found the software package that I'm using (built into 8.04 Hardy Heron) is called "Nautilus"

This package is supposed to allow for simple file sharing by right clicking a folder and sharing on the network.  

So why does anything I share through this disappear upon rebooting the machine?

Please help!  I am about 10 minutes away from just putting windows on this damn PC to share drives on it.

---

### Post by armyturtle on 2008-09-06
Are you serious?  No one knows what the hell I'm talking about?

---

### Post by Sir_Ty on 2009-04-05
I just had the same question but I think I solved it.  The drives which actually contain the shared folders aren't automatically mounted.  So if I mount those (places, removable media, click the drive) then the shares return.  Since these drives are in removable bays, I really have no desire to change the behavior. But perhaps this is the same issue you are having army?

(Perhaps not, I just realized I'm running 8.10 and you are probably running 8.04. That being said, I think the shares are permanent now even after reboots.)

---

