---
title: "wifi trouble shooting"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by monkeybrain20122 on 2014-03-28
Hi

I have installed lubuntu for a friend. When he is in my place, wifi always work. But he says that he is unable to connect to the internet at home (he lives in a rooming house with shared wifi) He says the network is detected but he cannot connect. This is an intel wifi card as far as I remember and I didn't install any proprietary driver, it just works (in my place, that is) I told him to do as in post #7 of this thread [http://ubuntuforums.org/showthread.php?t=1618934](http://ubuntuforums.org/showthread.php?t=1618934), but he called back and said it didn't work.

I know that it is impossible for you guys to help in any concrete manner with so little information. But I am going to his place tomorrow to have a look. I would need some advice for what I should look at in a case like this (router? DNS? firmware? Doesn't seem to be a wifi card issue as he can connect in my place) and how to gather the relevant information (ifconfig?)

Thanks.

---

### Post by Bucky Ball on 2014-03-28
*Thread moved to **Networking & Wireless**.*

Unsure why you would post this in **Absolute Beginners**, monkeybrain20122. :-k You have a much better chance of getting help with this here.

When you get to your friend's place, post the result of:

```
sudo lshw -C network
```

... and we'll take it from there as you are absolutely correct; virtually impossible to help you when you are not sitting in front of the computer and it is always difficult when a poster is posting for someone else ...

What I can say, though, is if it 'just works' at your place then there is nothing wrong with the card or drivers. The command above should prove that. Most Intel cards work 'out of the box' as the drivers are generally already part of the Ubuntu kernel.  The problem will lie elsewhere, possibly with a router or how the user is attempting to connect to it.

---

### Post by monkeybrain20122 on 2014-03-29
Well turned out there was no problem. The guy has mispelled the password. :confused: Enetered the correct one and connected right the way. :)

---

### Post by Navneet_Kumar on 2014-03-29
hahaha.....there was avery difficult task....impossible to diagnose the error in such cases,,,,:D

---

