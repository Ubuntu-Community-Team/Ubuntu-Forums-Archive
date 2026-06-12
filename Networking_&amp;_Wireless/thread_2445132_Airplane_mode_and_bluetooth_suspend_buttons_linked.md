---
title: "Airplane mode and bluetooth suspend buttons linked in OS"
date: 2020-06-09
forum: Networking &amp; Wireless
---

### Post by lumberg2 on 2020-06-09
Sorry if this is the wrong sub for this, but I wasn't fully sure where to post. I have been trying to disable the "Bluetooth can be turned off to save power" option in System>Power, but whenever i disable it, airplane mode engages. This cannot be correct. I have searched this site and maybe my search terms are not creative enough. Anyone else dealt with this?

I am on a HP Elitebook 850 G3, if that is helpful. This issue is only an annoyance, but still...

Thanks in advance,
Guy

---

### Post by CelticWarrior on 2020-06-09
Welcome.

The description is arguably misleading. Some users, as you, may read it as a way to switch off some power saving feature. It isn't, it's actually to switch off that device, hence the airplane mode.

---

### Post by JoelParke on 2020-06-21
I have the SAME issue.  When in settings under 'Power' there are two toggles:
One for WiFi - says Wi-Fi can be disabled to save power.
One for Bluetooth - says Bluetooth can be disabled to save power.

If you click on the toggle to disable the ability to turn off wifi to save power. 
(all it does is turn off the wifi).  
The same happens if you click the toggle to disable the ability to turn off bluetooth to save power.
It turns off bluetooth.

SO THERE SEEMS to be NO WAY to disable turning off wifi or bluetooth on low power.  
All these toggles do is disable bluetooth and wifi.. Hence Airplane mode.

THIS is a important bug: either because the Power dialog is misleading (as CelticWarrior pointed out) or a problem with the mouse waking again...
  
When my mouse goes to sleep... it takes several seconds to get it to wake again and respond.... even though the mouse itself wakes up very quickly. (meaning the mouse itself wakes as soon as you click on a button).  But the cursor does not respond.....
And the settings in the power section seem to imply disabling turning off wifi or bluetooth to save power. 
At the very least, the comment on the toggle** should say:**
Turn off WiFi. 
Turn off bluetooth. 

Could someone clarify this?????  -- as my misunderstanding seems to be related to what happens to the mouse when it goes to sleep and why does it take several seconds to get it to reconnect on the Ubuntu side. 

I will start a new thread related to the bluetooth mouse problems?
Or does someone have a thought about bluetooth mouse issues with Ubuntu 20.04?

---

### Post by CelticWarrior on 2020-06-21
So, why is my answer wrong?
You pretty much said the exact same...

---

### Post by JoelParke on 2020-07-02
Your answer is exactly correct.  The issue is that it doesn't correct the text related to Bluetooth and WiFi.
For example: I was initially confused when I read: 'WiFi can be turned off to conserve power' 
This is exactly correct.
But for me, I was attempting to keep Ubuntu from ever turning off the Bluetooth or WiFi. because I have and issue with my bluetooth mouse, that when it has been idle for a while, the mouse goes to sleep, and then clicking on a button wakes it up, but it takes Ubuntu to notice the movement of the mouse for 8-10 seconds.  So I mistakenly thought that perhaps Ubuntu was turning off the bluetooth to save power. Which it was not.  So I wanted a caption under Power like:
Turn off bluetooth immediately (this will save power usage). 

So what you said was correct, but when you find bluetooth mouse dropping out, it begins to feel like somehow the Power settings might stop this. Even though the mouse dropping out is some different bug.

Sorry for the confusion, but I think a small change to the ui caption might be helpful to others (like me that were confused).

---

