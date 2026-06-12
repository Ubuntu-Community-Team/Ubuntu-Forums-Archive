---
title: "[SOLVED] interpid network manager doesnt remember settings"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by tgpraveen on 2008-11-10
so i was also one of the MANY who were having probs interpid's nw manager after upgrading from hardy.

interpid forgot my prev ip address and other settings and wasnt allowing me to set them either.
so i used the soln from the site and in the interfaces file in my /etc/network 
i removed all but the top two lines
and restart and voila nm starts automatically for the first time i am able to set my ip address and dns server,etc. and all works.

but when i restart then again ubuntu forgets my net settings i dont want to set my dns and ip address every time i start.

PLEASE help me. this network manager is the best and the worst upgrade in this version.

---

### Post by Iowan on 2008-11-10
Is the solution mentioned [here]("http://ubuntuforums.org/showthread.php?t=975658") the one you tried?

---

### Post by tgpraveen on 2008-11-13
the link mentioned by u did help me and now my settings do seem to saty over reboots.
but now i am feelinng that my boot time has gone up specifically it takes around 1:50 secs to boot into ubuntu wheras for xp it takes 1:35 that with many progs on autostart in xp. i know my sys is old but still ubuntu shouldnt get beaten by xp.

why do i feel this a result of the above solution well i am not fully sure but now i seem to notice that now when ubuntu boots and the progress bar is loading then at about 10% or so(its the same position always) ubuntu gets stuck for a few secs and there aint any processor activity and then after few secs it progresses normally.

is this a true prob or just my imagination??.

---

