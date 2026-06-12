---
title: "Windows partition not shutting down properly"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by neuralfrenzy on 2011-04-25
Hello Ubuntu users! 

I installed Ubuntu 11.04 Beta 2 as a dual boot on my Windows 7 laptop and now my Windows partition won't shut down properly. Windows acts like it's shutting down, then the screen freezes, and goes black. The hard drive light is still going, though, and so are the fans.

I was just wondering if anybody has had this problem or not. Thank you in advance for any help. :-)

---

### Post by Mark Phelps on 2011-04-25
How did you install Ubuntu? Using Wubi (inside Windows)? Or as a separate partition?

And, if the second, how did you shrink Win7 to make room? Did you allow the Ubuntu installer to do that?  If so, you likely damaged the Win7 filesystem in the process, and you're lucky it still boots.

Also, Ubuntu 11.04 is still in testing.  You will get better and faster responses if you post your 11.04 questions to the Natty Development forum.  That is located at: Other Community Discussions --> Development & Programming --> Natty Narwhal Testing and Discussion.

---

### Post by neuralfrenzy on 2011-04-25
It's on a separate partition and not in Wubi. I shrunk the Windows partition in Windows but I didn't create a separate partition using Windows.

I don't have anything important on here so I will remove Ubuntu and reinstall it (I've done this before in trying to get this to work right). This time though I will use Windows to create the separate partition.

Thanks for the reply, I appreciate the help. :-)

---

### Post by wilee-nilee on 2011-04-25
> **neuralfrenzy said:**
> It's on a separate partition and not in Wubi. I shrunk the Windows partition in Windows but I didn't create a separate partition using Windows.

I don't have anything important on here so I will remove Ubuntu and reinstall it (I've done this before in trying to get this to work right). This time though I will use Windows to create the separate partition.

Thanks for the reply, I appreciate the help. :-)

You might try a chkdsk with windows as well at some point. The ubuntu install itself should not effect the windows shutdown, but strange things happen.

---

### Post by neuralfrenzy on 2011-04-26
I did a disk check and everything was fine. After that I tried to install Ubuntu the advanced way on a partition that I created inside of Windows but some of the stuff was over my head. I was afraid I was going to screw something up so I just ditched it. I was thinking just formating the whole drive and installing Ubuntu, I have a backup of the hard drive in case I want to go back.

---

### Post by mutahirqureshi on 2012-02-18
I'm having the same problem. I installed Ubuntu 11.10 alongside Win7 and whenever I reboot into Win7 after booting into Ubuntu, and then try to shut down Win7, after the shutting down screen, I get a black screen and the system freezes. I have to force shutdown using the power button. To be able to shutdown properly again from Win7, I have to first boot into safe mode and then shut down from safe mode and then normally boot Win7 again. However, if I boot Ubuntu again, I run into the problem again and I have to boot into safe mode again.

---

### Post by Ms. Daisy on 2012-02-18
Did you defragment Windows before you installed Ubuntu? I had this problem when I skipped defrag before dual booting.  

Have you run chkdisk in windows since you started having the problem?

---

