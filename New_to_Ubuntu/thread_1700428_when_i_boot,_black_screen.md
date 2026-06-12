---
title: "when i boot, black screen"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by meowski on 2011-03-05
hello! im new to linux, and sort of to windows. ive been using mac. earlier, i had downloaded ubantu then used daemon tools to emulate it and it worked perfect and i was able to run everything. then, everything froze so i restarted it. when i rebooted it, it would start correctly, then turn all black with a flashing cursor. so i tried to uninstall it and reinstall it, and i get to the end of the installation then it does the same thing again. someone, please help!

---

### Post by meowski on 2011-03-05
by the way, it is a toshiba running windows xp. and i can boot into windows perfectly.

---

### Post by Hedgehog1 on 2011-03-05
> **meowski said:**
> hello! im new to linux, and sort of to windows. ive been using mac. earlier, i had downloaded ubantu then used daemon tools to emulate it and it worked perfect and i was able to run everything. then, everything froze so i restarted it. when i rebooted it, it would start correctly, then turn all black with a flashing cursor. so i tried to uninstall it and reinstall it, and i get to the end of the installation then it does the same thing again. someone, please help!

meowski,

Your install is OK - you are getting caught when the video driver is loading.

Please read and follow the 'blank screen problems' thread below. 

You will be changing the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

You might need to to enter other boot parameters There are 6 of them. You may have to do them one-by-one until you get video.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)  (Common Kernel Options Section)

***The Hedge***

:KS

---

