---
title: "authentication information: make it go away!"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by frankeleone on 2007-11-24
Hi,
   I have Kubuntu Feisty. I used to be able to click remote places to samba shares to mshome and then my windows computer (XP) icon would show up and I could read and write to it. A lot of things have been done since those good old days, including reformatting both computers. Now, after I get to mshome (the workgroup), I get no icon of the windows computer, and instead get a dialog box asking me for authentication information including a username and password. This used to work "out of the box", I can't get it going now. Any help would be greatly appreciated, however, gui help would be more appreciated. In my frustrated logic, if it worked before w/o command line work, why would it need it now if the OS on both the computers is the same? I am not really a newbie at this point, so this problem is all the more frustrating. The computers are connected w/ a wired router that has not changed since it used to work. Thanks in advance, Frank

---

### Post by jetsam on 2007-11-25
Hi.  I don't know the real fix for this problem, but I just stumbled across a workaround.  I don't usually use Kubuntu, but I booted into Kubuntu desktop to try smb4k.  It's a KDE based SMB network browser, and I noticed that if I used it to browse Windows shares, it didn't have the authentication problem you're talking about (that I also have if I browse through Dolphin.)  

Smb4k is in the repositories, and seemed well done and pretty useful.  I wish something as polished existed for gnome.

---

### Post by frankeleone on 2007-11-25
Hi Jetsam,
        Thank you so much for the workaround. It  does solve the problem. After I loaded the program and messed w/ some settings, I am now able to read/write to my windows computer. I am very thankful for your time. For me, it would be better to figure out this authentication issue w/o the workaround, as I just want to understand how things work or why they are not working, but this may not be possible. Interestingly, now, with Smb4k running in the background, I can now get to my windows computer the old way, via clicking remote places, samba shares, mshome. However, this only works SOMETIMES. At other times (trying it again seconds later), it again asks me for the authentication info as it was before. In my mind, this is BIZZARO. Why would it be only working sometimes??? To repeat, I do have a reliable patch if I use Smb4k, but if anyone out there can understand what the issue is based on the info you have read by my posts so far, I would appreciate "the fix" over the workaround. Thank you again,Jetsam. Frank

---

