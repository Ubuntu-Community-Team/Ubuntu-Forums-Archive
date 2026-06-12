---
title: "Wont Display Discharging"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by CrazzzyBudha on 2011-03-08
The indicator applet will not display that my laptop battery is discharging. It has been working fine until today. When plugged in it displays that the battery is charging and an estimate until it is charged. When it is not plugged in, it displays that the battery is at full charge and not discharging. Under "details" it displays that the battery has some level below full charge (58.6w when fully charged, energy: 36.7w) which does not change whether plugged in or not. But the "state" changes from "charging" when plugged in the "Charged" when discharging.

Any ideas? Thanks a lot!

---

### Post by DGINSD on 2011-03-08
Very interested in details on this issue I have an identicle issue with my laptop (Dell Inspiron 1150 w/Ubuntu 10.10) also won't hibernate with the lid closing which I think is related.

What drivers are related to these type of issues?

To OP'er you'll want to list all your details I belive machine make model OS version and what not. I'll be hoping to gain insight into my own issues base on solutions to yours

---

### Post by cap10Ibraim on 2011-03-08
hey install this small utility and test the following
```

sudo apt-get install acpi

```
the run from the terminal while discharging 
```

acpi

```
currently my output is 
```

Battery 0: Discharging, 62%, 01:25:56 remaining

```

---

### Post by DGINSD on 2011-03-08
Dont have my 'puter handy now but as soon as I do I'm on it would love to get this one solved.

---

### Post by DGINSD on 2011-03-08
ran it on batt. power and it listed the following:

Battery 0: Discharging, 96%, 01:20:03 remaining

ran it with the charger pluged in and listed this:

Battery 0: Full, 100%, rate information unavailable

the battery icon displayed was what looked to me to be an empty battery even though the acpi command said I was at 96%, whats that about?

---

### Post by CrazzzyBudha on 2011-03-08
Hate to make this post and kind of abandon it. I had the problem i originally described (Hardware is an Acer Aspire 4820T, Ubuntu 10.10 btw) for a day or so, and after driving me nuts for a little while I noticed tonight that it has magically gone away. 

My ACPI output is currently:
```
Battery 0: Discharging, 85%, 04:55:32 remaining

```

And the indicator applet is reflecting as much. Wish I could tell you what fixed it, but since I posted I haven't tried so much as a restart. 

BTW, check out my awesome battery life :D

Edit: Since someone else is having a similar problem I can keep an eye on this and wait to mark "solved". Then again it could start acting up again tomorrow for all I know

---

### Post by cap10Ibraim on 2011-03-08
> **CrazzzyBudha said:**
> Hate to make this post and kind of abandon it. I had the problem i originally described (Hardware is an Acer Aspire 4820T, Ubuntu 10.10 btw) for a day or so, and after driving me nuts for a little while I noticed tonight that it has magically gone away. 

My ACPI output is currently:
```
Battery 0: Discharging, 85%, 04:55:32 remaining

```

And the indicator applet is reflecting as much. Wish I could tell you what fixed it, but since I posted I haven't tried so much as a restart. 

BTW, check out my awesome battery life :D

Edit: Since someone else is having a similar problem I can keep an eye on this and wait to mark "solved". Then again it could start acting up again tomorrow for all I know

that's my point , it's not a hardware issue , the problem is with the indicator in the panel , this applet has random errors ,

---

### Post by DGINSD on 2011-03-08
> **cap10Ibraim said:**
> that's my point , it's not a hardware issue , the problem is with the indicator in the panel , this applet has random errors ,

So it's a known issue with more than one type of laptop? What are the chances for a fix?

---

### Post by cap10Ibraim on 2011-03-08
I don't know check out the related bugs 
[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=battery+applet+&orderby=-importance&search=Search&field.status:list=NEW&field.status:list=INCOMPLETE_WITH_RESPONSE&field.status:list=INCOMPLETE_WITHOUT_RESPONSE&field.status:list=CONFIRMED&field.status:list=TRIAGED&field.status:list=INPROGRESS&field.status:list=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=battery+applet+&orderby=-importance&search=Search&field.status:list=NEW&field.status:list=INCOMPLETE_WITH_RESPONSE&field.status:list=INCOMPLETE_WITHOUT_RESPONSE&field.status:list=CONFIRMED&field.status:list=TRIAGED&field.status:list=INPROGRESS&field.status:list=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

---

### Post by CrazzzyBudha on 2011-03-09
If it is a problem with the indicator applet, maybe you could try a different one to see if it works. Searching "battery" in the software center brings up Battery Monitor (Batmon). I don't know of any others.

---

