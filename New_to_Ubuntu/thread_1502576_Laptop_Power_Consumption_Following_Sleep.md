---
title: "Laptop Power Consumption Following Sleep"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by anon2122 on 2010-06-05
Apologies for cross-posting, but I am not sure if I originally asked in the best place, as I had very few views and the post has dropped away.

[http://ubuntuforums.org/showthread.php?t=1502350](http://ubuntuforums.org/showthread.php?t=1502350)

as originally posted.

Below, I quote to save clicking the link.

/////

Dear all,

                                 I installed Ubuntu 10.04 x64 on my new  laptop (Acer TravelMate Timeline 8371). It's a high-spec CULV laptop,  and gets around 7-8 hours battery life under light usage in Windows 7.
 

 I am getting even better battery life in Ubuntu (suggestions of 9  hours+, in fact Ubuntu has suggested 9hrs30mins on occasions. I believe  this estimate is correct, since Ubuntu seems to be a much leaner OS than  Windows 7.
 

 To explain my system config (as it's not too common) – this laptop has  two graphics chips. An Intel 4500MHD integrated chip for low power  consumption, and an ATI Mobility Radeon 4330 for casual gaming/3D  graphics work etc. Out the box, Ubuntu was only going to get 2 hours  battery life, since it was not disabling the unneeded card.
 

 I compiled a 2.6.34 kernel with the new vgaswitcheroo enabled, and used  instructions online to create an 'interface' to it, which allows the  card to be switched, and power to the cards controlled.
 

 My own modification was to add to init.d a few power saving commands  suggested by powertop, in addition to my own commands to enable Intel  graphics by default, and power down the ATI chip.
 

 This works fine most of the time, and I can get my 9+ hours of  estimated battery life out the laptop under light/minimal usage.
 

 The issue comes with sleep. I managed to get sleep to work using the   i8042.reset=1 addition to grub (See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120)  for the bug report).


But when I resume for sleep, my battery life estimate and power  consumption both dramatically worsen. For example, before sleep,  powertop reported my power consumption as 6.8W (10 hours 30 mins  remaining), yet after sleep I was only expected to get 4.4 hours with it  running at 14.8W :(


I think after resuming from sleep, the fan turned itself on and wouldn't  disable, although I can't be sure that's the only issue. My kernel  appears to be fine, and the second graphics card seems to be staying off  fine (only 2.5 hours battery if it comes on, so it's not that)


So... anyone got any ideas about the power consumption after sleep? I am  not sure what logs would help, but if there are any, give me a shout  and I'll get them.


Also, where is the best place to run commands I want executed as the  root user at boot? I would like to add all the powertop recommendations  to something to execute them at boot (mainly the ondemand governor, as  that really helps the power consumption by allowing the CPU to  underclock to 800 MHz instead of 1.4GHz).


Finally, while I'm here, are there any other tweaks or patches I should  apply to optimise power consumption, as I'm new to running ubuntu on  real hardware, although have used it a bit in Virtualised Applications?


Regards

///

---

