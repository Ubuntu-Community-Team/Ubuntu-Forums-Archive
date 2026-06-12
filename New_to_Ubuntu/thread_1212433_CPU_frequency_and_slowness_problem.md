---
title: "CPU frequency and slowness problem"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by HungryOcopus on 2009-07-13
Hey everyone, complete newbie to Ubuntu here. I've just installed ubuntu into a dual boot with vista, and I really love the whole opensource nature of it, I'd like to make ubuntu my default OS, but I have two big problems stopping me.

1. I use a toshiba satellite pro laptop, and as my room is hot (and i often use my laptop on the bed - no desk) it can get hot quickly. In vista I use the power saver setting and it keeps my core temp low (presumably because it doesn't use much cpu power) but in ubuntu whenever I try to use the cpu frequency thing I get a message saying it's not supported. My processor is an intel pentium dual core (1.6 each cpu I think). So in Ubuntu my comp gets incredibly hot after about 20 mins, as the cpu's are pushed to the max always.
I've browsed online to a solution, but I've not really found any kind of solution.

2. Despite ubuntu using a lot of cpu power, it runs pretty slowly, noticably in firefox. I don't have visual effects on, and I don't have many applications running at the same time. It's not my connection, because I'm comparing it to firefox in vista. Is there something obvious I'm missing to speed up ubuntu?

Thanks for any help you can give, and I hope I can start using ubuntu full time as soon as possible!

---

### Post by lovinglinux on 2009-07-13
Welcome to the forums.

I had the same problem. There is a command that fixes this, but I don't know if it works for your CPU, since it is P4 related. See post [http://ubuntuforums.org/showpost.php?p=4373214&postcount=6](http://ubuntuforums.org/showpost.php?p=4373214&postcount=6)

Nevertheless, there are several threads about similar issues:

[cpu frequency not supported](http://www.google.com/search?q=cpu frequency not supported+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) [ubuntuforums.org]  > [color=#CC0000]**Note:**[/color] when you see [ubuntuforums.org] after a link on my posts it means that I am using Google site search feature. This feature allow us to get search results only from a specific site, in this case Ubuntu Forums, by adding the string *site:ubuntuforums.org* after the keywords. This method is much better than the forum search feature, since it gives you more precise results. I usually add this to my posts when a subject is very common and already answered several times.

---

### Post by HungryOcopus on 2009-07-14
Hi, yes I searched a bit longer (and a bit smarter!) and found one fix for the cpu scaling problem. I needed to install powernowd from the synaptic manager. 

As for the slow processes, I found out I'm probably suffering from the vino server problem, and disabling remote server seems to make it a little smoother, but I still have super slow reaction from programs like firefox, compared with vista anyway, which I guess could just be a support issue. Anyway, thanks for the responses.

(I'm posting this just in case anyone else is experiencing the same problems and is too newb to delve into old posts for answers)

---

### Post by lovinglinux on 2009-07-14
> **HungryOcopus said:**
> Hi, yes I searched a bit longer (and a bit smarter!) and found one fix for the cpu scaling problem. I needed to install powernowd from the synaptic manager. 

As for the slow processes, I found out I'm probably suffering from the vino server problem, and disabling remote server seems to make it a little smoother, but I still have super slow reaction from programs like firefox, compared with vista anyway, which I guess could just be a support issue. Anyway, thanks for the responses.

(I'm posting this just in case anyone else is experiencing the same problems and is too newb to delve into old posts for answers)

Try

[Tips: Things that might improve Jaunty performance ](http://ubuntuforums.org/showthread.php?t=1152095)

[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

