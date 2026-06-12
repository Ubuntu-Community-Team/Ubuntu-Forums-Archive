---
title: "Ubuntu switches to low-graphics mode when unattended, intermittently"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-06-08
When I leave my computer and later return, depending on how long I've been away, I find the screen-saver running, the screen turned off, or the computer suspended.

That is how it should be.

But, sometimes -- and I have no clue why -- when I return, I see the following message on a black screen:[INDENT][COLOR=Navy]Ubuntu is running in low-graphics mode.

Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.[/COLOR] 
[/INDENT]The message gives several options. Despite some experimentation, I find that the only way I can get running again is to reboot.

Do you have any idea what is happening or, better, how to fix it?

I have Lucid 10.04 with a dual-screen desktop.

---

### Post by Paddy Landau on 2010-06-10
Bump?

---

### Post by sydbat on 2010-06-10
I take it you never had this problem before. I wonder, then, if one of the monitor connections is loose or becoming faulty? Also, the video card might be going (had that happen to me last fall) and creating intermittent connection during sleep. Or your monitor(s) are crapping out.

So, my questions are:
1) How old is the video card?
2) Are the connections solid? If so, how are the wires?
3) Age and type of monitors? Last time you vacuumed them out? (strange I know, but I had a CRT that started making popping noises and it turned out to be dust build up inside)

Those are the things I would look at first. I'm sure you have, but it's always good to double check.

---

### Post by Paddy Landau on 2010-06-10
> **sydbat said:**
> I take it you never had this problem before.
I upgraded to Lucid (fresh install) about two weeks ago, and it's happened since then. But you make a good point. The drivers for my system seem to have been updated with Lucid, meaning that the display works better than it used to.

> **sydbat said:**
> 1) How old is the video card?
2) Are the connections solid? If so, how are the wires?
3) Age and type of monitors? Last time you vacuumed them out?

[LIST=1]
[*]I bought the laptop new about three years ago, so not all that old.
[*]The wires look in good condition and the connections solid.
[*] I'm using a dual monitor; the attached monitor is rather  older; I don't remember how old. I cannot vacuum; it's a laptop and I'd be too nervous to open it up!
[/LIST]
 
Given your comments, and the history of my video card, I'm of the opinion that the driver probably is not quite right. So, unless anyone has any bright ideas, I think I'll have to write this off as a hardware problem (a video card created for Windows but used under Linux).

I'll experiment with my power settings to find out whether it's a particular event (it only happens when I'm away from my computer for a while). Unfortunately, as it's intermittent, I cannot easily test!

Thanks for your time.

---

### Post by sydbat on 2010-06-10
A friend had a laptop a couple of years ago and found that suddenly a few things stopped working properly. I think it was a Dell. He was running XP. 

Anyway, he finally got tired of things messing up and (because it was out of warranty) decided to open it up. He found a few things amiss...like the power connector (to plug in for recharging) on the motherboard had come loose. Closer inspection showed there was no solder holding it onto the board, so he soldered it. Then he found similar things all over the board and tried to fix as many as he could. He did get another 6 months out of it.

So, I wonder if there are loose components on your motherboard. It does happen. 

If you are unsure whether to open it yourself, take it into a trusted computer repair shop and have them poke around. Of course, after you eliminate all other possibilities first.

---

### Post by Paddy Landau on 2010-06-10
Thanks, sydbat.

I'm persuaded that you're right and that hardware is to blame.

I won't open up the laptop -- I can't afford to break it! -- but I may get, as you say, a "trusted" computer expert to look.

---

