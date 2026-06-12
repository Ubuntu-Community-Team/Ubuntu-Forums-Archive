---
title: "Burned another coaster"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by lwalper on 2011-07-25
I seem to be having trouble burning audio CDs. Using Brasero I have been able to burn CDRW data disks, but when I tried to burn an audio, everything looked like it was going smoothly, then, in the end I get the message "burn unsuccessful" or some such notice.

So I thought I'd try Gnome CD Master. Installed it from the repositories without any problem, but when I try to drag a wav file onto the "add file"  area I get the message that the file is somehow incompatible. An MP3 file of the same track doesn't even show up in the possible files to add for burning. This software says it uses cdrdao. Is that something I need to hunt for and add somewhere?

---

### Post by Gremlinzzz on 2011-07-25
I use gnomebaker without problems.
could be your CDs are they new cause they don't last forever:D
I was thinking rewrites then i see your coaster statement.

---

### Post by lwalper on 2011-07-25
OK, I'll try gnomebaker. No, they're standard CDs, fairly new. I buy them by the 100 and go through them fairly quickly distributing various audio materials.

I had problems while using distro 10.04, never was able to burn anything - but this OS gave me hope when I burned gparted to a CDRW.

---

### Post by XubuRoxMySox on 2011-07-25
I think alot of this has to do with hardware. Brasero almost always made coasters on my 'puter, but **[COLOR="Purple"]Xfburn[/COLOR]** works flawlessly. So does K3B if you don't mind storing all the Qt libraries it pulls in when installed.

-Robin

---

### Post by mikechant on 2011-07-25
In my experience, "burn unsuccessful" messages occurring right at the end of the process are sometimes bogus. It's worth trying the disc in an audio CD player, maybe check the start of the first track and end of the last track.

---

### Post by Gremlinzzz on 2011-07-25
> **mikechant said:**
> In my experience, "burn unsuccessful" messages occurring right at the end of the process are sometimes bogus. It's worth trying the disc in an audio CD player, maybe check the start of the first track and end of the last track.

[http://www.ehow.com/how_5062879_clean-lens-dvd-burner.html](http://www.ehow.com/how_5062879_clean-lens-dvd-burner.html)

---

### Post by Anuovis on 2011-07-25
Might be your hardware. GnomeBaker is probably far better than Brasero though. All Brasero did was ruin my CDs one after another till I stopped using it.

---

### Post by lwalper on 2011-07-25
Success!! - with K3B.

Thanks!

---

### Post by lwalper on 2011-07-25
Is there anything out there that will split a long track into several smaller equal-length tracks before burning?

---

### Post by Brushstroke on 2011-07-25
I don't get it. Everybody says they have problems with Brasero but I have never had a failed burn with it. With GnomeBaker however, almost every other disc would fail to burn, whether it was an .ISO, an audio CD, a video DVD, whatever. I ended up wasting a lot of CDs/DVDs using that program.

---

### Post by relay_man on 2011-07-25
+1  K3b

I've used K3b since 8.10 with no problems ever.

K3b will burn audio on Buffalo dung if  you can get it
to fit in the drive...

---

### Post by kelvin spratt on 2011-07-25
> **Brushstroke said:**
> I don't get it. Everybody says they have problems with Brasero but I have never had a failed burn with it. With GnomeBaker however, almost every other disc would fail to burn, whether it was an .ISO, an audio CD, a video DVD, whatever. I ended up wasting a lot of CDs/DVDs using that program.
I have also never had a problem with Brasero but i don't use cheap CD or DVD.

---

### Post by bodhi.zazen on 2011-07-25
> **Brushstroke said:**
> I don't get it. Everybody says they have problems with Brasero but I have never had a failed burn with it. With GnomeBaker however, almost every other disc would fail to burn, whether it was an .ISO, an audio CD, a video DVD, whatever. I ended up wasting a lot of CDs/DVDs using that program.

It is spotty, but if you have problems with one burner, it is worth trying another.

I find k3b has been the most reliable on my hardware, although I also have had good luck with xfburn.

I have had problems with gnome-baker and brasero.

---

