---
title: "My CD RW doesn't recognize a blank dvd/cd"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by JacquesPotter on 2011-08-02
So, I'm working on to other issues see threads 

[http://ubuntuforums.org/showthread.php?t=1812042](http://ubuntuforums.org/showthread.php?t=1812042)
and
[http://ubuntuforums.org/showthread.php?t=1812038](http://ubuntuforums.org/showthread.php?t=1812038)

To solve them I need to burn a copy of the MS OS, but my CD Drive "tsstcopr cdrw/dvd tsh492B" wont read a blank dvd/cd. I've got a Memorex DVD-RW; rewritable 4X; 4.7GB; 120min, blank dvd. I noticed there is a new driver available for download. See
[http://www.driverboost.com/lp/drivers/update/Tsstcorp-Drivers.php?gclid=CJXJwYH2saoCFWsbQgodplEh-Q](http://www.driverboost.com/lp/drivers/update/Tsstcorp-Drivers.php?gclid=CJXJwYH2saoCFWsbQgodplEh-Q)

Does anyone have any suggestions on how to fix this?

FYI. As you can tell from my other threads, I'm a newbie so please keep it dumbed down for me. Thanks.

---

### Post by jtarin on 2011-08-02
What are the indicators that make you think it is not recognizable?

---

### Post by JacquesPotter on 2011-08-03
> **jtarin said:**
> What are the indicators that make you think it is not recognizable?

Under the section where it states that "Select a disc to write" it states "Please replace the disc with a supported CD/DVD." It states this whether I have the dvd loaded or no cd/dvd loaded.

Oh yea, I'm using Brasero. 

Is this what you needed to know?

---

### Post by jtarin on 2011-08-03
These writers are sometimes very picky about the medium you attempting to write to. Do you have another brand possibly you could try before we get too far into this?

---

### Post by yetiman64 on 2011-08-03
From a firmware info file for that drive,
> CAN WRITE DVD-R : NO
CAN WRITE DVD-RW : NO
CAN WRITE DVD-RAM : NO
CAN WRITE DVD+R : NO
CAN WRITE DVD+RW : NOTaken from [[COLOR=Blue]--this thread--[/COLOR]]("http://forum.rpc1.org/viewtopic.php?f=14&t=38981") on a drive firmware board. It is not designed to write any dvd types only read some > CAN READ DVD-ROM   : YES 
CAN READ DVD-R     : YES 
CAN READ DVD-RW    : YES 
CAN READ DVD-RAM   : NO 
CAN READ DVD+R     : YES 
CAN READ DVD+RW    : YES 

---

### Post by jtarin on 2011-08-03
> **yetiman64 said:**
> From a firmware info file for that drive,
Taken from [[COLOR=Blue]--this thread--[/COLOR]]("http://forum.rpc1.org/viewtopic.php?f=14&t=38981") on a drive firmware board. It is not designed to write any dvd types only read some
Good catch!! +1

---

### Post by JacquesPotter on 2011-08-03
No, the only kind I have right now is the Memorex. Is there a way to find out if it is a supported medium?

---

### Post by yetiman64 on 2011-08-03
> **jtarin said:**
> Good catch!! +1
:), time for the OP to buy a DVD burner, cheers.

Edit: OP, your hardware is not capable of burning any dvd types, hence the unsupported medium message. You need to replace the drive itself to burn DVDs, it is only capable of burning cd types by design. Regards yetiman64

---

### Post by jtarin on 2011-08-03
Even the title of the thread should have tipped me off.:lolflag:

---

### Post by JacquesPotter on 2011-08-03
> **yetiman64 said:**
> From a firmware info file for that drive,
Taken from [[COLOR=Blue]--this thread--[/COLOR]]("http://forum.rpc1.org/viewtopic.php?f=14&t=38981") on a drive firmware board. It is not designed to write any dvd types only read some

OK. Is it my understanding then that I need a write-able cd not dvd?

Just saw the last message... thanks for your help!!! I'll go and buy some RW CD's.

Thanks again for all your help.

---

