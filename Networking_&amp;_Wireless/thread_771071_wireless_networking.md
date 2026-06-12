---
title: "wireless networking"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by chrisfaulkner on 2008-04-27
Hi

I just installed Hardy Heron. Administration -> Drivers is only warning me about my ATI graphics device. dmesg seems to indicate my wireless chip (broadcom) is loaded. 

So first of all, where is the device manager for me to check this ?

SO I need to get my laptop on the network so I try Administration -> Network and all three connections are greyed out. I unlock and set up my wireless device, entering the key, DHCP, etc, then wait and nothing happens. No messages to tell me that it connected (or not), or perhaps that the key was wrong. Silence. And I am not networked. So what do I do ? Is there a wireless network scanner with ubuntu ? Or a wizard to help me connect ?  Where are the logs ?


Thanks

Chris

---

### Post by TrueDego on 2008-04-27
OK there are a few things you can do.  First get a CD of 8.04 and enable the CD as a software source in System > Administration > software sources.  Then open synaptic and install fwcutter.  Then you should see b43 in the Hardware Drivers in admin.  After you can see the checkbox, there is a blog that has a walkthough with the info to finish it.  I used it and it went perfectly.  The blog is [Here]("http://300lb.blogspot.com/2008/04/how-to-get-broadcom-wireless-to-work-in.html").  Hope this helps!

---

### Post by chrisfaulkner on 2008-04-27
Thanks for your help. 

I tried but the install failed. It tried to reach some internet site and it failed because I have no network connection. Ah well. I keep hoping someone somewhere will manage to get Linux ready for the mass market. Maybe one day...

Thanks

---

### Post by TrueDego on 2008-04-27
How are you getting online now?  It sounds like your doing everything right.  Ok, its attempting to get online.  Its going to fail.  Go to that blog and get the file on the computer your using, just dont use IE7 to DL the file.  Get the file put on your Ubuntu system and youll be up and running in 3 mins.  Keep going, dont give up now!

---

