---
title: "Karmic 9.10 Freezing - Where do I Start Troubleshooting?"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by twm3 on 2009-11-28
To Those with the Patience of Saints,

Be thee prepared as I know enough to be dangerous but not much more.

Abstract: Dell D630 Karmic 9.10 Ubuntu Freezing - Where do I Start Troubleshooting?

Details: Had been run 9.04 since May/June with the occasional crash - perhaps once every three or four weeks. Since 9.04 was easier to use than Windoze and more stable, I can overlook that occasional crash. Bottom line: I believe the hardware is stable.

Upgraded to 9.10 on the day of release. Until about a week ago, Karmic 9.10 was crashing about once a week. Seemed as though crashes were occurring when using Kmail. Crashes were weird as system would go away, blink, and then would present me with the login screen. 

In the past week, the freezes (versus crashes but the end effect is the same) have upped themselves to once to three times a day. :-( Perhaps to the point where 9.10 is of questionable use.

Finally got PO'ed enough yesterday and did a total install (not an upgrade but a clean install). Thank gahd I put /home on another partition (why isn't that standard - seems like best practice) so minimal time was lost. All upgrades are in place and kernel is x.x.15 (should be most stable release kernel).

Then system froze on me again. Enough is enough.

What I have noticed:

[LIST=1]
[*]Kmail and Firefox 3.5.5 are running. But then again, Kmail is always running while there is usually always, but not all the time, a Firefox process running (minimized or not minimized).
[*]Keyboard does not respond. Ctrl-Alt-Del (why not try if the Windoze key combination?) doesn't do anything despite me wishing it would. Ctrl-Alt-Bksp does not do anything (Ctrl-Alt-Bksp has been assigned to restarting X). Caps Lock LED does not turn on when depressed.
[*]Sometimes during the freezes, it looks as though something is going on. CPU usage will go to 100%. Some keyboard input is accepted but takes minutes to be echoed. Patience after five or so minutes diminishes to nothing and I power cycle the system.
[/LIST]
SO HOW DO I START TROUBLESHOOTING AND/OR REPORTING THIS BEHAVIOR? 

I read the bug reporting and that makes sense if one does know which module is misbehaving. Unfortunately I don't which module it is. If my life depended on it, I would say that it is X that is freezing. Do I just take a stab in the dimness (not exactly dark) and report as an X crash? In whatever case it is that is crashing and/or freezing, what do I submit?

Thanks in advance for any and all words of wisdom, help, etc. on how to start reporting and/or solving this issue.

Oh, one more thing. I HATE asking for help. Besides asking for help here, where would you go for the basic steps on how to attack an issue like this?

~Tom

---

### Post by kaurman on 2009-11-28
Hi,

Firstly, I'd have a look at the system logs.

System-->Administration and then system log viewer. E.g have a look at dmesg and see if it has any valuable data in it.


K

---

