---
title: "ubuntu us mirrir running super slow!"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by fremantle on 2011-04-29
i just installed natty, so far working great w/o any bugs.

however, whenever i try to install a package, and the system has to fetch files from ubuntu archives, i found that the download speed bcomes ultra low. example, i am installing ruby, and the terminal is fetching packages at 120kbps when my internet speed is over 15mbps. i know that the issue is with ubuntu mirrors because all my other downloads are working as usual. is anyone else facing this problem?

---

### Post by Dutch70 on 2011-04-29
I believe everyone else is facing this problem. 
It's because of Natty being released yesterday, all the servers are overloaded.

Took me 3+ hours to get a 16MB update this morning @1000 B/s :P

---

### Post by earthpigg on 2011-04-29
yes, my mom does use linux :)

regarding your question: because 11.04 just came out everyone is downloading, upgrading, installing/trying new software, etc. This heavily increased load on the servers is why software updates and the like are downloading at far below normal speeds.

This happens every 6 months, whenever a new version of Ubuntu is released. If there are 500 children on a playground large enough for 50 children, you can either wait for them to clear out or use a different (& identical) playground.

Same thing here: you can wait a few days/weeks, or you can use an alternative mirror.

To use an alternative mirror in ubuntu 10.04, 10.10 or ubuntu classic in 11.04: 

close update manager, ubuntu software center, or any other package manager you have running.

system -> administration -> synaptic.

settings -> repositories.

download from -> other -> select best mirror.

it will take about 5 minutes for it to test every mirror in your country, but once done it will select the fastest one for you, and you need only accept that selection.

close synaptic when done.

if, a week or a month from now, you start seeing many '404' errors in package managers, that means that the fastest mirror from a week or a month ago is now nonexistent. do this process again to find a good mirror or just select "Main Server for [Your Country]".

(im still downloading at 600kb/s, the max speed of my connection, having using this method.)

---

### Post by sandyd on 2011-04-29
I keep on telling people....
Use apt-p2p. It allows you to use bandwidth from other computers, sort of like a p2p torrent network.

Ive downloaded the entire repo, and am apt-p2ping it at 500MiB/s over level(3), because the  100mb/s that I donated to the Ubuntu torrent (on a different ethernet port) is fully used.

I considered adding my server to the ubuntu repos, since its only used internally (the bandwidth used has no impact on its functionality), but I thought it was too much of a hassle..

---

### Post by RJ12 on 2011-04-29
> **earthpigg said:**
> yes, my mom does use linux :)

regarding your question: because 11.04 just came out everyone is downloading, upgrading, installing/trying new software, etc. This heavily increased load on the servers is why software updates and the like are downloading at far below normal speeds.

This happens every 6 months, whenever a new version of Ubuntu is released. If there are 500 children on a playground large enough for 50 children, you can either wait for them to clear out or use a different (& identical) playground.

Same thing here: you can wait a few days/weeks, or you can use an alternative mirror.

To use an alternative mirror in ubuntu 10.04, 10.10 or ubuntu classic in 11.04: 

close update manager, ubuntu software center, or any other package manager you have running.

system -> administration -> synaptic.

settings -> repositories.

download from -> other -> select best mirror.

it will take about 5 minutes for it to test every mirror in your country, but once done it will select the fastest one for you, and you need only accept that selection.

close synaptic when done.

if, a week or a month from now, you start seeing many '404' errors in package managers, that means that the fastest mirror from a week or a month ago is now nonexistent. do this process again to find a good mirror or just select "Main Server for [Your Country]".

(im still downloading at 600kb/s, the max speed of my connection, having using this method.)


Thanks! Helped a ton :)

---

