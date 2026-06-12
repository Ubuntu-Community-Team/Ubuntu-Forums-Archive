---
title: "Evolution crashes at startup"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by Dayi on 2011-06-20
Can I please have help to resolve my Evolution crashes? It is in the send/receive mode for about 5-8 seconds and before completion, it crashes. It appears to have a new, 2nd "fetching" action that it is performing. I shut down and started my computer, but after many tries it continues to crash upon launching. It started today after I did 2 things: 

a) In the inbox, I created a new recipient rule that all mail that is from one of my own email addresses is moved to a subfolder in my inbox. (I deleted the folder that I created the rule for...I'm not sure how to delete the actual rule, if I have time to do it before it crashes.)

b) I registered for this site....which is probably not the issue. 

Thanks in advance!

---

### Post by Rex Bouwense on 2011-06-20
What version of Ubuntu are you using?

---

### Post by Dayi on 2011-06-20
Ubuntu 11.04

---

### Post by Rex Bouwense on 2011-06-20
Did it ever work correctly?  If it did it may be broken and you can fix it through the Synaptic Package Manager which is under Administration.  Bare with me I am not using 11.04 now and I don't remember exactly where it can be found.  Using Synaptic custom filters->broken, you can repair Evolution if it is indeed broken.

---

### Post by Dayi on 2011-06-20
Thanks for your response. It was working great. I've only been using it for a few days. I uninstalled it, but now I don't know how to install a new Evolution program. I'm so new to Linux, so I'm not sure how to install any programs yet. I just went to: [http://linux.softpedia.com/progDownload/Evolution-Download-18873.html](http://linux.softpedia.com/progDownload/Evolution-Download-18873.html) 
and tried downloading the new Evolution, but it just gives me a file that I extracted and that is where I am stuck...not sure how to run the installation...it doesn't seem to contain an ".exe" file.

---

### Post by haqking on 2011-06-20
> **Dayi said:**
> Thanks for your response. It was working great. I've only been using it for a few days. I uninstalled it, but now I don't know how to install a new Evolution program. I'm so new to Linux, so I'm not sure how to install any programs yet. I just went to: [http://linux.softpedia.com/progDownload/Evolution-Download-18873.html](http://linux.softpedia.com/progDownload/Evolution-Download-18873.html) 
and tried downloading the new Evolution, but it just gives me a file that I extracted and that is where I am stuck...not sure how to run the installation...it doesn't seem to contain an ".exe" file.

I suspect you downloaded the binaries (there are no .exe in Linux that is a window thing)

A binary is so you can compile it for your system.

However you can use your synaptic package manager in your SYSTEM>Administration menu and type evolution into the search box and then choose install.

There are other ways but you said you are new to Linux so ive kept it simple.

hope this helps

---

### Post by Dayi on 2011-06-22
Thanks! I reinstalled it like you suggested and realized that there was an infinite relooping error in Evolution, because I created a new email address witnin it and I made a mistake with entering it in....so, I unplugged it from the internet and deleted all the errors...It works again, whew!!!

---

