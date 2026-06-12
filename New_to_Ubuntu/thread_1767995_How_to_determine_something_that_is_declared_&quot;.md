---
title: "How to determine something that is declared &quot;FAIL&quot; on shutdown"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by spacon08 on 2011-05-26
Hi,

I should say I'm new to the world of GNU/Linux and Ubuntu so forgive my ignorance. II have a query regarding something that has been declared "FAIL" on shut down. I see this FAIL status when I see the screen of white text on a black background after selecting shut down. The screen disappears quite fast so it is difficult to determine what it states as having a failed status. Any idea how I can determine what this is?

The only issue I have had with my machine is on one occasion I had to force shutdown because for some reason my machine was unresponsive after being left idle (I had a black screen with only a cursor at the top left). Could it be related to this?

I'm running 11.04 on a ubuntu pre-installed (system76) machine.

Thanks in advance.

---

### Post by AgentZ86 on 2011-05-26
> **spacon08 said:**
> Hi,

I should say I'm new to the world of GNU/Linux and Ubuntu so forgive my ignorance. II have a query regarding something that has been declared "FAIL" on shut down. I see this FAIL status when I see the screen of white text on a black background after selecting shut down. The screen disappears quite fast so it is difficult to determine what it states as having a failed status. Any idea how I can determine what this is?

The only issue I have had with my machine is on one occasion I had to force shutdown because for some reason my machine was unresponsive after being left idle (I had a black screen with only a cursor at the top left). Could it be related to this?

I'm running 11.04 on a ubuntu pre-installed (system76) machine.

Thanks in advance.

May not be a problem , but check into your logs:
System/Administration/Log File View

I'm not sure which ones you want to look at but you can speed up your search by hitting ctrl+f and you can search the log for the word failed or something that might help

I get failed -22 and things all the time in the logs but I'm not sure some of this applies to my system it may just fail because it's looking for something that is not there.

I've heard of suspend issues causing freezups and there is a solution but I only came acrossed it looking for something else, but anyhow just fyi on that

I wish I could be more help

---

### Post by lightstream on 2011-05-26
I agree that it could be just something that's not found or not present ie nothing to worry about as opposed to something which is malfunctioning.

A completely non-technical solution is to record the shutdown process on a video camera, then play it back frame-by-frame to read the message.

---

### Post by wildmanne39 on 2011-05-26
> **spacon08 said:**
> Hi,

I should say I'm new to the world of GNU/Linux and Ubuntu so forgive my ignorance. II have a query regarding something that has been declared "FAIL" on shut down. I see this FAIL status when I see the screen of white text on a black background after selecting shut down. The screen disappears quite fast so it is difficult to determine what it states as having a failed status. Any idea how I can determine what this is?

The only issue I have had with my machine is on one occasion I had to force shutdown because for some reason my machine was unresponsive after being left idle (I had a black screen with only a cursor at the top left). Could it be related to this?

I'm running 11.04 on a ubuntu pre-installed (system76) machine.

Thanks in advance.
Hi, I also agree unless you are having a problem I would not worry about it, I see those sometimes booting up but it is usually something that could not be loaded or started but it was not necessary for the use of ubuntu.

---

### Post by wolfen69 on 2011-05-26
The word fail is not neccessarily a bad thing when it comes to how linux handles operations. I see that word all the time in linux. Most of the time it just means that something can't be done that doesn't *need* to be done. If your pc is working good, I would not worry about it.

If you could see a windows pc "thinking", you would see similar things.

---

### Post by spacon08 on 2011-05-27
Cheers guys thanks for all the responses and reassurances.

---

