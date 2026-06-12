---
title: "Slow bootup time"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Elsoreth on 2010-08-25
I have two computers running Ubuntu (Lucid Lynx), and both have some sort of oddity in the bootup process.  

The issue that bothers me most is the inability of my laptop to load in a timely manner--It consistently takes several minutes to get to the login screen.  I've been looking through the forums for some hint on how to solve my issue, but in all honesty I'm not sure where to start.  

I'd be very appreciative if someone could help me.  My laptop is an IBM T42 thinkpad.  Attached is my bootchart image, and if there's anything else that I should post I'd be happy to oblige.

---

### Post by LiquidMeson on 2010-08-25
Picture is tooo small can't see anything. Try uploading it to [http://imgur.com](http://imgur.com)

---

### Post by CharlesA on 2010-08-25
You need to upload the bootchart to an external image site, as the forum attachments can't handle something that big.

You could try running without "quiet" and see if it hangs anywhere.

---

### Post by Elsoreth on 2010-08-25
> **CharlesA said:**
> You need to upload the bootchart to an external image site, as the forum attachments can't handle something that big.

You could try running without "quiet" and see if it hangs anywhere.

Heh, I didn't notice the size change.

Here it should be in its full glory.

[http://imgur.com/p8e24.png](http://imgur.com/p8e24.png)

---

### Post by CharlesA on 2010-08-25
It looks like it's using mount.ntfs for over 3 minutes.

Do you have an NTFS partition set to be mounted automatically?

---

### Post by Elsoreth on 2010-08-25
> **CharlesA said:**
> It looks like it's using mount.ntfs for over 3 minutes.

Do you have an NTFS partition set to be mounted automatically?

If I do it I didn't set it up on purpose.  How would I check, and could it have anything to do with me running lucid through wubi?

---

### Post by CharlesA on 2010-08-25
Probably has to do with that, yes.

Wubi installs Ubuntu inside of Windows and, I believe it mounts the Windows partition.

---

### Post by Elsoreth on 2010-08-25
> **CharlesA said:**
> Probably has to do with that, yes.

Wubi installs Ubuntu inside of Windows and, I believe it mounts the Windows partition.

Hmm.  I guess I knew it ran off the windows partition, as I can access the windows files, but I've installed through wubi on other computers without having such a slow boot time.  I don't suppose there are any tricks to speeding up the mounting process?

EDIT: Actually, thinking about my issue a bit more I actually had difficulty installing it with wubi on this computer.  The newest version of wubi refused to load in XP, and so I eventually used an 8.04 install and upgraded from that...

---

### Post by CharlesA on 2010-08-25
It would probably be easier to just run Ubuntu in virtualbox instead of Wubi.

---

### Post by Col.Krumpet on 2010-08-25
> **CharlesA said:**
> It would probably be easier to just run Ubuntu in virtualbox instead of Wubi.

Oh yeah, if this is the case it would take AGES to boot up.
I had some of the same problem back when I first started getting into Linux (Fedora at this time) and my laptop was taking forever to load and was a bit unstable as well.
I finally ended up partitioning the HDD and loading Linux side by side with Windows XP and never had a problem after that.

---

### Post by DavidOfLondon on 2010-08-26
I left windows for the specific reason that I don't see why in the 21st century an OS should take 4 minutes to load and crash every other day. 

I zeroed my hard drive and installed Ubuntu 10.04 as the only OS and haven't looked back.

I have the default partitions recommended at install and it took less than 30 mins to install the whole thing from CD. 

I seriously recommend zeroing your hard drive and starting again - there is absolutely no reason why a default install of Ubuntu should take the length of time yours does. Keep everything off your desktop if you want super-fast boot up.

My laptop is a 160gb, 4 year old HP with no frills. I've filled the thing with apps and all sorts and yet it STILL loads in ...get this....

28 seconds.

From the moment I push the button to the moment I can go online is 28 seconds.

Save your stuff and zero the machine. It's the only guaranteed answer that won't have you ripping your hair out trying to partition, mount, back up, upgrade (a fraught process) etc.

David.

---

### Post by Col.Krumpet on 2010-08-26
> **DavidOfLondon said:**
> I left windows for the specific reason that I don't see why in the 21st century an OS should take 4 minutes to load and crash every other day. 

I zeroed my hard drive and installed Ubuntu 10.04 as the only OS and haven't looked back.

I have the default partitions recommended at install and it took less than 30 mins to install the whole thing from CD. 

I seriously recommend zeroing your hard drive and starting again - there is absolutely no reason why a default install of Ubuntu should take the length of time yours does. Keep everything off your desktop if you want super-fast boot up.

My laptop is a 160gb, 4 year old HP with no frills. I've filled the thing with apps and all sorts and yet it STILL loads in ...get this....

28 seconds.

From the moment I push the button to the moment I can go online is 28 seconds.

Save your stuff and zero the machine. It's the only guaranteed answer that won't have you ripping your hair out trying to partition, mount, back up, upgrade (a fraught process) etc.

David.

While I agree that this would end all the problems it may be a matter of not being able to zero out the HDD and install straight Ubuntu for whatever reason Elsoreth may have to keep Windows.
However if you can I say take the plunge and ditch Windows.

---

### Post by CharlesA on 2010-08-26
You can always install it side-by-side with Windows.

---

### Post by migs73 on 2010-08-26
You say you upgraded from 8.10, I upgraded from 9.10 and my boot time was in the minutes as well. After a clean install of 10.04 boot time now 28s. Don't think Wubi helps either, it is always going to be slower at everything.+1 on the side by side install with a clean 10.04 probably best. I only have windows on a VM inside Ubuntu now, as I only need 3 programs that run exclusively on MS.

---

