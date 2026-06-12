---
title: "wireless_script not running from desktop (ubuntu 13.10)"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by Christine_Jones on 2014-06-26
I copied the script into a text file using a windows pc via a flash drive... to my ubuntu desktop.  Told it to run per instructions ( method #2) ...  but i get no results!  What am i doing wrong?  

I'm new to ubuntu - and not very adept.  My wifi stopped working so i'm trying to run so i can post...   i have a brix gigabyte w/ rtl8723ae PCIe adapter.  I've been reading threads but cannot resolve for my pc!  Please help!

---

### Post by veddox on 2014-06-26
To clarify matters: what "wireless_script" are you talking about? Could you post it here please(use the code tags)? And which instructions do you mean?

---

### Post by Christine_Jones on 2014-06-26
I am using thread from previous postshttp://ubuntuforums.org/showthread.php?p=12350385#post12350385

I downloaded it using a windows 7 pc - copied to a usb drive - then copied to my ubuntu desktop - made sure i could execute by changing permissions tab in properties of txt file -  then chose 'run' when prompted...  with no result

Not sure yet how to add code tags...   still looking for instructions on that!  

Thanks so much for any and all help you can provide.

---

### Post by Christine_Jones on 2014-06-26
Wait...   i figured the code tag thing...   but i'm accessing the forum on my nook right now so i can't code the actual file...

And the script comes from...
> [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

Is this how i should post?

---

### Post by Christine_Jones on 2014-06-26
I discovered part of my answer... when I copied the txt file to my Ubuntu desktop - there was an option in the bottom to "finish with... ???".  I originally told it Microsoft Windows (which was selected by default) -- this last time I chose to copy and save to my desktop - I changed that option to Linux/Ubuntu.

This allowed me to execute the file - and now I can post the resulting text file to help resolve my wifi issues.

final question - do I continue on with this post or start a new thread???

thanks again for your help!

---

### Post by Christine_Jones on 2014-06-26
Just in case I can continue here --- I pasted the file into pastebin

[http://pastebin.ubuntu.com/7707795/](http://pastebin.ubuntu.com/7707795/)

thanks again!  I'm loving the forum - and really learning a lot!

---

### Post by veddox on 2014-06-27
OK, I'm afraid I don't know enough to learn much from the output of that script (maybe some other user can help?), so let's take it right from the start:

[LIST=1]
[*]Did you previously have wireless working on that computer with that exact same setup? *(If so, continue with question 2. If not, go to 4)*
[*]What did you change since it stopped working?
[*]Was there any error message?
[*]Does the computer recognize a wireless signal?
[*]Does any other computer in your house recognize wireless?
[*]If you answered "yes" on question 4, what happens when you try to connect to that wireless?
[/LIST]

(Your first post was very ambiguous, so I am trying to get a bit more information with which we can hopefully pinpoint the problem.)

---

### Post by Christine_Jones on 2014-06-27
1. Yes
2. N/a
3. No
4. It tells me that it only has 2 in its list and both are out of range...  but i know there are at least 5 in range physically that are not 'seen' when i goto " connect option in wifi menu
5. All other computers, tablets, and roku are running wireless just fine
6.  n/a

I rebooted wifi router a couple of times
Rebooted computer several times
All to no avail

I'm thinking this has to be a driver issue...
Any thoughts on where to get the most current driver?

---

### Post by mörgæs on 2014-06-28
13.10 has less than a month of support left. Before proceeding I suggest a fresh install of 14.04 using wired internet connection.

---

### Post by veddox on 2014-06-28
> **mörgæs said:**
> 13.10 has less than a month of support left. Before proceeding I suggest a fresh install of 14.04 using wired internet connection.

+1

That's a good idea. Should hopefully fix the driver problem too.

---

### Post by Christine_Jones on 2014-06-28
Thank you for your help!  I really appreciate it.
I moved my computer, monitor & keyboard into the same room as the router.  It works wonderfully.  I plugged in an ethernet cable - that works too.  
I am going to call this problem solved - mostly because I was having trouble with the script - but have solved that part of the problem.
I will continue to try to figure out why my wifi doesn't work in my office down the hall.  Should I have further trouble, I will open a new thread.
My conclusion to the rtl8723ae wifi signal loss issue is that there is probably interference from other electrical sources throughout the house; be it wiring or all the wifi and bluetooth stuff we have.  

Thanks again!

---

### Post by steeldriver on 2014-06-29
If you are experiencing signal quality / interference issues, probably the first thing to try is choosing a different wireless channel on your router

---

### Post by mörgæs on 2014-06-29
> **Christine_Jones said:**
> Should I have further trouble, I will open a new thread.

It it's essentially the same problem then please keep everything in the same thread.

---

