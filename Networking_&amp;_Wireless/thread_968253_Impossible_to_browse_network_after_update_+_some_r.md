---
title: "Impossible to browse network after update + some remarks on ubuntu development"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Halbarad on 2008-11-02
Since I installed the recommended upgrades to hardy, nautilus is not able any more to browse the samba shares in other pcs connected in my local network. Same behaviour in two different ubuntu PCs (laptop and desktop) -- both of them were okay before updating. When I dual-boot the networking is alright in Windows.
What happens now is: it takes a lot even to open the Places/Network. When I get to Workgroup, the Windows shares come out blank (after waiting for one minute or so); the Ubuntu shares are not present at all. I cannot access my shares even by using smbclient, whereas I could before.

The issue is, I don't have any more free time left for playing with more Ubuntu malfunctioning, because I must work. It is alright if something does not work since the beginning; but I cannot afford that the system suddenly stops working because of a recommended upgrade -- especially if the developers had been warned about the bugs in time. But this is a long story.

There were some probs with my pc when I installed Ubuntu (mainly related to graphics and to a wireless that I don't try to use any more, and another problem about the screen of my laptop getting erratically dim) -- I have done many trials, have notified launchpad the bugs etc. Have reinstalled Ubuntu several times, because it is now a MYTH that one of the main differences between Windows and Linux is that you can understand and fix things in Linux. My experience says, everything is so awfully complicated that no one in the Ubuntu staff is able to fix many problems, not even to identify them correctly. Just read any of the Launchpad threads to get a feel of the overwhelming confusion and of the thick fog in which many issues are immersed. Some of the bugs by which my laptop is affected have been there for more than five years, very little has been done to fix them, no one exactly knows what they depend on -- alright. Some people say, different strategies for dealing with graphics, network etc. co-exist in Ubuntu, they might perhaps come to conflict sometimes. Basic changes of strategy take place without discussion, without even informing the users. The filesystem hierarchy is being altered in ways that are more or less arbitrary and highly confusing -- just see the mess they are doing with /mnt and /media.

Okay, I MIGHT be taking an unnecessarily gloomy outlook. Bt think of this. I tested the alpha of Intrepid (had some more free time then), reported that the network didn't work any more, many more people reported the same; the prob has not been fixed, on the contrary it has been extended to Hardy  right now. What I mean is: networking and a few other basic input-output functions are the railroads and the power plants of an operating system. Such stuff as Compiz fusion is just candy, it is bill gates stuff for bill gates people. That is to say: it serves NO purpose except helping people falling in love with their PC. If you wish, you can care about stuff like that only after you have got the rest working AND transparent for all users who wish to understand.

As I understand Linux, the priority is clarity (surveyability: clear hierarchy in the filesystem, in the procedures, etc.). If THIS is in danger in the present trend, just go back, take your time, develop a clear and well-structured map, even if this might mean not to output a new Ubuntu version every sixth month.
And also try to think, honestly: how would you react if, after a recommended update, XP's network suddenly and totally stopped working?

I'll keep updating, but in the meantime I get ready to migrate to Fedora.

---

