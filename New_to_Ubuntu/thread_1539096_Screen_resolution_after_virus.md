---
title: "Screen resolution after virus"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by sarum on 2010-07-26
I have an ex-office computer dual booting XP & Hardy Heron. All has worked well for a year or so. Then a virus struck, I think,(XP is protected by Avir:?), and was cleaned up. The Heron however is not well. On start up the screen is black with odd colours, and then opens at 600x800. System/pref:/screen gives only 600x800 - no alternatives.
Inserting the live (Heron) CD reverts to 1042x760 resolution.
Is there a way to use the live CD to get the resolution back to where it was?, or perhaps the CLI?
Thanks for any help...............sarum

---

### Post by jtarin on 2010-07-26
You say a virus struck.....what did it affect in Windows? Do you have the name of the virus detected? 
Try the terminal command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by k3lt01 on 2010-07-26
System > Preferences > Monitors. Adjust your screen resolution there.

It is highly unlikely a Windows virus has done this, not impossible but unlikely. Personally I'd be looking for other problems.

---

### Post by rolnics on 2010-07-26
Have you tried setting up your video settings again? 

If the live-cd of Hardy works fine, you might want to just copy the xorg.conf across to replace the one on your install?

---

### Post by sarum on 2010-07-26
Thanks for your replies.jlarin,the trouble started with Hardy's resolution, so I switched to XP and ran the antivirus without noting any names; I think there may have been a couple of things to clear up. Also I ran Cclean thinking that what's wrong with XP would affect the dual boot Linux. I'm told this isn't so.
The code you enclosed gets the answer 'xserver-org is not installed' This seems to be the problem? rolnics' reply suggests copying from the live CD - I shall try this; not sure how, but I'll give it a go. Any help in how to will be appreciated.
k3lt01 - thanks for your reply. I tried sys/pref/monitors, but there was no alternatives. Thanks again all.....sarum

---

### Post by jtarin on 2010-07-26
[Try xrandr]("http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html")

---

### Post by Wim Sturkenboom on 2010-07-27
One wonders how a problem in Windows can cause a graphics 'problem' under Linux in a dual boot setup.

Answer: it can't and there is no relation unless the virus managed to fry your video card and/or monitor.

---

### Post by VH-BIL on 2010-07-27
> **Wim Sturkenboom said:**
> One wonders how a problem in Windows can cause a graphics 'problem' under Linux in a dual boot setup.

Answer: it can't and there is no relation unless the virus managed to fry your video card and/or monitor.

+1
Have you tried to access your Linux files from your Windows partition. If you can't I doubt the virus could. It is quite doubtful that software can do damage to hardware too.

---

### Post by sarum on 2010-07-28
Thanks for the last 2 replies; I was mistaken in thinking that the trouble with Ubuntu might have been caused by what had happened to XP.
rolnics' suggestion of copying xorg-conf from the live CD solved it. So I'm back to 1024x768, and am very grateful to you all.......sarum

PS. There's been a lot of 'resolution questions and answers' in the past involving cli codes and so on. Is rolnics' a quick and easy solution for all?

---

