---
title: "New to it all. Some basic advice please."
date: 2010-10-09
forum: New to Ubuntu
---

### Post by lm1980 on 2010-10-09
I finally did it. I installed Ubuntu after months of looking into it all. Also with XP giving me some right grief today I decided to do it.

Ubuntu all the way. Got it up and running with all my music imported, photos stored etc. managed to upload onto my ipod and more other things that are basic.

Would like some advice on basic things like; internet security...is it needed? my XP system was a pain for spyware, adware and all that.
If it is recomended to use a internet security package. Which one?

I look forward to reading your posts.

cheers

---

### Post by kroq-gar78 on 2010-10-09
when I switched, I researched some stuff on that.

If you use firefox or chrome (I like firefox; default) there is an extension called "WOT" or "Web of Trust". It just shows you trustworthiness of various websites. Also available for Windows. [mywot.com]("http://mywot.com")

Linux  is very safe virus- and spware-wise. You really don't need an antivirus software unless you transfer you files with a Win machine. The AV I use is clamAV
to install, type this in a terminal (applications => accessories => Terminal)
```
sudo apt-get install clamav
```
if you want a GUI (buttons and everything to make it look nice), type this in a terminal along with the previous command:
```
sudo apt-get install clamtk
```

Hope it helps!

---

### Post by CharlesA on 2010-10-09
You don't really need an Anti virus on Ubuntu.

I've used clamav before with nothing but false positives.

Read the thread here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by lightningfox on 2010-10-09
For security see this: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Also, to be able to play all video and audio files see this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ubunterooster on 2010-10-09
Basic safety tip: Be careful where you download your programs from. A got-to-have program from some site you never before heard of is very risky. Web Of Trust is a good step in checking those sites. In short, stick to the Software Center as much as is possible.

---

### Post by CharlesA on 2010-10-09
> **ubunterooster said:**
> Basic safety tip: Be careful where you download your programs from. A got-to-have program from some site you never before heard of is very risky. Web Of Trust is a good step in checking those sites. In short, stick to the Software Center as much as is possible.

+1. Think before you download stuff.

---

### Post by BaffledMollusc on 2010-10-09
Regarding antivirus protection, I guess it may technically be a good idea. 

Practically, though, it's probably not necessary. When I used Windows I spent huge amounts of time with AdAware, Spybot, AVI antivirus and so on, but since I moved to linux four years ago I've never run any antivirus software and never had a problem. I think you'll be fine, especially if you're behind a NAT router at home, as long as you don't download anything really suspect. And even then any trojan etc is almost certainly going to be targeted at Windows, so probably won't do anything.

I realise it's anecdotal, but no one I know who uses linux has ever suffered from malware.

Shrug. Extra security won't hurt, though!

---

### Post by Dex73 on 2010-10-09
Just wanted to mention a firewall. Ubuntu has one built in, but it's off by default.

To enable type   "sudo ufw enable"   into a command line.

To get a GUI interface type   "sudo apt-get install gufw"    in a command line.

---

### Post by lm1980 on 2010-10-10
Many thanks to you all.

I'm pretty much all setup to the extent I was with XP. I now can backup DVDs. All good.

Cheers again

---

### Post by Legendary_Bibo on 2010-10-10
Welcome to the Dark Side.

The Force is strong with this one ma'lord.

---

