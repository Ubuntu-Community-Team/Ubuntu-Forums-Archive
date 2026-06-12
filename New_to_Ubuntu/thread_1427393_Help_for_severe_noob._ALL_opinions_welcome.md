---
title: "Help for severe noob. ALL opinions welcome"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Dogberri on 2010-03-11
iv always been a mac person so i dont know anything about linux/ubuntu stuff, im inthe process of reading through the pocket guide. my main delema right now is i want a comp that i can use just for ubuntu experimenting. i found one at micro center that looks like it would be ok([http://www.microcenter.com/single_product_results.phtml?product_id=0329986](http://www.microcenter.com/single_product_results.phtml?product_id=0329986))

 but im not sure how upgradeable the "non-tower" kind is. one of my main concearns is that the Integrated graphics would not be able to display in HD or very well on a good screen. Any inputs would be much appreciated. thanx

---

### Post by halitech on 2010-03-11
I've got the same machine that I gave to my father to use. Looking inside its not upgradeable from what I can remember. It does have an AGP port so you aren't stuck with the onboard graphics. Not a bad price for what you are getting but I'm sure you could find a better system on Craigs List or Kijiji for less that you can upgrade in the future. Also, I'm not sure but the ram is either SDRam or DDR, wish I could remember which one for sure.

---

### Post by RedRat on 2010-03-11
Don't know where you live, but check out some computer shops (not the big box stores like Best Buy or others) for used computers. Many times, and depending on your area, these small shops take in computers that are being replaced by businesses and refurbish them. I know I have a little repair shop nearby that carries a lot of these computers and they go for a very good price. Of course, Criag's list is not a bad idea too.

If you want more mainstream type computers, some electronic stores also sell refurbished computers by HP, Dell, etc.

At the end of the day, you might want a machine where you can buy your own video card depending on the performance and things you want to do. Don't short change yourself here, because once you get onto Linux, you will want to do more and more.

---

### Post by markemark3000gt on 2010-03-11
Before I bought a refurb, I would buy a no os system from  here: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5742468&CatId=119](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5742468&CatId=119). You would be getting twice the machine, for about $100.00 more. Plus I happen to be biased towards AMD, they have never let me down.
Edited for content.
If you just want to play around with Ubuntu, and you are running on a Mac, just install virtual box on your Mac and install Ubuntu, or any other Linux distro that you would like, it is very simple to do, and once you get used to doing it, it will even become fun.
Even though I run Ubuntu, I am always playing around with new Linux distros. 
Maybe the community here will be of help to you. Good luck on your journey towards Linux.

---

### Post by Dogberri on 2010-03-11
> **halitech said:**
> I've got the same machine that I gave to my father to use. Looking inside its not upgradeable from what I can remember. It does have an AGP port so you aren't stuck with the onboard graphics. Not a bad price for what you are getting but I'm sure you could find a better system on Craigs List or Kijiji for less that you can upgrade in the future. Also, I'm not sure but the ram is either SDRam or DDR, wish I could remember which one for sure.

ok thanks. i have been told that it doesnt take must machine power to opperate, is this true? and iv herd of people "partitoning" thier hard drives....any one have a good explanation on that? can i do that with linux?

---

### Post by Don1500 on 2010-03-11
> iv herd of people "partitoning" thier hard drives....any one have a good explanation on that? can i do that with linux? 

Not only CAN you do it in Linux, you must. Complete directions are available during installation, or you can find directions in this forum, just do a search, you'll get all the help you need.

Partitioning is the division of a physical hard drive into two or more virtual hard drives. One hard drive looks like two or more hard drives to your computer. This does not increase the size of your hard drive storage space, just divides it. (Example: a 100 gig hard drive can be divided into two 49 gig hard drives. There will be a little memory loss for overhead but in today's large drives you won't notice it.)

A typical linux install partitions a single hard drive into two partitions, one called "root" (symbol "/") and one called SWAP (no symbol). the SWAP should be approximately 2 time your ram, on the machine you described that would mean 4 gig. The rest of the drive would be for the root partition. Some people make three partitions, a 5 gig root, 4 gig SWAP and the rest in HOME (symbol "/home").

---

### Post by halitech on 2010-03-12
I've had it running on machines as low as a P300 with 128meg of ram using Puppy Linux. The lowest I've gone with a Debian based install was a P3 500 with 160meg of ram using a minimal Debian install and putting LXDE on for the desktop. Obviously it wasn't a speed demon but the people that got the machines were happy to have a working, up to date and safe computer.

---

### Post by Thomas Garman on 2010-03-12
It's not a totally bad idea, but since you are looking to experiment why not just get one of the super cheap acer netbooks from Microcenter.  I have one that I enjoy messing up with Linux experiments and it always comes back to life.  I plug a 20" monitor into it and also I use a wifi keyboard/mouse...  for $250 you can carry it anywhere.  I have it set up as a Dual Boot XP/Ubuntu box.

Fun.

---

### Post by cascade9 on 2010-03-12
> **halitech said:**
> I've got the same machine that I gave to my father to use. Looking inside its not upgradeable from what I can remember. It does have an AGP port so you aren't stuck with the onboard graphics. Not a bad price for what you are getting but I'm sure you could find a better system on Craigs List or Kijiji for less that you can upgrade in the future. Also, I'm not sure but the ram is either SDRam or DDR, wish I could remember which one for sure.
 
 +1 on the 'you could find a better system for less'. It might take some looking though, unless your lucky or know where to look. 
 
 BTW, It uses DDR1 (333Mhz). AGP is nice as an option, but its getting harder to find now, about twice as expensive to upgrade as PCIe (current standard). When you do find a card and your very limited in the choices you have. Also, that case only takes 'half-height' AGP and PCI cards, both of which can be hard to find. 

> **RedRat said:**
> Don't know where you live, but check out some computer shops (not the big box stores like Best Buy or others) for used computers. Many times, and depending on your area, these small shops take in computers that are being replaced by businesses and refurbish them. I know I have a little repair shop nearby that carries a lot of these computers and they go for a very good price. Of course, Criag's list is not a bad idea too.

If you want more mainstream type computers, some electronic stores also sell refurbished computers by HP, Dell, etc.

At the end of the day, you might want a machine where you can buy your own video card depending on the performance and things you want to do. Don't short change yourself here, because once you get onto Linux, you will want to do more and more.

Not that bad an idea on the 2nd hand 'white box' (non corporate) computers, but like refurbished 'corporate' computers (Dell, HP, Compaq, IBM, etc) they arent much cheaper than buying new these days. 

I'd avoid corporate machines, they tend to be less upgradable and far more likely to have issues if you want to upgrade. 
 
 > **markemark3000gt said:**
> Before I bought a refurb, I would buy a no os system from  here: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5742468&CatId=119](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5742468&CatId=119). You would be getting twice the machine, for about $100.00 more. Plus I happen to be biased towards AMD, they have never let me down.
  
  You could build a new machine for that cost. 

> **Dogberri said:**
> ok thanks. i have been told that it doesnt take must machine power to opperate, is this true? and iv herd of people "partitoning" thier hard drives....any one have a good explanation on that? can i do that with linux?

That P4 could actually use more power than a lot of the newer computers. P4s ran hot, and used a lot of power...a low end new computer will use similar or less electricity at full load, and because they have more processing power they then to run at lower loads so use much less electricity overall.

> **Dogberri said:**
> but im not sure how upgradeable the "non-tower" kind is. one of my main concearns is that the Integrated graphics would not be able to display in HD or very well on a good screen. Any inputs would be much appreciated. thanx

Intergrated graphics of that age should be fine for displaying normal video to a good screen (depending on your resolution), but HD could be an issue. It might be able to do 720p OK, but 1080p is probably going to be jerky, if it works at all.

---

### Post by sdpiowa on 2010-03-12
As said, you could probably find a better computer for a similar price.

You should be able to try Linux via "Boot Camp" on the Mac.

---

