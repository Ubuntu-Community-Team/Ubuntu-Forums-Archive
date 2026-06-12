---
title: "Madwifi vs. Ndiswrapper"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Anduu on 2008-05-18
I'm pretty sure I know what kind of answer I am going to get ("It depends....") but I'll throw this out there anyway ;)

My situation...

I am currently running 32bit Ubuntu on my 64bit laptop because Madwifi doesn't support my card(Atheros 5007) under 64bit as of yet.It has come to my attention that I can get my card to work under 64bit using Ndiswrapper but I am torn.

My question...

Which method seems to work best overall?Using Madwifi my wireless performs well but is slightly lacking.I get the odd dropout here and there and slowdowns now and then.Is Ndiswrapper any more stable?Does it perform better?

I ask this because moving to 64bit Ubuntu is no trivial affair.It would mean reformatting/reinstalling and starting from scratch.I would hate to go through all the effort to discover my wireless in a worse state than it is now.

Anyone have any insight?

---

### Post by NonPermissive on 2008-05-18
I wouldn't know, but I would suggest trying the 64 bit Live CD (there is a 64 bit Live CD, right?), with Ndiswrapper for a few hours, and guaging it for yourself.

---

### Post by Anduu on 2008-05-18
> **NonPermissive said:**
> I wouldn't know, but I would suggest trying the 64 bit Live CD (there is a 64 bit Live CD, right?), with Ndiswrapper for a few hours, and guaging it for yourself.

Yes that is an option I am considering.

I am hoping however to get input for others who have used both Madwifi and Ndiswrapper and can give me their opinions on the pros/cons of each before I decide to go on an experimentation rampage lol ;)

---

### Post by Anduu on 2008-05-21
One more try...

Anyone have any experience/opinions on the madwifi vs ndiswrapper front?

---

### Post by mapes12 on 2008-05-22
I have used ndiswrapper under 7.10 with a Linux unsupported wireless card. 

As you probably know ndiswrapper uses windows drivers to enable unsupported wireless cards to work in the Linux environment.

My experience, and from what I have read on this forum that of others, ndiswrapper support can be hit and miss depending on your cards chipset.

I gave up on the ndiswrapper support because over a period of a few weeks the configuration broke down. I was spending more time trying to configure the wifi than doing anything else. I swapped wifi cards to a native Linux supported card and haven't looked back since.

This is only my experience. In truth I guess you will not know the difference on your machine unless you give both a try.  

BTW: My laptop is an IBM Thinkpad T23.

---

