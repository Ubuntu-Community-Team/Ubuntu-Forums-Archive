---
title: "[SOLVED] Connecting to DSL ISP after connecting to wireless router"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by ScarletSpider on 2008-07-03
Hi, after a long three day search and no progress I decided to post...so bear with me please:

I have installed Ubuntu HH and I am using a Netgear wg111v2. usb adapter to connect to my Comtrend ADSL router.After installing the driver for the wg111v2 I still had no luck, after reading a lot of posts with related problems I got the solution which was to install Wicd manager. Ta dah! Now I have my computer connected to the netgear usb adpater which has detected my router and connected.SUCCESS...this is where the problem begins, now I have a DSL provider which I need to connect to AFTER I connect to the router (can't change anything in this router-its unsecure (diff. problem))

I want to connect to the internet using the given username and password now, everything else is great: USB adapter works and gives me connection to the router. 

In a lot of diff. posts I have read, people with the same problem tend to get answers which don't relate to the problem because the people dont understand the situation completely that we need to connect to the wireless router FIRST and THEN connect to the internet using the DSL providers given username and password. In Windows, this is done using by setting up wireless (PUBLIC NETWORK) and then using "dial-up" to connect to the PRIVATE NETWORK (i.e, the dsl provider)

If anyone can help solve this problem, I appreciate the effort :D and sorry for the long explaination.:KS

---

### Post by ScarletSpider on 2008-07-04
Sorry, I couldnt find the edit button...Today I realized that what Im trying to do is connect to using PPPOE after connecting to the wireless router..if that helps clarify anything?

-Edit: I just found the edit button..lol

---

### Post by prshah on 2008-07-04
> **ScarletSpider said:**
> 
what Im trying to do is connect to using PPPOE after connecting to the wireless router..if that helps clarify anything?



Clear as mud... but try ```
sudo pppoeconf
```

And the "edit" button took me a while too when I started out...

---

### Post by ScarletSpider on 2008-07-04
OMG..ur a genius...I realized that I had already setup pppoeconf to my dsl provider and...just needed to run it...thannnnk youuuu for that..lol

One last question if you dont mind---> will I ALWAYS have to run "sudo pon dsl-provider" in order to start it...or is there any way I can make this an automatic startup task for the OS??

---

### Post by prshah on 2008-07-04
> **ScarletSpider said:**
> OMG..ur a genius...I realized that I had already setup pppoeconf to my dsl provider and...just needed to run it...thannnnk youuuu for that..lol


Captain Obvious: At your service. Now I'm off to warn an old lady that crossing the road can be dangerous.

[EDIT:] Just saw your edit. Guess we're both addicted to the edit button now.

You can include the line ```
pon dsl-provider
``` (Note, no "sudo") in your "/etc/rc.local" file; Don't disturb the last line in the file ("exit 0").

Or you can add it to startup with System-Preferences-Sessions-Add, then just fill in the blanks, only in this case, use gksudo instead of sudo. (Actually, this is not a good solution. The first one is better).

---

### Post by ScarletSpider on 2008-07-04
Thanks again for all the help, appreciate it :D

(EDIT:)LOL, this button IS very addicting cap. obv :P

---

### Post by prshah on 2008-07-04
> **ScarletSpider said:**
> Thanks again for all the help, appreciate it :D

(EDIT:)LOL, this button IS very addicting cap. obv :P

OK! Please mark the thread solved if your problem is cleared; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

