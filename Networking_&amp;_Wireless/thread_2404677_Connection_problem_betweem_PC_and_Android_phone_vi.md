---
title: "Connection problem betweem PC and Android phone via KDE connect"
date: 2018-10-27
forum: Networking &amp; Wireless
---

### Post by WimiBuntu on 2018-10-27
Hi

Yesterday I installed on my Ubuntu 18.04 KDE Connect and also on my phone with Android 7. All is well, they recognize each other and I can even browse through the files on the phone. Now I wanted to copy my photos (a few Gb) from the phone to the PC. But after a few second the phone dims the screen, then goes black and soon after that the connection seems to get lost. Then I get an error message about error splicing and a missing transport endpoint.

Now I do not know what to do. On the phone I already checked the only option that I found to keep the wifi alive. But it was already switched on.

On the Internet I found people stating that it had to do with large files. So I tested it by keeping the phone awake, again and again touching the display. Then the file transfer won't break off. But it did not want to do this permanently.

Best regards

---

### Post by cmcanulty on 2018-10-27
I would just set the screen timeout to a few minutes temporarily and transfer everything you want then reset timeout to whatever you prefer.

---

### Post by WimiBuntu on 2018-10-27
I have tried to delay the lock to 5 min. No luck.
I tried to set up the laptop as a device for smart lock. No luck.
I also disabled the network lock, which is not recommended. But still no luck :(

---

### Post by bijayalaxmi1808 on 2018-10-28
I think it is the Android phone which is causing the issue.
Looks like the Android phone is connected to a Wi-fi AP and the wi-fi link goes to sleep when the screen is turned off.

You can prevent the wi-fi from going to sleep mode when the screen is off.

On your Android phone: Go to Settings > Wi-Fi settings > Configure > Keep Wi-Fi- on during Sleep - Set this to [B]Always
[/B]The above navigation is for my Honor phone[B].
[/B]If you have a different phone then the navigation might change but the end setting (**Keep Wi-Fi- on during Sleep**) should be same.

That's all. I hope this will help you.

---

### Post by WimiBuntu on 2018-10-28
Thank you, but as mentioned in the initial post, I already had the wifi setting switched to always. Did not solve the issue.

However, yesterday I set the dim screen setting to the max of 10 minutes. And then I touched the display again and again after a few minutes. Still the copy process of my files broke off, but only after 45 minutes or so. Still, I find it curious that it has something to do with the phone being not dimmed.

---

