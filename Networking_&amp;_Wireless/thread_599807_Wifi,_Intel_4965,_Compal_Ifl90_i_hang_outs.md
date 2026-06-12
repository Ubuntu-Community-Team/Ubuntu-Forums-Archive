---
title: "Wifi, Intel 4965, Compal Ifl90 i hang outs?"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by Devilish on 2007-11-01
Hello,
I have laptop California Acess M160S ( also known as Compal IFL90 ) and a big problem.
I installed Ubuntu Gutsy, worked fine ( almost ) and the i run firefox. Wifi is working ( after installing iwlwifi i mac80211 ), opening and page and the problem - when i go on a new site it's waiting about 30 seconds and then opening the site. Its everytime when i go to the new site - when im exploring the site its completely ok. I tried also Opera -> same.
What is the weirdest:
- ping from console -> works fine, about 76 ms
- on second computer ( windows ) -> works fine
- on windows by VMware -> works fine

Im using NetManager to connect, as I said - i installed drivers and its not the routers fault ( i checked )

Any ideas ?
Regards

---

### Post by RandomUsr on 2007-11-01
In reality, if you're using Gutsy, a Stable version of the Mac80211 was already installed. All I had to do was

sudo modprobe -r iwl3945

 sudo modprobe iwl4965

.....and it just works using WPA2

I do have some timeouts that are very few, and the card
doesn't seem to retain WPA2 after shutdown, but I'm working
on that issue. I haven't noticed a 30 wait for new sites tho.

---

### Post by Devilish on 2007-11-02
Yeah, I heard that there are not any problems with the card - i think this is my luck ;)
Maybe you have any ideas how to solve it, or how to find the error ?

---

