---
title: "Ubuntu installed on PS3, but desktop way too small (screenshot attached)"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by NOLA345 on 2010-11-04
I have searched and searched and found  numerous tutorials about resolution, etc. I am not even sure if my issue  is resolution based. So let's try this:

1) Can you first tell me what the problem is (resolution, cable connection, size, etc.)

2) Once diagnosed, can we try to figure out how to fix this problem??

Here is what I have:

PS3
Samsung DLP HD 1080 52inch ([http://www.amazon.com/Samsung-HL-T6156WX-HDTV-Widescreen-1080p/dp/B001A5ID80](http://www.amazon.com/Samsung-HL-T6156WX-HDTV-Widescreen-1080p/dp/B001A5ID80))
Simple red, white, yellow connection
Ubuntu 9.04

I  am 100% new to linux, but I know computers pretty well. I also have a  separate PC and a Mac in case I need to do something with one of those  to fix this issue. I burned the Ubuntu iso to a CD and did all the  necessary steps to get it on my PS3. As you can see in the picture, it  appears to be up and running, sans the fact that I can barely see  anything.

[[IMG]http://img109.imageshack.us/img109/6096/ubuntuscreenshot.th.jpg[/IMG]]("http://img109.imageshack.us/i/ubuntuscreenshot.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by ibizatunes on 2010-11-04
Ubuntu 9.04 is out of support
I would start again, download 10.04 LTS release
[http://phanboi.wordpress.com/2010/05/25/tutorial-ubuntu-10-04-ps3/](http://phanboi.wordpress.com/2010/05/25/tutorial-ubuntu-10-04-ps3/)

---

### Post by NOLA345 on 2010-11-04
I saw that last night as I was looking for a solution. Does that mean I won't be able to find someone to help me with the issue I am having? Is it really that complex?? 

Would I probably get the same screen issue if I had a new version???

Nice name by the way; I plan to head out there next summer for a few weeks. 

:P

---

### Post by mcduck on 2010-11-04
> **NOLA345 said:**
> I have searched and searched and found  numerous tutorials about resolution, etc. I am not even sure if my issue  is resolution based. So let's try this:

1) Can you first tell me what the problem is (resolution, cable connection, size, etc.)

2) Once diagnosed, can we try to figure out how to fix this problem??

Here is what I have:

PS3
Samsung DLP HD 1080 52inch ([http://www.amazon.com/Samsung-HL-T6156WX-HDTV-Widescreen-1080p/dp/B001A5ID80](http://www.amazon.com/Samsung-HL-T6156WX-HDTV-Widescreen-1080p/dp/B001A5ID80))
Simple red, white, yellow connection
Ubuntu 9.04

I  am 100% new to linux, but I know computers pretty well. I also have a  separate PC and a Mac in case I need to do something with one of those  to fix this issue. I burned the Ubuntu iso to a CD and did all the  necessary steps to get it on my PS3. As you can see in the picture, it  appears to be up and running, sans the fact that I can barely see  anything.

[[IMG]http://img109.imageshack.us/img109/6096/ubuntuscreenshot.th.jpg[/IMG]]("http://img109.imageshack.us/i/ubuntuscreenshot.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

The problem is your connection.

You are using composite video (the yellow cable with RCA connector) for video connection, and that only allows standard TV resolutions. Which are way too small for any desktop use.

To get decent resolution you need to use a component or ,preferably, a HDMI cable. (You'd want to do that anyway, really, composite video will not be able to give you anything even close to the image quality PS3 has.

edit: PS3 will handle progressive scan 1920x1080 resolution at 60Hz (1080p), while component video cable will only allow you interlaced 720x576@50Hz (PAL, 576i) or interlaced 640x480@60Hz (NTSC, 480i). Same limitations apply to S-Video and RGB-SCART cables, with the exception that RGB-SCART is able to handle 576i60 AKA PAL-60).

---

### Post by NOLA345 on 2010-11-04
Anyway around it just temporarily till I get the proper connection?

---

### Post by HacDan on 2010-11-04
Most likely not, the PS3 will only output @ 640 * 480 resolution over composite cables. No matter how much you change it, that's the only thing the connection supports.

---

### Post by mcduck on 2010-11-04
> **NOLA345 said:**
> Anyway around it just temporarily till I get the proper connection?

No, the cable/connection you use simply isn't physically able to transmit higher resolution.

edit: besides, a decent HDMI cable will only cost you somehting around $10/10&#8364;, and the imropvement in picture quality is insane. 

Really, composite video is the worst video connection still in existence, and even with the ages-old original Playstation switching to S-Video or SCART cable made an easily noticeable improvement in the picture sharpness and colors. Using the connector that limited image quality 16 years ago will not eaxctly let your PS3 shine. ;)

I really don't get why they still ship those cables with current-gen consoles, even leaving the cable completely out of the box would be a better choice if a 10&#8364; HDMI cable is too expensive to include in the package. At least then nobody would actually try *using* the composite cable. :D

---

### Post by NOLA345 on 2010-11-04
Looks like I'm heading shopping at lunch. Can I just pick one up from Best Buy? Anything to look for besides just a regular HDMI cable??

---

### Post by mcduck on 2010-11-04
living on the other side of the world, I can't really say much about the selection in BestBuy. :D

But the general rules of buying cables should apply; thicker cable and sturdy connectors usually mean better insulations between individual wires and more durable cable. But since HDMI cables are digital, you really don't need anything expensive and unless you need longer cable than 1-2m then pretty much any cable will give you same image quality.

Just look for the cheapest HDMI cable of suitable length that doesn't look like it might break into pieces if you hold it too tight. Shouldn't cost you more than $10–$20 (I paid 8€ for the 1m cable I'm currently using).

..and believe me, you'll be happy that you bought the cable. :)

---

