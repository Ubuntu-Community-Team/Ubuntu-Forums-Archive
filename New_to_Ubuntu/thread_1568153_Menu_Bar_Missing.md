---
title: "Menu Bar Missing"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Information Overload on 2010-09-04
My menu bar or panel or whatever its called is missing. The thing where all my applications go and the power button and everything is gone. I don't know what I did, I was trying to install an application and all the sudden it was gone. My computer then froze and I had to do a cold-hard shutdown by holding the button because I had no other option. I know a cold shutdown is a bad thing but nothing seems to be wrong other than the darn menu bar being missing. Now it went missing before the freeze so I don't know what I did wrong. I'm just about fed up with Ubuntu being a pain in the neck. Is there some known issue with Ubuntu Netbook Edition? Because I'm having all kinds of troubles. This is the third time I've had to reinstall and I don't want to do it again. Help is greatly appreciated. I've searched the internet and failed to come up with a solution. I don't have a bottom menubar so thats not an option, I've tried killall gnome panel and I've done metacity --replace but nothing seems to work. Please help. :(

---

### Post by kmsalex on 2010-09-04
Forgive me if this is the first thing your tried but instead of kill gnome-panel have you tryed just, gnome-panel or sudo gnome panel?

---

### Post by gordintoronto on 2010-09-04
I've never used the netbook edition. A Google search turned up:
"Open the configuration editor by pressing Alt + F2, then type gconf-editor and hit ENTER,
In the Configuration Editor, browse to /apps/panel/toplevels/top_panel
Look for the key "auto_hide", click on it to toggle its value." 

which might get you somewhere.

A computer which freezes might have a hardware problem...

---

### Post by Information Overload on 2010-09-05
I've tried all the options you've suggested already and nothing worked. When I did gnome-panel it came up with no application installed so I figured my system was fried for the fifth time. *Sigh* I don't know what I do but I always end up killing Linux. However, I'm not going to give up. I've reinstalled Ubuntu and am going to make an image of the OS if I manage to get it customized without killing it again... Thanks for trying to help. :) But I think its just my bad luck right now.

As for a hardware problem I've been running windows on this thing for about a year and I never had it freeze on me. So if it is a hardware problem its how Linux is using the hardware not the actual hardware itself.

---

