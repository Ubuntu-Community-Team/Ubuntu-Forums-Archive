---
title: "[SOLVED] Enable / disable network connection"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-09
Hi..... again!!
I can't find a simple way to disable / enable my network connection ( to the internet).
In Win XP I have an icon on the task bar, click it and select **enable / disable** the connection - but in Ubuntu??????
I'm using Hardy and +64
Cheers

---

### Post by rbc on 2008-12-09
On the right side of the top panel (unless you have moved it) should be network icon. Right click on it, then check/uncheck "Enable Networking"

---

### Post by thadacto on 2008-12-09
Thanks rbc; therein lies my problem.
My panel was not functioning correctly and I deleted it. Now I can't find the same icon. I have one  which is:
Network Connection: ethO
but there is no provision for enabling nor disabling. Where can i find the original one??

---

### Post by wizard10000 on 2008-12-09
another way is

```
sudo /etc/init.d/networking stop
```

You'd start the network back up by using 'start' instead of 'stop'.  You can also restart networking by using 'restart'.

Hope this helps -

---

### Post by thadacto on 2008-12-09
Eventually I'm back - having problems getting into Ubuntu Forums - must be so many people with problems.
Thanks wizard1000, but I was trying to avoid having to go into the terminal every time. I'm sure there's an icon somewhere (or maybe that's only in Windows?!

---

### Post by Tatty on 2008-12-09
have you tried right-clicking on the icon that says "Network Connection: ethO"?

**EDIT:** Just realised this is the network monitor applet, so this wont help.  See my next post.

---

### Post by genus_001 on 2008-12-09
If you right click in your panel, and click "Add to panel", you should be able to find the applet that allows you to enable/disable in there.

---

### Post by Tatty on 2008-12-09
> **genus_001 said:**
> If you right click in your panel, and click "Add to panel", you should be able to find it in there.

No, network manager does not get added via this way.  However, you can use this to add a notification area, which you need for the network manager to live in.

Once this is added then the network manager applet should appear in the notification area when it is run.  This should happen automatically when the computer is booted, but if not then: ```
nm-applet
```

---

### Post by thadacto on 2008-12-09
Hi Tatty,
Yep, it gives: Property - no provision for enable / disable
               Help      - Nothing there about enable / disable
               About    - nothing there
               Remove from panel
               Move
               Lock to panel.

It's a mystery!

---

### Post by mikewhatever on 2008-12-09
> **thadacto said:**
> Eventually I'm back - having problems getting into Ubuntu Forums - must be so many people with problems.
Thanks wizard1000, but I was trying to avoid having to go into the terminal every time. I'm sure there's an icon somewhere (or maybe that's only in Windows?!

May I point out that there was an icon, but you opted to delete it.

---

### Post by Tatty on 2008-12-09
> **thadacto said:**
> Hi Tatty,
Yep, it gives: Property - no provision for enable / disable
               Help      - Nothing there about enable / disable
               About    - nothing there
               Remove from panel
               Move
               Lock to panel.

It's a mystery!

See my last two posts.  You need to add a notification area by right clicking on a panel and selecting "add to panel"

---

### Post by thadacto on 2008-12-09
I opted to delete it, the whole panel, because it wasn't working correctly. Whenever I used the left or right arrows, the panel moved in that direction but left a line of blurb, applets etc. If I used the auto hide, I was left with a dark grey bar across the top of the screen. So I thought the best way was to delete the whole panel and make a new one. but I can't find the correct icon. In windows, I could find the program and just create a short cut and use any icon. Seems it's not so in Ubuntu.
I'll have a go at some of the previous suggestions and see what happens.

---

### Post by Tatty on 2008-12-09
> **thadacto said:**
> I opted to delete it, the whole panel, because it wasn't working correctly. Whenever I used the left or right arrows, the panel moved in that direction but left a line of blurb, applets etc. If I used the auto hide, I was left with a dark grey bar across the top of the screen. So I thought the best way was to delete the whole panel and make a new one. but I can't find the correct icon. In windows, I could find the program and just create a short cut and use any icon. Seems it's not so in Ubuntu.
I'll have a go at some of the previous suggestions and see what happens.

Im not quite sure what you mean.  Do you have a Panel available on your desktop?  If so then all you need to do is right-click on it then select "Add to panel".  Then add a Notification Area to the panel.

Reboot your machine, and when it comes back up the network manager applet should appear in the Notification Area.

---

### Post by thadacto on 2008-12-09
Hi tatty - yep, that code got the applet into the Add To Panel pop-up box. 
It's the "wired network connection" applet that I was looking for.
Got it and thumbs up!! Many thanks.

---

