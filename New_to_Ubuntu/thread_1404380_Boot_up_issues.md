---
title: "Boot up issues"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Marc St Louis on 2010-02-11
I have ubuntu installed on a second HD that is a slave to the HD with windows.  Most of the time it takes a while to boot up, the second HD is not detected for some reason.  When that happens I can't even boot into windows.  Is this a problem that can be fixed?  I am a bit worried that if for some reason this becomes a permanent problem I will not be able to access windows anymore.

---

### Post by mhgsys on 2010-02-11
Seems like a master/slave problem to me. 


Check if master / slave jumpers are set correctly.

---

### Post by oldfred on 2010-02-11
It may be a hardware issue but to review the boot process you can post the results of this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by mwcrowley on 2010-02-11
Check your cables.  If one is loose the hard drive is not present when the computer boots up, and grub is not getting off the ground to boot windows.

---

### Post by Marc St Louis on 2010-02-11
The jumpers are set correctly
I thought it might be a loose cable but I have checked them repeatedly and they seem good.


I'll check the boot info script but I have no internet access on ubuntu so I have to go back and forth from one OS to the other for that

---

### Post by Marc St Louis on 2010-02-11
I ran the boot up script and this is the result, sorry but the only way I can post is as an image

---

### Post by oldfred on 2010-02-12
Cannot read the image. Copy and paste the entire results.txt in your reply and highlight with the mouse & click on the # [code] tag in the edit panel to make it easier to scroll thru.

---

### Post by Marc St Louis on 2010-02-12
> **oldfred said:**
> Cannot read the image. Copy and paste the entire results.txt in your reply and highlight with the mouse & click on the # [code] tag in the edit panel to make it easier to scroll thru.

Yes I sort of figured that might be a problem.  It's all academic now as it will no longer boot up.  

I do believe I found the problem, the last time it did boot up I had an error message that said the HD was failing, too many bad sectors, and that I should back up any information then replace the HD.  There was no information on that HD that was worth saving so I didn't bother but unfortunately there is plenty of information on the other HD that I would like access to.  What I really need to find out now is how I can get the windows HD to boot up.

---

### Post by mhgsys on 2010-02-12
(To run the Recovery Console, boot into your WinXP setup CD and press r when prompted.) 

Use a windows recovery/installation cd, drop to recovery console

and typ 
```
fixmbr
```


if that doesn't do trick use
```
fixboot
``` instead

FIXBOOT writes an entirely new boot sector, while FIXMBR repairs the MBR (master boot record) in the boot sector.

---

### Post by Marc St Louis on 2010-02-12
Thanks mhgsys but there's a couple problems with that.  First it's win2000 and second I don't have win2000 cd. 

That's ok though as it finally booted up, after several hours of mucking around.  I'm going to back the drive up and if it goes it goes.

---

### Post by mhgsys on 2010-02-12
Ah, I did know it was win 2000 ... The only thing I could make out properly of your screenshots/image was winXp on sda1

Anyway:you booted it by now, good luck with it ..


> **Marc St Louis said:**
> Thanks mhgsys but there's a couple problems with that.  First it's win2000 and second I don't have win2000 cd. 

That's ok though as it finally booted up, after several hours of mucking around.  I'm going to back the drive up and if it goes it goes.

edit: Please mark this thread as solved

---

### Post by Marc St Louis on 2010-02-15
I was able to temporarily fix this problem by installing auto super grub disk.  Worked like a charm

---

