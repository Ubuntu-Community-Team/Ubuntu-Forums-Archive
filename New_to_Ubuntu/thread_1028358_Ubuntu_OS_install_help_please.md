---
title: "Ubuntu OS install help please"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by SilverPotato on 2009-01-02
Hi everyone I'm new here at your forum. So here is my introductory paragraph.

I've been using ubuntu for a little under a week on my Laptop and I want to install it on my desktop. The only problem is I can't get the installer to recognize my partition. I made a 30GB ext3 partition for Ubuntu however it only recognizes a non-existent 320gb sata (Mine is only 300gb). Up until step 4 of 7 I get a bit freaked out that I'll wipe my hard drive. So I'd like a bit of guidance through this issue. Thanks :D

---

### Post by anjilslaire on 2009-01-02
Have you tried the "manual" partioning option? You should be able to designate which partion to install to, although your issue does sound odd...

---

### Post by SilverPotato on 2009-01-02
I'm pretty sure I tried manual but I chickened out for some reason. I'll take a quick look back and put up what its showing.

---

### Post by BenAshton24 on 2009-01-02
Maybe You have an extra 20 gigs you didn't know about?
It's difficult to suggest any ideas without actually seeing what's going on and knowing all the information... do you have an ntfs partition on it? (windows) and does it detect that? ubuntu also needs a swap partition of a few gigs on it.. so you might have to create one of those too

my suggestion is to remove the 30 gig ext3 partition and to restart ubuntu installer and select install on largest space available.

Hope this helps

Ben

---

### Post by SilverPotato on 2009-01-02
I think I might have found the problem.

When I click manual it shows my XP partition and my other partition which I changed to fat32. Should I just highlight it and click next? because the check box isn't working.

EDIT:

I formated it to ext3 and it says it needs a root file system. Which should I use?
/
/home
/boot
etc

---

### Post by sadaruwan12 on 2009-01-02
Hi,

I can understand your problem try this guide and if this solves your problem
[URL="http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron"]
http://www.howtoforge.com/.....hardy-heron[/URL]

---

