---
title: "where does Network Manager store its network information"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by bitter_mike on 2007-12-15
Ok, so every now and again, I try to connect to my school's wireless (which is WPA Enterprise encrypted and uses TTLS authentication) and nm-applet asks me for all my network login information again. Its kind of a pain in the *** to type, so I was hoping I could get it to remember the network permanently. 

So my question is, where does NetworkManager store its information about wireless networks that it knows about? And is there a different place I can store the information that isn't going to get reset?

---

### Post by csat on 2007-12-16
Try use wicd instead and disregard about where it is kept.  Look for [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) and you can find valuable information for your Ubuntu.

---

### Post by bitter_mike on 2007-12-16
Network Manager has been good to me and I'd like to keep it. Whats so good about wicd?

---

### Post by samurailink3 on 2007-12-18
wicd was good to me, but I've since switched to network manager. I think that wicd has TONS of potential, but its not what I'm looking for right now, it still seems a bit beta-ish... very good program overall, though :)

I did have a question... where does nm-applet get its icons from? Where can I swap out the default ones? I'm guessing .icons, but I'm not sure what to call them or where its looking for them in the first place. Any help would be appreciated!

---

### Post by mutzinet on 2007-12-20
Using Wicd in this case is a bad advice, because wicd does not support WPA-enterprise, as far as I know.

---

