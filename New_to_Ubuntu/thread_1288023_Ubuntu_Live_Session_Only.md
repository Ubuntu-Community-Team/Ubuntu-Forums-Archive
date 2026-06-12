---
title: "Ubuntu Live Session Only"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by CJWW1989 on 2009-10-10
I have a question. I ordered my Ubuntu disc and what have you and got it. I tried installing it and it got to about 74% and then gave me some error which said it may be due to a faulty HD. Ubuntu is currently running now, but it has been as a Live Session User and not as my main account I signed up for. Any idea how to get it how it should be? My computer seems to install Windows XP Pro just fine. Any ideas? Thanks.

---

### Post by coffeeaddict22 on 2009-10-10
Hi,
Welcome to Linux!
Linux does have better tools for playing with your hardware at a very close to the metal level, and it's quite possible your HD is getting close to failing or has a bad sector.  Other OS tend to tolerate bad behaviour better (or at least ignore it); I guess you can argue whether that's a good thing or not.
The simple answer is do a check.  make sure your hard drive isn't mounted; the easiest way is by opening a terminal, and if you're in a live session type in ```
fsck
``` and you should be away.  There's an option to fix errors, but it should happen automatically.  That may solve your problem.

If that doesn't find anything, there's a bit of difference between installing off the live CD once you're in Ubuntu and booting up and installing; I've had different options work with different versions, so try both.   

If neither work, you need to get the exact message from the fail; that'll help considerably to track down the issue.

Good luck, and post back if you need more help.

---

