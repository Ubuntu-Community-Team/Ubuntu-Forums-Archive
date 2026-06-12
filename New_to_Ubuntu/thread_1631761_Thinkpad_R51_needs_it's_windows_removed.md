---
title: "Thinkpad R51 needs it's windows removed"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by tpr51 on 2010-11-27
HI ALL,

I installed ubuntu like 2 weeks ago just to see what all the hype was about.... 

the thing is .. in the past 2 weks I have not had a reason to boot to the XP side .. actually find myself dreading the wait it would take for it to boot and just let it auto boot into ubuntu in nothing flat!

that being said .. there are a few quirky lil things related just to the thinkpad i need to work thru such as the onscreen graphics for the volume buttons or caps lock ect...anyway heres my question for today...

the thinkpad has a recovery partition of something like 5gig...XP and all the BS it needs is on 30gig and ubuntu i gave 5gig (40 gig harddrive) 

just need one of you thinkpadders to tell me whats the best way to go about removing the XP stuff without wiping out the recovery ...just incase i go braindead and think its a good idea to return to windows at a later date..lol

is it just a simple matter of deleting that partition? or would it be better to reinstall ubuntu fresh and let it take that space from the start or ...or...??

if its something that your gonna tell me "open a terminal" ... oh boy ... i dont know squat about that part yet.. never used dos either ... i fall into the "point n click" crowd for now

anything you can throw at me about thinkpads would be appreciated ... thanks 

ubuntu 10.10 (for about 2 weeks now) it has updated a couple times tho ...on thinkpad r51 2888hu1

---

### Post by Locke_99GS on 2010-11-27
You can use the Ubuntu installer (or gparted) to remove the XP partition and leave the recovery partition in place.

Alternatively, if that recovery partition actually contains (or can create) a recovery CD, you could use it to create the recovery CD, then remove all of it.

Be sure to back up any data you may need off your CP install before wiping it out. People tend to forget about photo's - don't be like me and lose a couple years of your daughters childhood because you overlooks the photo's! :)

---

### Post by tpr51 on 2010-11-27
Oh Duh! 


now i feel stupid ... I had to buy the disks from ibm to reinstall the partition when i ffirst got this laptop ... guess i been lucky and never needed to restore anything after that and forgot all about making newer back ups 

 thanks for the tip to remember pics and such and sympathy for your loss... however only having 40gig to play with i had to remove all that stuff long ago to make room for cleaners and anti virus and firewalls and ..and... just so the thing had room to defrag!!  (which is why I've been looking at linux in the first place)

anyway... so i make a new recovery set (just incase i ever wanna go back to the dark ages) ... the next question is should i redownload the latest ubuntu and start over fresh ? i mean how is ubuntu to know it just got alot more living space?  deleting the 2 partitions(XP and the recovery) just makes blank space yes?this new space is going to need some kind of formatting ... or am i showing my "duh" factor again here lol

oh and by the way ...Elkhart,In ... wow i lived in Muncie most of my life ... too cold for me anymore

---

### Post by Locke_99GS on 2010-11-27
Elkhart is too cold for me, too. :) I spent a few years at Ft. Sill in the past - the winters there can be brutal, as well.

Once you remove the XP/recovery partition, it will be unallocated free space. You can use a tool such as *gparted* (available in the repo's) to enlarge your Linux partition(s), using some or all of this space. Linux will be very happy with the added space, and you won't have to do anything to let it know about it. No need to reinstall Ubuntu, unless you want to that is.

When using partition editors, be very careful about the choices you make - make sure you're aware of the way Linux designates partitions, and how they are mapped on your drive.

---

