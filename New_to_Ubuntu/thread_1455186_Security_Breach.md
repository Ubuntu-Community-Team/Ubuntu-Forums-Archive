---
title: "Security Breach"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Swatfoot on 2010-04-15
Hello everyone, I am writing concerning a security problem that while I was sleeping my Kubuntu was restarted and msql was open and partly configured.
I'm not sure what logs to check for other occurrences or what should I install to avoid this sort of thing again.

---

### Post by QIII on 2010-04-15
Compromised by someone who had physical access?

Here's a pretty good bit on security:  [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Swatfoot on 2010-04-15
> **QIII said:**
> Compromised by someone who had physical access?

I Sleep about Six Feet away from my PC, I doubt anyone could sneak past me in my room. I should have taken a screen shot of the window that was open. Is there a way to check the logs?

---

### Post by QIII on 2010-04-15
In the link I included in my post, the bodhi.zazen includes this link:

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

I would read bodhi.zazen's tutorial and take a look at the links he provides.  He has done a pretty exhaustive job.  Far easier to read it there than for someone to try to recreate the wheel.

Not trying to put you off.  I'm just saying there is a prepared resource already, and the author is very well versed in such things.

---

### Post by airtonix on 2010-04-15
> **Swatfoot said:**
> Hello everyone, I am writing concerning a security problem that while I was sleeping my Kubuntu was restarted and [COLOR=Red]**msql was open and partly configured**[/COLOR].
I'm not sure what logs to check for other occurrences or what should I install to avoid this sort of thing again.

sounds like you left automatic updates turned on with the feature that answers yes to install them.

when you say "mysql was open" do you mean it was halfway through the install process of configuring the setup ? 

if so i doubt you were comprimised.

protip : suspend your machine when you sleep, or close all unnecessary ports.

---

### Post by Swatfoot on 2010-04-15
Thank you for the replies and links,It seems my work has just started but then again when does It ever stop ;)

---

