---
title: "no wireless after moving"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by distractible on 2011-04-10
Hello! I am using ubuntu 10.4 on my compaq presario laptop and after we moved recently my wireless network icon disappeared from the toolbar and the computer no longer detects wireless networks.  We had a bit of trouble getting our wireless router to work and a friend tinkered with it and got it to work. I think he said that he reinstalled the software. Now, Ours and our neighbors' networks are visible from our other computer. If anyone has any advice that would be great! : )

---

### Post by fabricator4 on 2011-04-10
> **distractible said:**
> Hello! I am using ubuntu 10.4 on my compaq presario laptop and after we moved recently my wireless network icon disappeared from the toolbar and the computer no longer detects wireless networks.  We had a bit of trouble getting our wireless router to work and a friend tinkered with it and got it to work. I think he said that he reinstalled the software. Now, Ours and our neighbors' networks are visible from our other computer. If anyone has any advice that would be great! : )

It's normal for wireless networks to be visible to anyone, unless you specify that it is to be a hidden network during setup of the router.  The router would have needed to be re-configured because of the move, possibly even if you stayed with the same ISP - you are now on a different line/exchange.

Make sure you have security enabled (on the router), preferably WPA over WEP.

Next, check the obvious things first: Is the wireless device in the computer enabled?  Most can be switched off to save power when they are no longer required.

Secondly, check startup applications and make sure that Network manager is ticked to run at startup.

If all that is OK, then open up network connections (System -> Preferences -> Network Connections) and check that the setup is good for your router.  If all of this works, you should now have the network icon on the panel, and a working network connection.

Gotchas to look out for: it's possible for the network card to be on, but have networking disabled in Network Manager.  Sometimes mine becomes disabled for no apparent reason...  You normally still have the network icon however.  The second gotcha is to set the wireless network connection to connect automatically when it's available (in Network Manager again).  If it's not enabled you have to connect manually each time you boot or resume.

Chris.

---

### Post by distractible on 2011-04-11
Hi Chris!
Thanks for your reply! My wireless device appears to be on (the light is lit) and Network Manager is ticked to run at startup. When I open up Network Connections, it shows a list of a bunch of different wireless networks that I have connected to int he past, all with "Auto" in front of them. (I believe I set it up to connect automatically before.) But not our current wireless network, it isn't there (I haven't connected to it before). I am not sure how to proceed now. I got the network icon back on the toolbar by using the add to panel feature, but it just has that little red X in the corner... I'm not very tech savvy! So this is all pretty mysterious for me. Thank you for your help!!

---

### Post by doppel.ganger on 2011-04-11
I once had the same problem with my grandfather's laptop, he wanted to speed it up. Plug your computer into a WIRED network and go to System -> Administration -> Additional Drivers and make sure that a driver that has to do with wireless is enabled. Hope this helps!

Shoot, ignore this. I was thinking of something else and don't know how to delete a post.

---

### Post by Rex Bouwense on 2011-04-11
After your friend finished "tinkering" with your router, did you ask him if he changed anything.  If he did, even if you have the auto connect activated, you may not be able to automatically connect.  For the time being, turn off the security protection and see if your computer can connect to the wireless without security.  
Can you connect to the router using an ethernet cable?

---

### Post by 5149.5 on 2011-04-11
You could also try the connect to hidden network option.

---

### Post by fabricator4 on 2011-04-11
> **distractible said:**
> Hi Chris!
Thanks for your reply! My wireless device appears to be on (the light is lit) and Network Manager is ticked to run at startup. When I open up Network Connections, it shows a list of a bunch of different wireless networks that I have connected to int he past, all with "Auto" in front of them. (I believe I set it up to connect automatically before.) But not our current wireless network, it isn't there (I haven't connected to it before). I am not sure how to proceed now. I got the network icon back on the toolbar by using the add to panel feature, but it just has that little red X in the corner... I'm not very tech savvy! So this is all pretty mysterious for me. Thank you for your help!!

When you right click on the network icon in the panel, is their a tick next to "enable networking".  If not, click on enable networking.  What happens?

Chris

---

### Post by gandaran on 2011-04-12
> **distractible said:**
> Hi Chris!
Thanks for your reply! My wireless device appears to be on (the light is lit) and Network Manager is ticked to run at startup. When I open up Network Connections, it shows a list of a bunch of different wireless networks that I have connected to int he past, all with "Auto" in front of them. (I believe I set it up to connect automatically before.) But not our current wireless network, it isn't there (I haven't connected to it before). I am not sure how to proceed now. I got the network icon back on the toolbar by using the add to panel feature, but it just has that little red X in the corner... I'm not very tech savvy! So this is all pretty mysterious for me. Thank you for your help!!
I have had this problem before and what I do is to remove every wireless connection in the network manager wireless tab then disable and enable the network again, wait a couple seconds and the new wireless connection is finally detected.

---

