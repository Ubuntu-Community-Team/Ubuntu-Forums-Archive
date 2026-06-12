---
title: "Some Oddity's and Ensuing Confusion"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by DGINSD on 2011-04-04
So I was doing some reading on the Linux security and decided to switch from the Firestarter configuration tool to the GUFW one while in Synaptic looking up Firestarter for removal Synaptic pulled up "xserver-xorg-video-radeo", and "xserver-xorg-video-ati" before I could finish typing "Firestarter" both of which are graphic drivers for card I don't have. Figuring I didn't need these I marked them for removal but when I did that Synaptic told me it was also going to remove "xserver-xorg-video-all" as well and that raised a red flag so I thought I should ask before continuing.

Some info about my system that may help I have a Dell Inspiron  1150 laptop with a built in Intel I855 graphics chip which the drivers for are not loaded with the default install of Ubuntu. I loaded them and all is working well. My question really is can I safely remove all these graphics drivers that don't have anything to do with my system, even the "xserver-xorg-video-all" that Synaptic wants to remove with them (and theres quite a few)?

When I found these drivers a thought popped in my head; "perhaps thats what the "Computer Janitor" is for, removing thing you don't need". So I fire it up and the only thing it has listed  to remove is "GetDeb-Repository" which seems odd it would want to remove that at all but also that theres nothing else that was on my system that needed removing?

---

### Post by 5149.5 on 2011-04-05
I noticed the same thing the other day when poking around in SPM. I ran across the noveau package and since I don't need it, I decided to remove it. One look at the list of things to be removed changed my mind in a hurry.

---

### Post by wolfen69 on 2011-04-05
I am not an expert on this matter, but as far as I know, a lot of these packages that are going to be uninstalled, don't really get uninstalled. I believe they are only referring to meta-packages. But since I have enough hard drive space, I generally stay away from uninstalling stuff. If you have the room, it doesn't hurt to leave it. It's not like in that other OS where apps all fight for your attention. Others may disagree.

---

### Post by DGINSD on 2011-04-05
> **wolfen69 said:**
> I am not an expert on this matter, but as far as I know, a lot of these packages that are going to be uninstalled, don't really get uninstalled. I believe they are only referring to meta-packages. But since I have enough hard drive space, I generally stay away from uninstalling stuff. If you have the room, it doesn't hurt to leave it. It's not like in that other OS where apps all fight for your attention. Others may disagree.

Yeah if I had the room I wouldn't care, but my HDD is only 80G to begin with 40 of which is filled with my Windows diaper changing station, not leaving a ton of room for my Ubuntu stuff. So till I either buy an new computer, HDD, or take my Windows training wheels off every byte counts.

---

