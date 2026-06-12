---
title: "Wireless in Edgy?"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by Georgie-o on 2006-10-19
I think Edgy is bit too edgy...  6.06 found my wireless connection everytime with two different laptops.  Edgy has no suck luck.  Did they change something in how wireless is handled?  If they did, it didn't work.

---

### Post by Georgie-o on 2006-10-20
by the way the card is an Atheros AR5005G 802.11abg NIC.

---

### Post by mjziegle on 2006-10-20
> **Georgie-o said:**
> by the way the card is an Atheros AR5005G 802.11abg NIC.

Kernel isn't compatible with the madwifi driver installed.  Compile your own and add 'madwifi' to etc/default/linux-restricted modules.  I've had to compile my own wireless driver for atheros, zydas, and ralink chipsets for edgy

check the wiki for madwifi.  it's easy enough to follow.

---

### Post by Georgie-o on 2006-10-20
You've got to be kidding!  A newer of version Ubuntu has less wirless hardware support?  An OS that can't get the internet to work is like a car without an engine.  I'm a big Unbuntu supporter and I've gotten a number of people to switch to Dapper - because it "just works" on their laptops.  A laptop without wireless is an expensive paperweight.  Someone should let the developers know that this was an ill-advised decision.:evil:

---

### Post by Georgie-o on 2006-10-20
So how the do I "compile" the drvier?  (just in case I decide to spend a few hours of fruitless frustration before giving up and just sticking with Dapper..)

---

### Post by effoff on 2006-10-20
I agree, I have tried 10 wireless cards, of all chipsets and none of them work "out of the box" with Edgy. If the final release is like this, then Edgy will suck. It will also loose half its user base (laptop users). A laptop user should not have to "compile a roll-your-own kernel for very standard and current networking support, particularly wireless. There are no excuses for this. I don't even want to hear the developers' snivellings. I can install SuSE or Mandriva or even OpenBSD in less time that it takes to read their texts.

---

### Post by newman on 2006-10-21
> **Georgie-o said:**
> You've got to be kidding!  A newer of version Ubuntu has less wirless hardware support?  An OS that can't get the internet to work is like a car without an engine.  I'm a big Unbuntu supporter and I've gotten a number of people to switch to Dapper - because it "just works" on their laptops.  A laptop without wireless is an expensive paperweight.  Someone should let the developers know that this was an ill-advised decision.:evil:


I AGREE!!!

I just spent several hours with this bullshit!
I "upgraded" from 6.06 to edgy only to re-start the computer and find NO GUI !!!
Then I spent more time downloading the edgy CD and re-installed the OS and now NO WIRELESS!!!

WTF?!!!

This is so frustrating.  I refuse to go back to windows!  I can't. I won't. But this isn't helping the linux morale. This really sucks a$$!!! How can you update or even install the system with no internet connection?!

---

### Post by mjziegle on 2006-10-21
What part of BETA software don't you understand?

---

### Post by effoff on 2006-10-21
> **mjziegle said:**
> What part of BETA software don't you understand?

You mean "Release Candidate" software, just before official release, don't you?

---

### Post by jimrz on 2006-10-22
> **mjziegle said:**
> What part of BETA software don't you understand?

this is "release candidate" NOT beta...official release is less than 1 week away and frozen...if released "as is" this is imo a huge step backwards...extemely disappointing

---

