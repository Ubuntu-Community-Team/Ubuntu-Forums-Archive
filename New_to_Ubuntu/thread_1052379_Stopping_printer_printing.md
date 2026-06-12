---
title: "Stopping printer printing"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Bruv on 2009-01-27
I have spent some time managing to get my printer to print.
During the process I have pressed to print many times,
Now the printer is working I have a backlog of "jobs" that are printing that I cannot find how to stop.......This could be serious....there could be an ink shortage if my printer keeps this up.

HELP ME PLEASE....

---

### Post by Peter09 on 2009-01-27
Top right you should have a printer icon. Click on that to see all the print jobs in the que. Then you can delete them.

---

### Post by Bruv on 2009-01-27
Top right of what ?
I have accessed the printer through Printing I also have HPLIP toolbox. I can only see one job.
The pages that are being printed are capitalised letters and numbers, with no apparent sense at all.
And nothing I have ever wanted to print.....the count of pages so far exceed 20....and the printer demands more paper

---

### Post by Peter09 on 2009-01-27
Looks like the document is corrupt or in the wrong format. You need to kill that print job (the single document you can see)

---

### Post by Bruv on 2009-01-27
I have stopped the job I can see, but it is in a queue.....and I don't know how long the queue is in front of it.

Even the printer refuses to switch off....because its still hungry.

---

### Post by cariboo on 2009-01-27
Open Firefox and in the address bar type:

```
http://localhost:631
```

to get to the cups mangement console, click on jobs and it should list all the queued printer jobs, you can cancel them from there.

Jim

---

### Post by Bruv on 2009-01-28
Did that, and it only shows the job I had in hand and cancelled earlier, twice, plus a test page.
The printer has been turned off over night and it seems to have righted itself, thankfully.
I had done the same before with no result.

Anyway it is OK now....I shall remember that next time, many thanks.

---

### Post by Peter09 on 2009-01-28
The printer has an internal buffer, so if you get the same problem you will need to cancel the offending job to stop it transferring more rubbish and also turn the printer off to clear the internal buffer.

---

