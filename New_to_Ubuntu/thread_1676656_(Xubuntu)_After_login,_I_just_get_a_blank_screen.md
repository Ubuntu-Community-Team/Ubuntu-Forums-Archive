---
title: "(Xubuntu) After login, I just get a blank screen"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by stalemath on 2011-01-27
I recently set up Xubuntu 10.04 on an older machine that I wasn't using, with the intentions of setting up a server. The install completed with no problems, and after I installed it I was able to log in and work through the interface freely. However, after I shut down the machine and booted it back up later, I encounter problems. It goes to the log in screen, as I assume it should, and I log in with the correct info... and it takes me to a blank screen (with the blue default background image), appearing as if it's about to load the interface, but it just remains still. I've shut off the machine and tried again numerous times, but I keep getting the same result. Any help would be appreciated, as this is my first time experiencing with any form of Linux. Thanks.

---

### Post by mharrison on 2011-01-27
While it is on the blank screen, try this.

Hit ALT+F2 and then type in xfce4-panel and hit Enter and see if anything happens.

---

### Post by stalemath on 2011-01-27
That fixed it! Why did I have to do that though? I know I'm going to set this up as a server, but would I have to do that each time I log in?

---

### Post by mharrison on 2011-01-27
I am not sure why as I don't use xfce, but I would try rebooting and see if it makes you do it again, and if it does I would then go to System -> Preferences -> (not sure if xfce has this but...) Startup Applications and create a new entry and paste that command in there.

Perhaps someone a bit more knowledgeable can help with a reason/better fix.

---

### Post by stalemath on 2011-01-27
I restarted it and I was able to log in fine. Thanks for your help.

---

