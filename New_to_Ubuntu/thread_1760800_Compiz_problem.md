---
title: "Compiz problem"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by BluffTrout on 2011-05-17
I have not long upgraded from 10.10 to 11.04 on my Sony Vaio VGN-FZ11M laptop but can't get Compiz to work.

I had compiz on 10.10 and it worked fine, now when I enable and change settings like the cube, it doesn't change anything.

Anyone else having / had this problem? Can't work it out!

---

### Post by linuxman94 on 2011-05-17
See this site for instructions on how to activate the cube:
[http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/]("http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/")

---

### Post by BluffTrout on 2011-05-17
> **linuxman94 said:**
> See this site for instructions on how to activate the cube:
[http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/]("http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/")
Unfortunately that doesn't solve my problem. It's not just the cube that doesn't work, even something small like wobbly windows won't work when enabled...

---

### Post by linuxman94 on 2011-05-17
Yeah i have the same problem with the wobbly windows.  If you really want the effect, choose ubuntu classic at the login screen.  We'll have to wait before all compiz effects are fully supported by unity.

---

### Post by BluffTrout on 2011-05-18
I don't particularly want wobbly windows but it was just an example. I didn't realise it was unity that was not compatible with compiz, I like unity too much to revert back to classic now.

---

### Post by wildmanne39 on 2011-05-18
> **BluffTrout said:**
> I don't particularly want wobbly windows but it was just an example. I didn't realise it was unity that was not compatible with compiz, I like unity too much to revert back to classic now.
Hi, actually unity uses compiz but when you activate somethings in compiz it deactivates the unity plug in that causes the problem, if you follow that guide you can get it to work right with unity, it takes a little more effort then before.:)

---

### Post by mcduck on 2011-05-18
> **BluffTrout said:**
> I don't particularly want wobbly windows but it was just an example. I didn't realise it was unity that was not compatible with compiz, I like unity too much to revert back to classic now.

It's exactly as compatible with Compiz as any other Compiz plugin is. :D

Just make sure you actually read the messages about conflicting keyboard shortcuts etc. when enabling different Compiz plugins.

edit. For the reference, I just enabled wobbly windows on my laptop. No ptoblems there. Enabling it gave a conflict message about Wobbly Windows & Snapping Windows plugins providing same functionality, so I told it to disable snapping windows. The top panel got a bit bugged but that was fixed simply by restarting Unity ("unity --replace"). Works just fine.

---

### Post by BluffTrout on 2011-05-18
Is there a way to reset the compiz settings to default or would reinstalling compiz do that for me? Still having no luck.

---

### Post by wildmanne39 on 2011-05-18
> **BluffTrout said:**
> Is there a way to reset the compiz settings to default or would reinstalling compiz do that for me? Still having no luck.
Hi, click on the reset unity and compiz below this text in my signature.:D

---

### Post by BluffTrout on 2011-05-18
> **wildmanne39 said:**
> Hi, click on the reset unity and compiz below this text in my signature.:D

Thanks, greatly appreciated!

---

### Post by wildmanne39 on 2011-05-18
> **BluffTrout said:**
> Thanks, greatly appreciated!

Hi, your welcome if you need more help post back here and I will try to help.:D

---

### Post by Salese_B on 2011-05-31
Hi, I'm having the same problem here. Reseting the Unity configs to default does not resolve the issue... Instead, when I run [unity --reset] it flashes sometimes and a left bar appears, but the whole system freezes and I need to restart the computer.

Any other suggestions? Every single effect stopped working after the update to 11.04. And I only would like the use the transparency on my console... Hahahaha...

Thanks anyway :)

---

### Post by wildmanne39 on 2011-05-31
> **Salese_B said:**
> Hi, I'm having the same problem here. Reseting the Unity configs to default does not resolve the issue... Instead, when I run [unity --reset] it flashes sometimes and a left bar appears, but the whole system freezes and I need to restart the computer.

Any other suggestions? Every single effect stopped working after the update to 11.04. And I only would like the use the transparency on my console... Hahahaha...

Thanks anyway :)
Hi, did you restart after letting it run that command for about 3 minutes?

---

### Post by Salese_B on 2011-05-31
Well... I ran [unity --reset] and waited about two or three minutes, then I assumed something went wrong.

Do it take some minutes to complete?

---

### Post by wildmanne39 on 2011-05-31
> **Salese_B said:**
> Well... I ran [unity --reset] and waited about two or three minutes, then I assumed something went wrong.

Do it take some minutes to complete?

Hi it never completes it just shows nothing after a while, that is why I said wait 3 minutes then reboot,Use ctrl alt delete I think will get a restart

---

