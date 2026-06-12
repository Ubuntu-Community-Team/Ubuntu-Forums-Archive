---
title: "10 gigs missing from newly installed 160 HD"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by s1baker on 2011-04-02
Hi,
I just cloned a 30 gig HD to a new 160 gig HD. When I use gparted to look at the partition sizes on the new HD ( see attached ), it shows a total of only about 150 gigs. Is this supposed to be this way?

thanks

---

### Post by no2498 on 2011-04-02
linux/ubuntu gives room for sudo user
hope that helps

---

### Post by s1baker on 2011-04-02
I'm the sudo user, in fact, the only one who uses this computer, is there a way for me to see this 10 gigs and write to it?

---

### Post by coffeecat on 2011-04-02
> **s1baker said:**
> Hi,
I just cloned a 30 gig HD to a new 160 gig HD. When I use gparted to look at the partition sizes on the new HD ( see attached ), it shows a total of only about 150 gigs. Is this supposed to be this way?

It's the difference between gigabytes (GB) and gibibytes (GiB). One gigabyte = 1000 x 1000 x 1000 bytes (base 10). One gibibyte = 1024 x 1024 x 1024 bytes (base 2). Disc manufacturers use the term gigabyte to mean 1000 x 1000 x 1000 bytes. So a 160GB hard drive is equal to 149.01 GiB. Since your screenshot shows 149.05 GiB, your HD manufacturer has been generous and has given you 160.04GB!

The confusion arises because GB has traditionally been used for base 2 measurements in computer circles. But this is not strictly accurate since prefixes such as "giga" belong to the Système International:

[http://en.wikipedia.org/wiki/Systeme_International](http://en.wikipedia.org/wiki/Systeme_International)

But I'll say no more as this is a subject which can raise passions. :wink:

---

### Post by oldfred on 2011-04-02
Both my 160GB drives are 149.05GiB. Which is not GB.

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

Hard drive mfg use GB, most software uses GiB. Wait till you buy a 2TB drive and see how much you lose.

You also lose some usable space in partitions to formating and the space for the journal , and Linux usually reserves about 5% to make sure you do not crash system when full.

---

### Post by wolfen69 on 2011-04-02
Manufacturers base 1gb=1000mb. But the computer bases 1gb=1024mb. You didn't lose anything, that's just the way they do it. An 80gb drive will show up as 74gb and so on...

Edit: Sorry for not being as detailed as the posters above me. I'm just lazy sometimes.

---

### Post by Niedzwiedz on 2011-04-02
The above posts cover the answer, but, sometimes I think it fun to share our individual experiences.

I remember back when I first installed Ubuntu (after some dual boots), I had this nice new 80 GB Hitachi, man this was going to be the ultimate install of Linux ever, untouched by windows.

I spent a good day reading of people's different partition schemes. I did a nice install as to what I felt work and then freaked out; "Where did all my 'NEW' HDD go!" :confused: this just was not right! A friend of mine laughed and said; "Aliens get that part". Then he went on to explain what we see posted above.

I still try to do a re-read whenever I prepare for a new install, kinda refresh the memory.

Then I buy a new 500 GB Western Digital for a nice untouched by windows install and still wonder if I did it correct? ](*,)

---

### Post by oldfred on 2011-04-02
@Niedzwiedz

If it works it is not really wrong. My best configuration a year or two later is not correct at all. After 3 or 4 years it is really bad, but by then I buy a new drive and can start over.

I do not like /boot partitions for standard desktops. I prefer smaller / partitions, but with 500GB drive small to me is 20 or 25GB. I have used about 6GB but may use 4GB more in /tmp to write a DVD, so I want only 50% use. I also add another / or two so I can test the beta install without overwriting my working version.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by s1baker on 2011-04-02
@Niedzwiedz

I am looking at your gparted screen shot and in the upper right corner it show sda to be 465 gibs, but in the partition listings sda2 shows 465 gibs and sda7 shows 453 gibs. sda2 + sda7 equals more than the total. What's up with that?

---

### Post by Niedzwiedz on 2011-04-02
> **s1baker said:**
> @Niedzwiedz

I am looking at your gparted screen shot and in the upper right corner it show sda to be 465 gibs, but in the partition listings sda2 shows 465 gibs and sda7 shows 453 gibs. sda2 + sda7 equals more than the total. What's up with that?

That is an optical illusion; Notice to the left of sda2 there is a - you can collapse sda2 and then see a + ? What I consider "inside" sda2 will add up to the total, so sda7 it actually a part of the total of sda2.

Best I can explain;
Now Old Fred up there can probably explain this better than myself, I always like seeing his comments, unknowing to him, he who brought about:config to my attention at some point in time. But, that another story, not sure if it need another thread.

@ Old Fred;
I like that about the extra / it something never thought of, normally I use my old Emachines for new stuff, that poor old hard drive been overwritten so many times, it thinks it been reincarnated.

---

### Post by s1baker on 2011-04-02
mybad, I now see that sda7, as well as sda5 & sda6 are partitioned inside of sda2.

---

