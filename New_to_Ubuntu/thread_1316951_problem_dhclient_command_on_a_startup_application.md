---
title: "problem: dhclient command on a startup application"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by leossskoy on 2009-11-06
hi!
I am a tech on our company,I have a problem on one of our pc. it seems everytime i turn on that pc it doesnt have an internet connection, or it can't get any ip because it is configured on dhcp. so i had to run in terminal the dhclient so it can get an ip.

my question is. is there any way that i can include a terminal command. that is 'dhlcient' on the startup application?..

i already create a sh file. like startme.sh inside of it-

dhclient

i already include it on startup application. but it doesnt seems to work.
is ther any other way?

thanks guys..

---

### Post by ukripper on 2009-11-06
> **leossskoy said:**
> hi!
I am a tech on our company,I have a problem on one of our pc. it seems everytime i turn on that pc it doesnt have an internet connection, or it can't get any ip because it is configured on dhcp. so i had to run in terminal the dhclient so it can get an ip.

my question is. is there any way that i can include a terminal command. that is 'dhlcient' on the startup application?..

i already create a sh file. like startme.sh inside of it-

dhclient

i already include it on startup application. but it doesnt seems to work.
is ther any other way?

thanks guys..

Why don't you make that one client to have static ip instead? And make your dhcp to ignore that ip

---

