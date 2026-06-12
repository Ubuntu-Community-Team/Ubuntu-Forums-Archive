---
title: "Rsync on remote server stops"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by netpage on 2009-01-28
Hi,

Sorry if this is a little off topic.  I have a Bubba server running Linux connected to a DLink DNS-323 NAS box.  I can remotely manage the Bubba server [via ssh] so I have mounted the NAS in/on it and tried to rsync from the Bubba to the NAS.  I am working from a Asus eee 1000H running Ubuntu 8.10.

My test went OK so I then set rsync to copy all my photos and then closed the terminal window thinking that it would continue copying the photos but it stopped.

Am I missing something?  I assumed that as the rsync command was run from the Bubba server it would continue until it had finished, not until the terminal window was closed.

Any assistance would be appreciated.

Thanks

---

### Post by hyper_ch on 2009-01-28
when you close the terminal then the session gets closed, the connection aborted and rsync stops. Either run it in the background, have cron run it or don't close the terminal or have it run in a screen session which you can detach.

---

### Post by netpage on 2009-01-28
Hi hyper_ch,

Thanks for the info.  It all makes sense.

I do not want to keep anything open on my eee as I need to take it to work so I will look at running it in the background.  Are you able to assist in what I need to type to make rsync run in the background?:)

Thanks

---

### Post by hyper_ch on 2009-01-28
use cron or use "screen"

---

### Post by netpage on 2009-01-28
Hi hyper_ch,

Thanks.  Which of these would be easier to set up for a novice like me?  I have looked at the cron option and it seems quite hard.

Thanks

---

### Post by hyper_ch on 2009-01-29
neither is harder than the other... just different understanding for each is required. I guess screen would be more helpful for a couple of things.

Have a look at that:  [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by netpage on 2009-01-29
Thanks hyper_ch,

I have managed to get **screen **working.  **Rsync **worked OK and carried on after closing the terminal window.

Now I seem to have hit another problem as **Rsync **unexpectedly stops.  Would this because of the large amount of data I am trying to copy?  I have about 20Gb of photos to transfer over ethernet very litte other network traffic.

Would **unison ** be a better option?

Any help would be appreciated.

Thanks

---

### Post by hyper_ch on 2009-01-30
well, log the output of rsync and check why it stopped... the only thing I can do here is just guess...

---

