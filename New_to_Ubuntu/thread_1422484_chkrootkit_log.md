---
title: "chkrootkit log"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-03-05
How would one write a simple script to run chkrootkit and then print the output to a log file in a designated location?  Haven't been able to find this information anywhere...

---

### Post by Ozymandias_117 on 2010-03-05
In your bash script just put ```
sudo chkrootkit > ~/Desktop/chkrootkitlog
``` You can rename the file to whatever, or include a .txt extension if you want. After you make your script, just sudo chmod +x it so it can be executed. You will still have to enter your password because chkrootkit needs admin rights.

edit: You can just change the pathway to wherever you want it, and the file doesn't have to already be there.

---

### Post by baddnady23 on 2010-03-05
Great reply.

> You will still have to enter your password because chkrootkit needs admin rights.


  Is there a way that I can sudo it so that cron can run it automatically without my input in it then?  Thanks for the help/

---

### Post by Ozymandias_117 on 2010-03-05
> **baddnady23 said:**
> Is there a way that I can sudo it so that cron can run it automatically without my input in it then?

Not that I know of, sorry.

---

