---
title: "Cannot connect to Internet trouble shooting"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by LinuxTryOut on 2007-12-03
First, I am very new to Linux but I am very knowledge with Windows. I just got Ubuntu 7.10 installed last week dual booting with my Windows XP.  Well, I didnt use Linux as much as Windows. Everything worked fine for me but today, I just log in Ubuntu and found out that I can't connect to the Internet, I log in my Windows everything is fine.

Since, I am new to Linux, I really got no idea how to trouble shoot to get my internet working in Ubuntu.

If you offer some helps plz post here with detail step by step. Again, There's nothing wrong with my NIC card nor Cable modem since It works flawfless in Windows enviroment.

Thanks

---

### Post by fineas on 2007-12-03
Hi LinuxTryOut and welcome to ubuntuforums:)

First, go to system>ubuntu help center, follow the "connecting to the internet" link. There you can find some advices for your internet connection and troubleshooting. Furthermore, in this page of the help manual, there is a "Networking Basics" link in the right panel. You can find these guides in
[https://help.ubuntu.com/7.10/internet/C/index.html](https://help.ubuntu.com/7.10/internet/C/index.html) and [https://help.ubuntu.com/7.10/internet/C/basics.html](https://help.ubuntu.com/7.10/internet/C/basics.html) too

Try what is suggested there. If you still have issues with your internet connection, post again in this thread. Include as many details as you can about your connection settings and the steps you followed

---

### Post by LinuxTryOut on 2007-12-04
First of all, I would like to say thank you even though I got it fixed before I checked this thread. Anyway, I think it is good to reply to this thread so that people got the same problems like I did may find the thread to be helpful.

I found out that Ubuntu network isn't as stable as Windows. In Ubuntu, the connection frequently drops the packages that it is received from other hosts. For example, when you updating Ubuntu and when you're watching streaming movies, the connection drops very often, sometimes, I am forced to reboot the cable modem and in Windows, this rarely happens.

Another thing, I found out about Ubuntu is that, sometimes, it's just death ( I can log in but i just can't run any applications )

---

### Post by fineas on 2007-12-05
> **LinuxTryOut said:**
>  First of all, I would like to say thank you even though I got it fixed before I checked this thread. Anyway, I think it is good to reply to this thread so that people got the same problems like I did may find the thread to be helpful.

I found out that Ubuntu network isn't as stable as Windows. In Ubuntu, the connection frequently drops the packages that it is received from other hosts. For example, when you updating Ubuntu and when you're watching streaming movies, the connection drops very often, sometimes, I am forced to reboot the cable modem and in Windows, this rarely happens.



1) I am glad you fixed your internet connection. If you want to stabilize it, this link might be helpful [http://ubuntuforums.org/showthread.php?t=282034&highlight=dns](http://ubuntuforums.org/showthread.php?t=282034&highlight=dns). I don't know anything about the inability to run applications in your session 

2) I haven't found any research that compares the stability of ubuntu and windows networking yet, so I don't have strong evidence to favorite any OS's networking. If you did your own research, it would be useful to post the experimental design you followed, especially the sample size. 


3) Same applies to your conclusion about the package dropping. 

We could easily set up an experiment to see whether the claim that the connection frequently drops the packages that are received from other hosts is correct. Using your example, we can choose a random sample of ubuntu users (50 could be enough), and ask them to watch streaming movies while updating. Then we can count the cases that their internet connection failed during this process. If the proportion of fails vs cases tested is significantly smaller than 10% (I might accept different number if you insist), we can dismiiss your claim as a biased comment of a person who ignores what is happening to ubuntu users.

4) If someone has problems with internet connection or anything else and reads _your opinions_ (I explained why I cannot accept them as facts), he/she willl have nothing to gain. It is better for him/her to open the manual, google for threads or guides that might provide solution and post about his/her problem in the forums, or ask a friend. If he/she had paid for support, he/she can call for. This method applies to both ubuntu and windows and any other OS.

---

### Post by rustybronco on 2007-12-05
> 
We could easily set up an experiment to see whether the claim that the connection frequently drops the packages that are received from other hosts is correct. Using your example, we can choose a random sample of ubuntu users (50 could be enough), and ask them to watch streaming movies while updating. Then we can count the cases that their internet connection failed during this process. If the proportion of fails vs cases tested is significantly smaller than 10% (I might accept different number if you insist), we can dismiiss your claim as a biased comment of a person who ignores what is happening to ubuntu users.

4) If someone has problems with internet connection or anything else and reads _your opinions_ (I explained why I cannot accept them as facts), he/she willl have nothing to gain. It is better for him/her to open the manual, google for threads or guides that might provide solution and post about his/her problem in the forums, or ask a friend. If he/she had paid for support, he/she can call for. This method applies to both ubuntu and windows and any other OS. +1

---

