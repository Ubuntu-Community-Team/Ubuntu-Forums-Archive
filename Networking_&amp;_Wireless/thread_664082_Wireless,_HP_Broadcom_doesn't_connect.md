---
title: "Wireless, HP Broadcom doesn't connect"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by ctoaun on 2008-01-10
Good evening all
Two questions sans answers? :)
I can&#8217;t connect to wireless internet, and because of my location, wireless is my only way of connecting to the internet for the time being. However, my other computer, which is not running Linux , connects to the internet just fine. No, I'm not bashing, just providing relevant info. 

Question 1:
 How can I utilize this other computer to fix the computer running Ubuntu? 

The computer on which Ubuntu is installed is a HP zv5000. It  has the same IEEE 802.11b/g "Broadcom 4306&#8221; card & driver as the following post: [[URL="http://ubuntuforums.org/showthread.php?t=663581&highlight=wireless"][URL="http://ubuntuforums.org/showthread.php?t=663581&highlight=wireless&page=2"]http://ubuntuforums.org/showthread.php?t=663581&highlight=wireless&page=2]([URL="http://ubuntuforums.org/showthread.php?t=663581&highlight=wireless"][URL="http://ubuntuforums.org/showthread.php?t=663581&highlight=wireless&page=2"]http://ubuntuforums.org/showthread.php?t=663581&highlight=wireless&page=2)
if I had internet access, I believe the referenced post would have worked for me as well  as the computers are identical  and the &#8220;iwconfig&#8221; info is the same. 

**Just to be clear, neither &#8220;sudo-apt&#8221; nor &#8220;synaptic package manager&#8221; are options for me right now. **

Question 2:
 Is there a way to put the applications on a flashdrive?

Please do not leave out info and assume that I will be able to fill in the blanks as Ubuntu is still new to me.

Thanks

PS: I also tried to use Wine. The "setup .exe" activated, so it *appears* to have installed. However, there is no evidence that it works. However, since the "Wine" usage info that I find is either not user friendly or not relevant, I've no way of knowing.

---

### Post by Schnautz07 on 2008-01-29
I had lots of problems configuring my hp's broadcom wireless also.  Luckily (after days searching) I ran across a VERY helpful post.  You will need some sort of wired internet connection to get it going, though, because you must first download drivers and then install ndiswrapper (an app that can use windows drivers)

This post tells exact instructions on how to install and use broadcom drivers on ubuntu.  I've used it about 5 times and it always works for me.

The only issues I have are when I try to connect to a hidden (not broadcasted) network.

Here is the link...  I hope it helps.

[http://ubuntuforums.org/showthread.php?t=572005]("http://ubuntuforums.org/showthread.php?t=572005")

Ken

---

