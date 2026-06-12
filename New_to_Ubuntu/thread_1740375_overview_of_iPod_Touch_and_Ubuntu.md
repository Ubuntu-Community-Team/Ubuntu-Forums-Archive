---
title: "overview of iPod Touch and Ubuntu?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Allen McBride on 2011-04-26
Hi folks,

I'm thinking of switching to Ubuntu, but I have an iPod Touch. I'm having trouble getting a sense of what functionality I would sacrifice. I have seen [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone), and I have looked at several threads on this forum. I gather that I can sync music. It sounds like I could manage apps but only through the iPod itself. Other than that, I'm still in the dark. Could I put PDFs and eBooks on it (maybe with Calibre)? Sync the calendar? Sync or extract voice memos? Sync or extract photos? And which of these things require jailbreaking?

I feel like there must be a summary or FAQ somewhere with this information, but I can't find it.

Thanks!
--Allen

---

### Post by earthpigg on 2011-04-27
Assume nothing will work, ever, and consider yourself very lucky if it does.

If the possibility of a complete lack of iPod support will be the difference between your Ubuntu experience will be a positive or negative one, overall, than perhaps it is better that you hold off for now? <--- I think that is a fair line of reasoning.

EDIT: but, ya know, it might kinda sorta work until the next update from Apple, if you are lucky.

---

### Post by wolfen69 on 2011-04-27
With ubuntu 11.04 I have no problems getting music and video on my ipod touch, but I have no idea about ebooks or pdf's.

---

### Post by Allen McBride on 2011-04-27
Thank you both! earthpigg, you mention updates -- I had meant to ask whether there was a way to update iOS with Ubuntu, but it sounds like you're suggesting there probably isn't.  --Allen

---

### Post by trozamon on 2011-04-27
I have an iPod touch, and until I jailbroke it, I couldn't sync anything. Also, updating is impossible, podcast managemant is hard; I would suggest just keeping windows or dual booting if you have the hard drive space.

---

### Post by dniMretsaM on 2011-04-27
When you mount your iPod, you can click on the icon an access the /var/mobile/media folder and all of it's sub folders which means you can put books in the Books folder. I think that's where the ebooks would go. You may be able to connect to your device through SSH (needs to be jailbroken with OpenSSH installed) by going to Places -> Connect to Server... I'm not sure what you would put in, but google around. I know it's out there somewhere.

---

### Post by earthpigg on 2011-04-27
> **Allen McBride said:**
> Thank you both! earthpigg, you mention updates -- I had meant to ask whether there was a way to update iOS with Ubuntu, but it sounds like you're suggesting there probably isn't.  --Allen

I'm suggesting you [avoid updates altogether]("http://ctmason.wordpress.com/2011/04/16/ios-ipod-ipad-devices-on-linux-long-term-non-jailbreaking-solution/"). :)

---

### Post by wolfen69 on 2011-04-27
> **earthpigg said:**
> I'm suggesting you [avoid updates altogether]("http://ctmason.wordpress.com/2011/04/16/ios-ipod-ipad-devices-on-linux-long-term-non-jailbreaking-solution/"). :)

Good idea. I had to wipe out my ipod touch and reinstall iOS 3 months ago, and luckily, I got it going in 10.10 and now 11.04, but I don't plan on updating it again.

---

### Post by nothingspecial on 2011-04-27
> **Allen McBride said:**
> Thank you both! earthpigg, you mention updates -- I had meant to ask whether there was a way to update iOS with Ubuntu, but it sounds like you're suggesting there probably isn't.  --Allen

I concur with earthpigg.

Once linux/ubuntu catches up with the specific firmware you have. Never, ever update it.

Managing my families iPods on Ubuntu has been tough.

Right now one of my sons classic 160 gig and my wifes 5 gen nano work perfectly.

But my 2 other sons have newer models updated with the latest apple firmware that does't work yet and I have to use windows in a VB to manage them, which means I have to mess about with an ntfs partition on an external drive. And every time they want a new song/album on them I have to convert the stupid thing to mp3 myself because iTunes will not do that. And it's all a big fat pain in the neck.

So once the good people at libgpod catch up with their particular firmware, those iPods will never be updated again.

---

### Post by dniMretsaM on 2011-04-27
Yeah, never upgrade. If your jailbroken, you probably know that already since updating is not a good idea. And depending on your device, you may be at the maximum FW (like I'm on 4.2.1 which is the max for my iPod Touch 2G).

---

### Post by rosencrantz on 2011-04-27
The iPod model/firmware is crucial. For 3G and earlier, iPod touch support is well established.
For 4G it's a bit trickier - on a non-jailbroken device, you can access the file system with ifuse, but apparently it's still read-only, so no sync with the likes of gtkpod, banshee et al.
I lost the jailbreak when I had to restore the factory settings a few months ago, so no experience with the howtos involving jailbreak yet.
Right now I'm using a VirtualBox Windows to transfer data and music and Google sync to manage contacts and calendars.

---

### Post by dniMretsaM on 2011-04-27
I can help you with jailbraking if you need/want to so you can have more access to your device when/if you move to Linux.

---

### Post by Allen McBride on 2011-04-28
Thank you all for the help! These suggestions sound like they might be what I need in the long term. Because I need a new computer very soon, I think I'd better stick with a Mac for now. But I'll definitely dual-boot Ubuntu and try some of these ideas, and hopefully I'll be ready to make the full switch next time around. --Allen

---

