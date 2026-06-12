---
title: "Microsoft Live Meeting on Karmic"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by beanco on 2010-04-29
Anybody have any idea how to get Microsoft Live Meeting running on Ubuntu?


I am involved with an international Web Conference  program in the EU, and *unfortunately* the 5 member parties/countries, have decided to use MS Live Meeting. -I tried to get them to think about open source solutions but tht was dead from the start.

so, if there is a way to get MS LM running through Ubuntu, it would be nice.... I really do not want to do a dual boot MS and Ubuntu....

Thanks

robi

---

### Post by Mark Phelps on 2010-04-29
You could try installing Wine and then installing LiveMeeting with that ... but there are no testing results for it in the WineHQ database, and the results for NetMeeting (LiveMeeting's predecessor) were rated Bronze -- the worst you can get and still have it working.

It doesn't look encouraging...

---

### Post by aperomsik on 2010-06-03
The Live Meeting web client was working fine for me on Karmic as long as I had sun-java5-jre installed. (As attendee anyway... I don't think I ever tried as presenter.)

That particular flavor of JRE is not available in Lucid, and now with sun-java6-jre installed the Live Meeting web client tries to load but gets stuck during loading. The meeting console window opens, but a tiny window opens in front of it with no visible content and then nothing else happens.

---

### Post by beanco on 2010-06-04
OK I am on Karmic.. I will try JRE 5 and see if it works.

BTW, we are having all kinds of sound issues on our MS computers at the shcool....

Robi

---

### Post by olyerickson on 2010-08-31
I've experienced the same symptoms as aperomsik, but trying to run Live Meeting in Firefox 3.6.8 under Lucid.   

* Go to a Live Meeting test page: [http://go.microsoft.com/fwlink/?LinkId=90703](http://go.microsoft.com/fwlink/?LinkId=90703) 
* Click "Join meeting"
* Wait for "Compatibility Test" to render

It's at this point that it epically fails...

John

---

### Post by cirorodrigues on 2010-11-05
> **aperomsik said:**
> The Live Meeting web client was working fine for me on Karmic as long as I had sun-java5-jre installed. (As attendee anyway... I don't think I ever tried as presenter.)

That particular flavor of JRE is not available in Lucid, and now with sun-java6-jre installed the Live Meeting web client tries to load but gets stuck during loading. The meeting console window opens, but a tiny window opens in front of it with no visible content and then nothing else happens.

Same issue for me. When using 10.04 I got it working with Java 1.6.15. After 10.10 update, with Java 1.6.21, I couldn't manage to get it working again.

---

### Post by bedge on 2010-11-08
Same here, not working.
The meeting opens as a small square with no data/controls/window decorations and is completely blank and unresponsive and cannot be moved or resized.
Same result for chrome/ffox.

#> java -version

java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Server VM (build 17.1-b03, mixed mode)

---

### Post by cirorodrigues on 2010-11-19
I managed to fix it. Not sure it will last, but it's working now.

Go to System > Preferences > Sun Java 6 Plugin Control Panel.
Go to tab Advanced, open Security, open Mixed Code, and select option "Enable - hide warning and run with protections".

I think the tiny window is an security alert from any type, so this option just let the process follow.
If you're not confortable to this security setting, just remember to get back to previous setting after LiveMeeting usage.

Let me know if this works for you.

---

### Post by aperomsik on 2010-11-19
@cirorodrigues, great find! I linked to your post from a related Launchpad [bug]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/589524")... maybe someone can fix it.

---

### Post by bedge on 2010-11-19
> **cirorodrigues said:**
> I managed to fix it. Not sure it will last, but it's working now.

Go to System > Preferences > Sun Java 6 Plugin Control Panel.
Go to tab Advanced, open Security, open Mixed Code, and select option "Enable - hide warning and run with protections".

I think the tiny window is an security alert from any type, so this option just let the process follow.
If you're not confortable to this security setting, just remember to get back to previous setting after LiveMeeting usage.

Let me know if this works for you.

Works for me. Thanks!

---

### Post by bedge on 2010-11-19
> **cirorodrigues said:**
> I managed to fix it. Not sure it will last, but it's working now.

Go to System > Preferences > Sun Java 6 Plugin Control Panel.
Go to tab Advanced, open Security, open Mixed Code, and select option "Enable - hide warning and run with protections".

I think the tiny window is an security alert from any type, so this option just let the process follow.
If you're not confortable to this security setting, just remember to get back to previous setting after LiveMeeting usage.

Let me know if this works for you.

Confirmed. This fixes the problem.

---

### Post by clarkNerd on 2011-06-02
I was also able to get this working using 11.04 Natty Narwhal.  I however have installed the Sun 1.6 JDK (1.6.0_25) manually so I don't have access to the security panel from the Ubuntu Menus.  In order to fix this for me, I had to do the following steps:

[LIST=1]
[*]Open a console and run 'jcontrol' (will be in the same directory as javaws)
[*]Click on the 'Advanced' tab
[*]Open the 'Security' menu
[*]Open the 'Mixed code...' Menu
[*]Click 'Enable - hide warning and run with protections'
[*]Click OK
[/LIST]

---

