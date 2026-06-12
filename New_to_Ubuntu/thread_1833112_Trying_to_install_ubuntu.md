---
title: "Trying to install ubuntu"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by EGamerHDK on 2011-08-25
I should say that I did successfully install Ubuntu. It's running on an old Pentium 4 from dell. Thing is... the graphics are all buggy. I think it's the graphics card. What should I do?

---

### Post by FormatSeize on 2011-08-25
If you are trying to install Ubuntu 11.04 on an old Dell with a Pentium 4 processor (that processor is a single core processor in all likelihood), then your hardware will not support the OS. I have 3 older model Dells that I used to practice building computers (so I didn't waste a lot of money breaking things), and they all have single core Pentium 4 processors. They don't run any of the newer generation Linux *buntu distributions, including Ubuntu 11.04. 
 
Right now, I have 11.04 running beautifully with no graphics card on a Pentium-D processor and whatever (probably old) integrated graphics are inside that Gateway. Ubuntu 11.04 also ran fine on a AMD Athlon inside a computer that I got dirt cheap from Wal-Mart so I could test whether it was a processor/integrated graphics issue with the old Dells, and that turned out to be the case.
 
What I would recommend trying (I'm not guaranteeing that it will work, though), is trying to find a graphics acceleration card that is compatible with your motherboard (its likely PCI, so you are either going to have to find a used one or something like tigerdirect.com to find this older technology (Best Buy won't have it)). When you cut on your computer, what you see will still likely make you scream, that is, until you install the drivers for that card. That may help. I have never tried this myself because I don't like waiting on things in the mail, so I ended up just building another computer that I was sure would support Ubuntu 11.04.

---

### Post by IWantFroyo on 2011-08-25
Open the Additional Drivers app, and install any missing drivers (I'm assuming you have Internet on that computer).

Also, if you can find the make and model, do a few searches with the word "Ubuntu" in them.

---

### Post by decoherence on 2011-08-25
If the OP has a P4, he may have an AGP slot for graphics rather than PCI. AGP precedes the P4 by a couple of years.

That said, the OP should find out for sure before purchasing something.

Along with a new graphic card, be sure to stuff in as much RAM as the computer will recognize if you haven't already. That'll give you the best speed boost to money ratio.

---

### Post by safinr on 2011-08-25
I'd try this as well, try the recommended driver and restart.

> **IWantFroyo said:**
> Open the Additional Drivers app, and install any missing drivers (I'm assuming you have Internet on that computer).

Also, if you can find the make and model, do a few searches with the word "Ubuntu" in them.

---

### Post by EGamerHDK on 2011-08-25
Alright, so I'm actually using the integrated graphics/on-board graphics. If I run it in "Classic Mode (No Effects)" then it runs fine. Graphics are a "little" buggy. Do you guys recommend just using an older version of Ubuntu?

---

### Post by sandyd on 2011-08-25
> **EGamerHDK said:**
> Alright, so I'm actually using the integrated graphics/on-board graphics. If I run it in "Classic Mode (No Effects)" then it runs fine. Graphics are a "little" buggy. Do you guys recommend just using an older version of Ubuntu?
try xubuntu

---

### Post by EGamerHDK on 2011-08-27
Will do! Is it made for lower end systems? Is this the Linux I should be installing on my 10 year old laptop that I have laying around? I've only fooled around with Ubuntu 11.04 so I'm most comfortable with it, but, I guess I should definitely feel around. Thanks again.

---

### Post by canam101 on 2011-08-27
It was interesting to see these commments about 11.04 and pentium 4 computers. I have had some small problems with 11.04, but they were enough to make me drop back to 10.10, which doesn't give me problems.

The problems I had with 11.04 were patches of black that appeared where icons should have been. If I moved the cursor over them they disappeared. There was also occasional hesitation that I do not see in 10.10. I was also seeing sylpheed's main menu occasionally sort of butting into the firefox 6 menu, so that I was seeing bits of both at the same time.

Although my pc has 2 gigs of ram, and 2 3.40 gig cpus, they are Pentium 4s.

---

### Post by akand074 on 2011-08-27
> **EGamerHDK said:**
> Will do! Is it made for lower end systems? Is this the Linux I should be installing on my 10 year old laptop that I have laying around? I've only fooled around with Ubuntu 11.04 so I'm most comfortable with it, but, I guess I should definitely feel around. Thanks again.

You'd have a better experience with a low resource OS. Try Lubuntu or better yet Puppy Linux.

---

### Post by snowpine on 2011-08-27
> **EGamerHDK said:**
> Alright, so I'm actually using the integrated graphics/on-board graphics. If I run it in "Classic Mode (No Effects)" then it runs fine. Graphics are a "little" buggy. Do you guys recommend just using an older version of Ubuntu?

If you're using older integrated graphics, then just run without effects. You'll be fine. :)

One suggestion I can make is to find out exactly which graphics chipset you have using the Terminal command:

```
lspci | grep VGA
```

Once you know this information, you can use the forum Search feature for more info. Good luck! :)

---

