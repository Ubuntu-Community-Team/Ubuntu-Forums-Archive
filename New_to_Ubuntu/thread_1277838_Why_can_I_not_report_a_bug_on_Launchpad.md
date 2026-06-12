---
title: "Why can I not report a bug on Launchpad??"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-28
I want to report a new bug on launchpad, but whenever I click on the "report a bug" link it takes me to this page:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)


When it should be going here: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

I don't want to read the community documentation on reporting a bug, I want to report one!!

And yes, I am logged into my account on launchpad.

---

### Post by wojox on 2009-09-28
Did you try using apport? Alt + F2 then ubuntu-bug <application>.

They under went some changes over there I noticed recently so maybe something is messed up with the link?

Maybe you should report a bug on reporting bugs. :lolflag:

---

### Post by humphreybc on 2009-09-28
I would use apport but the bug is about suspend/resume failure, so not really an application to report on.

Haha yeah well, if I could, I would!

Can someone click on the bug report link in my first post and see if it redirects to the community docs for anyone else?

---

### Post by philinux on 2009-09-28
> **humphreybc said:**
> I want to report a new bug on launchpad, but whenever I click on the "report a bug" link it takes me to this page:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)


When it should be going here: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

I don't want to read the community documentation on reporting a bug, I want to report one!!

And yes, I am logged into my account on launchpad.

If you know the package then use:-

```
ubuntu-bug packagename
```

I agree it's a bit convoluted on launchpad at the moment. Seems like they need to cut down on bug reports.

---

### Post by wojox on 2009-09-28
I tried the link and it took me to the Launchpad login page. So I logged in and it took me to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by humphreybc on 2009-09-28
Hmm I'm just reporting one now using:

ubuntu-bug <linux image packagename>

and that seems to work okay. Too bad you can't report directly on launchpad!

---

### Post by hansdown on 2009-09-28
The report link works for me humphreybc.

---

### Post by humphreybc on 2009-09-28
Weird so it doesn't work for me or wojox, but it does work for you, hansdown.

---

### Post by wojox on 2009-09-28
> **hansdown said:**
> The report link works for me humphreybc.

Did you login ?

---

### Post by hansdown on 2009-09-28
> **wojox said:**
> Did you login ?

Yeah, that blasts me to that same page too.

Haha! You should file a bug report.

If only it worked.

---

### Post by diesch on 2009-09-28
The community documentation on reporting a bug tells you how to report a bug in Launchpad:
[Filing bugs at Launchpad.net]("https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net")

---

### Post by hansdown on 2009-09-28
Found a page to report problems with launchpad.

[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by humphreybc on 2009-09-28
> **diesch said:**
> The community documentation on reporting a bug tells you how to report a bug in Launchpad:
[Filing bugs at Launchpad.net]("https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net")

Yeah, but it tells you to go to Launchpad and click on "Report a bug" - which in turn takes you back to the community docs...

...so it's a lovely vicious cycle/catch 22 scenario.

Launchpad Report a Bug > Community Docs page on how to report a bug > Launchpad Report a Bug > Community Docs page on how to report a bug.... etc etc!

The only way it seems to report a bug at the moment is via apport... unless it's just us?

---

### Post by humphreybc on 2009-09-28
Check out my bug report here:

[https://bugs.launchpad.net/malone/+bug/438476](https://bugs.launchpad.net/malone/+bug/438476)

---

### Post by humphreybc on 2009-09-28
ACTUALLY, it seems that this is not a bug, but deliberate!

The first paragraph of the community docs page:

> 
If you've come here when trying to file a bug about Ubuntu in Launchpad this was deliberate. Please read the following documentation regarding how to report a bug about Ubuntu.


That's ridiculous. We now have to do this to report a bug through launchpad:

> 
To file a bug against a specific package use a url similar to the following, [http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect](http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect), where PACKAGENAME is the name of the source package about which you want to file the bug.

Note the "no-redirect" option in the URL. Evidently Ubuntu are trying to cut down on bug reports by making you read a whole page on how to report a bug and then forcing you to create your own URL for reporting a bug. Sigh.

---

### Post by hansdown on 2009-09-28
> **humphreybc said:**
> Check out my bug report here:

[https://bugs.launchpad.net/malone/+bug/438476](https://bugs.launchpad.net/malone/+bug/438476)

Sweet! You rock humphreybc.

Wonder how long To fix.

---

### Post by diesch on 2009-09-28
> **humphreybc said:**
> Yeah, but it tells you to go to Launchpad and click on "Report a bug" - which in turn takes you back to the community docs...


No, this has changed some time ago. Now it's basically
> 
To file a bug against a specific package use a url similar to the following, [http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect](http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect), where PACKAGENAME is the name of the source package about which you want to file the bug. 

---

### Post by hansdown on 2009-09-28
> **humphreybc said:**
> ACTUALLY, it seems that this is not a bug, but deliberate!

The first paragraph of the community docs page:



That's ridiculous. We now have to do this to report a bug through launchpad:



Note the "no-redirect" option in the URL. Evidently Ubuntu are trying to cut down on bug reports by making you read a whole page on how to report a bug and then forcing you to create your own URL for reporting a bug. Sigh.

That's.....strange.

---

