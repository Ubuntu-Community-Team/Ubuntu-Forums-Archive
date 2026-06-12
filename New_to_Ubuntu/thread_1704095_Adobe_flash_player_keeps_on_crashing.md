---
title: "Adobe flash player keeps on crashing"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-03-10
Dear All,
This is exasperating. 

Adobe flash player is crashing at all the sites. I have checked my installation using [http://www.mozilla.com/en-US/plugincheck/](http://www.mozilla.com/en-US/plugincheck/),  and it says that Shockwave Flash, Java(TM) Plug-in, and Totem are up to date.

The crashing occurs in Mozilla, Opera and Chrome. Restarting did not help.

Could you please tell me what to do?

---

### Post by el_koraco on 2011-03-10
try epiphany?

---

### Post by mmasroorali on 2011-03-10
Installed and tried epipheny. Youtube and other sites shows while working. But epiphany itself crashes like crazy. Tried almost ten times, crashes as soon as I start a video in youtube.

---

### Post by NightwishFan on 2011-03-10
Youtube seems to crash a lot unless you disable cookies for it. Problem is, if you disable cookies you are not able to log into your account. If you just watch, than it is fine. (Remember to delete current cookies for it as well)

You can do this in Firefox under Edit -> Preferences -> Privacy. Do custom settings and block youtube cookies, and delete all the cookies already used below.

---

### Post by mmasroorali on 2011-03-10
> **NightwishFan said:**
> Youtube seems to crash a lot unless you disable cookies for it. Problem is, if you disable cookies you are not able to log into your account. If you just watch, than it is fine. (Remember to delete current cookies for it as well)

You can do this in Firefox under Edit -> Preferences -> Privacy. Do custom settings and block youtube cookies, and delete all the cookies already used below.

Clearing cookies helped, for Mozilla and Opera, only momentarily. After one or two viewings, it is back to the same old stuff. Clearing cookies did not help for Chromium. 

What is exasperating is that this problem was not there before. Are we moving forward or going backward?

---

### Post by NightwishFan on 2011-03-10
If you disabled them entirely it should stay working. Just clearing them resets after your first viewing and the problem continues. If you did both disable and clear them, then cookies are not the problem.

Edit: To be honest this issue is in the hands of youtube or adobe, the fact it is a problem on more than one browser confirms this.

---

### Post by mmasroorali on 2011-03-10
> **NightwishFan said:**
> If you disabled them entirely it should stay working. Just clearing them resets after your first viewing and the problem continues. If you did both disable and clear them, then cookies are not the problem.

Edit: To be honest this issue is in the hands of youtube or adobe, the fact it is a problem on more than one browser confirms this.

Yes, disabling cookies helped. Thanks.

I agree with you on the point of responsibility. All we can do is to raise our voices.

---

### Post by no2498 on 2011-03-10
reinstall flash player

---

### Post by Paddy Landau on 2011-03-10
I wonder if this is related to Adobe's new bug:
[http://ubuntuforums.org/showthread.php?t=1698956](http://ubuntuforums.org/showthread.php?t=1698956)

Have a look at [post #63]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930") and see whether that solves the problem. If so, it's Adobe's bug; this has been reported and we await a fix.

---

### Post by mmasroorali on 2011-03-10
> **Paddy Landau said:**
> I wonder if this is related to Adobe's new bug:
[http://ubuntuforums.org/showthread.php?t=1698956](http://ubuntuforums.org/showthread.php?t=1698956)

Have a look at [post #63]("http://ubuntuforums.org/showthread.php?p=10520930#post10520930") and see whether that solves the problem. If so, it's Adobe's bug; this has been reported and we await a fix.

The workaround you mentioned regarding unchecking hardware acceleration worked. Thanks. This worked for Opera and Firefox, but not for Chorme. Wonder, why.

---

### Post by Paddy Landau on 2011-03-10
> **mmasroorali said:**
> This worked for Opera and Firefox, but not for Chorme. Wonder, why.
Chrome has its own version of Flash. Check the rest of the thread; I seem to recall someone posted a solution for Chrome.

---

### Post by sandyd on 2011-03-10
a) when it crashes, just use VLC (hint, go to file -> network stream)

---

