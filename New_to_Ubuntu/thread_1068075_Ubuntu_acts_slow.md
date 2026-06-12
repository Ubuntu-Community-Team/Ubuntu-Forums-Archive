---
title: "Ubuntu acts slow"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2009-02-12
Is it just me, or is Ubuntu getting slower the more you use it? I could swear it was faster when I installed it on my netbook a little over a week ago. Windows are "delayed" when dragging, scrolling in firefox is horrible and overall system performance is unimpressive.

Now, you could say that this is because of weak hardware, but it is a eee 1000h that runs XP notably better than it runs Ubuntu.

It is not my intention to whine or anything, but I've had such great experiences with ubuntu in the past and this is really disappointing. 

Any help would be appreciated.

---

### Post by LowSky on 2009-02-12
I have a lenovo s10, which if i'm possitive is running almost the same chipsets as you. But I am also running 2GB of RAM so that helps a ton.
Seems to run everything just fine.

---

### Post by Mr.Kuchinawa on 2009-02-12
Thanks, I havee ordered a 2GB RAM chip. 

Does anybody know how I can move windows without actually watch them as I move them? as in just move the "frame"? It's hard to describe, but you can do so in windows.

Any other tips what can make both gnome and firefox more lightweight without drastically altering something or shifting to xfce would be great!

---

### Post by ibuclaw on 2009-02-12
Yeah, two questions:

1) What **Type** of hard drive does your EeePC have? (SSD / HDD)
2) What **Type** of filesystem have you used to install Ubuntu on? (ext3 / reiserfs / etc)

As it would be my recommendation for you to use the **ext2** filesystem if you use a **SSD** (Solid State Drive). Since the journal on ext3 and other soCal filesystems could potential shorten the life of it due to a higher level of disk writebacks.

In terms of speeding up Ubuntu/Firefox, there are plenty of information on the forums if you know what you are looking for.

There is an interesting blog here: [http://www.linuxhaxor.net/2008/09/30/make-linux-harder-better-faster/](http://www.linuxhaxor.net/2008/09/30/make-linux-harder-better-faster/)
that has some useful info, though I don't agree with the usage of some things enlisted there, as Ubuntu already uses it. But that is just my personal opinion.

Regards
Iain

---

### Post by Mr.Kuchinawa on 2009-02-12
Thanks. It's an HDD with ext3.

---

### Post by Bölvaður on 2009-02-12
Ubuntu doesnt slow down without a great help. So if you recall doing anything like adding some desktop effects and running games in the background I cannot see how it could happen.

You may be able to run better on your current hardware with lighter window manager and turn compiz off (Sytem &#8594; Preferences &#8594; Appearance [visual effects &#8594; none]).
xfce is quite good but if you dont need anything more than a completely empty screen and menu when you right click then openbox is for you, it is very light and you can add more things to it as you can see on peoples screenshots. I actually love "awesome" on laptops, with additional mousefree programs.

---

### Post by Mr.Kuchinawa on 2009-02-12
Compiz is not enabled, though I would like it to be (I've created another post regarding that). However, scrolling in firefox is a major problem. I don't think it's hardware related, but it's still a pain. It's way too choopy and uncontrollable.

Still - firefox' perfomance is by no means impressive otherwise.

Edit: I fixed the scrolling issue to a certian extent following this guide:
[http://www.earthv.com/tips_detail.asp?TipID=76](http://www.earthv.com/tips_detail.asp?TipID=76)

---

### Post by Mr.Kuchinawa on 2009-02-13
My new theory is that this might be related to a graphics problem, as compiz cannot be enabled. I think the problem might have occurred after I tried th vga-out, althugh that is mostly a guess.

Any way to confirm/fix this?

---

