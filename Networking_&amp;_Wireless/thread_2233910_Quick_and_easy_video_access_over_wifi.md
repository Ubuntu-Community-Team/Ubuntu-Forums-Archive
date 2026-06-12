---
title: "Quick and easy video access over wifi?"
date: 2014-07-11
forum: Networking &amp; Wireless
---

### Post by AnotherKevin on 2014-07-11
Hi all!

Hey, I'm a RN, not a 'puter whiz...  That being said, I have an extensive video and music library on my home PC.  We (the family) all have Android smart phones, smart TVs and tablets all connected to the wifi.  Is there a quick and easy way I can make the music and video available across the wifi?  Thanks.  I'm no dummy, but I have a lot of other things on my plate, too.  ANY help is appreciated...

Thanks!

Kevin

---

### Post by Bucky Ball on 2014-07-11
You mean you want to communicate from device A to device B and play device B's audio/video on device A? 

You don't say where the music and video you want to access is stored. Is it on a dedicated server/computer/hard disk/NAS, or scattered on various devices/hard drives across your home network?

---

### Post by AnotherKevin on 2014-07-11
> **Bucky Ball said:**
> You mean you want to communicate from device A to device B and play device B's audio/video on device A? 

You don't say where the music and video you want to access is stored. Is it on a dedicated server/computer/hard disk/NAS, or scattered on various devices/hard drives across your home network?


My media are all on a desktop PC with Kubuntu 14.04 on the primary drive.  I would like to access it with a web-type interface, if possible.  The devices I would like to use to access the media are all smart TVs or Android tablets/smart phones.  I'm open to other suggestions, however.

I tried using VLC, but I get into a loop where the tablet's asking for a password which is already in place.  It apparently see's the media, but doesn't access it.

---

### Post by SeijiSensei on 2014-07-11
I'd start by looking at DLNA solutions like [minidlna]("http://sharpxs.com/2012/11/24/ubuntu-12-10-media-server-howto-using-minidlna/") (in the Ubuntu repositories).  I just use NFS since all my machines are running Linux, but if you want to use phones and other clients, DLNA is probably the best choice.

---

### Post by AnotherKevin on 2014-07-12
> **SeijiSensei said:**
> I'd start by looking at DLNA solutions like [minidlna]("http://sharpxs.com/2012/11/24/ubuntu-12-10-media-server-howto-using-minidlna/") (in the Ubuntu repositories).  I just use NFS since all my machines are running Linux, but if you want to use phones and other clients, DLNA is probably the best choice.


Thanks for the response.  I'm going to jump on that suggestion and I'll let ya know how it works.  

Thanks again, SeijiSensei!

Kevin

---

### Post by AnotherKevin on 2014-07-12
Wow, [COLOR=#000000]SeijiSensei!  Worked like a charm!  Thanks...

The only issue is that only about 1/3 of my movies show in the directory.  They're all MP4s.  Kinda weird.  I have 40 movies and only about 13 show across the network.  Any idea on that?

And THANKS again...  

Kevin[/COLOR]

---

### Post by AnotherKevin on 2014-07-12
> **AnotherKevin said:**
> Wow, [COLOR=#000000]SeijiSensei!  Worked like a charm!  Thanks...

The only issue is that only about 1/3 of my movies show in the directory.  They're all MP4s.  Kinda weird.  I have 40 movies and only about 13 show across the network.  Any idea on that?

And THANKS again...  

Kevin[/COLOR]

Ah!!  So simple, I'm embarrassed!  The problem was file permissions.  However, I don't understand why some files had **read** permissions and some were **forbidden**.

In any case, I changed everything to **read** and it's all [I]working like a top!!!

[/I]Once again, my thanks to [COLOR=#000000]SeijiSensei!

[/COLOR]Kevin

---

### Post by Ben_Cunningham on 2014-07-13
You can use a Samba (don't think that will work with TV though) or your best bet, DLNA, which doesn't have as many features as Samba but should fit your purpose perfectly.

---

### Post by Bucky Ball on 2014-07-13
> **Ben_Cunningham said:**
> You can use a Samba (don't think that will work with TV though) or your best bet, DLNA, which doesn't have as many features as Samba but should fit your purpose perfectly.

OP already solved problem by using miniDLNA. Please read previous posts. ;)

---

