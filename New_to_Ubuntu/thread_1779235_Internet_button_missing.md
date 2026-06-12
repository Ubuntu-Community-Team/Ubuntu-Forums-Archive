---
title: "Internet button missing"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by scorpious on 2011-06-10
You know the internet button that by default is up in the top right hand corner of the screen? Mine has disappeared

Anyone know how to get it back?

Cheers

---

### Post by el_koraco on 2011-06-10
System - Preferences - Startup Applications. Check and see if "Network manager" is listed as one of them.

---

### Post by mikewhatever on 2011-06-10
Try hitting alt-f2, and in the window that opens type **nm-applet --sm-disable**.
By the way, the icon is the Network Manager applet. Any idea why it disappeared?

---

### Post by drpjkurian on 2011-06-10
Right click on your top panel and select 'Add to panel'
Then select 'Network monitor activity'

---

### Post by scorpious on 2011-06-10
@ el_koraco: Yes is there and is ticked

@mikewhatever: That didn't do anything apparent (Didn't give me an error either)


@ drpjkurian: The option of "Network monitor activity" is not in the list


Edit: I have no idea why it disappeared. its been gone for a while just hasn't bothered me till now.

---

### Post by drpjkurian on 2011-06-10
Hi
Please add 'notification area' to your panel. It might solve your problem

---

### Post by scorpious on 2011-06-10
Yea I tried that as well

Selecting Notification Panel then clicking "add" has no effect whatsoever



Thanks for the quick replies by the way

---

### Post by scorpious on 2011-06-10
interesting development. I noticed that when click to add notification area three tiny lines show up on the panel looking a bit like

-
-
-

But alot smaller

when I click on these and select I get a the attached picture.

Other than that I can't do anything with it

---

### Post by el_koraco on 2011-06-10
Click and hold those small lines, and move them to your left. 
If not, I'm not gonna try to reinvent the wheel, check out some of the threads and you might find a solution. 

[http://ubuntuforums.org/showthread.php?t=1621690]("http://ubuntuforums.org/showthread.php?t=1621690")
[http://ubuntuforums.org/showthread.php?t=1524391]("http://ubuntuforums.org/showthread.php?t=1524391")

---

### Post by mikewhatever on 2011-06-10
> @mikewhatever: That didn't do anything apparent (Didn't give me an error either)

Edit: I have no idea why it disappeared. its been gone for a while just hasn't bothered me till now.

Could it be that the applet is running but not displayed? What's the output of **ps -e | grep nm-applet**?

---

### Post by scorpious on 2011-06-10
```
 1537 ?        00:00:00 nm-applet
```

---

### Post by scorpious on 2011-06-10
> **el_koraco said:**
> Click and hold those small lines, and move them to your left. 

That sucessfully removed the lines to the left. cheers ;)
> **el_koraco said:**
> check out some of the threads and you might find a solution. 

[http://ubuntuforums.org/showthread.php?t=1621690](http://ubuntuforums.org/showthread.php?t=1621690)
[http://ubuntuforums.org/showthread.php?t=1524391](http://ubuntuforums.org/showthread.php?t=1524391)

No help there either :(

---

### Post by el_koraco on 2011-06-10
> **scorpious said:**
> That sucessfully removed the lines to the left. cheers ;)


What I meant was, items in the notification area should show up if the lines are moved. 

Btw, did you try rebooting?

---

### Post by scorpious on 2011-06-10
Just rebooted now. No change :)

Ok new plan.
How do I access the network Manager with using the applet?

---

### Post by mkornig on 2011-06-10
> **scorpious said:**
> You know the internet button that by default is up in the top right hand corner of the screen? Mine has disappeared
Cheers

Internet button? You mean the button for a browser (e.g. for Firefox)?

---

### Post by drpjkurian on 2011-06-12
Hi
Open the terminal type &#8220;sudo edit /etc/NetworkManager/nm-system-settings.conf&#8221; change the &#8220;managed=false&#8221; to &#8220;managed=true&#8221; and then save it.

then in the terminal type &#8220;killall nm-system-settings&#8221;

and then reboot.

---

### Post by VOT Productions on 2011-06-12
**ALT+F2** then n**m-applet**.

---

### Post by scorpious on 2011-06-12
Thanks for all the replies.

I've decided to upgrade to the new version of ubuntu, so it should be a problem after that.

Thanks again:popcorn:

---

