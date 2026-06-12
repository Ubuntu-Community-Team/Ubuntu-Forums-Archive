---
title: "Edubuntu thin client network lock up"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by GeorgeBarkley on 2007-03-26
I'm kind of a newbie computer administrator at an International School. We are using and dual processor AMD 64 server with 6 GB of memory running Edubuntu Edgy to around 60 thin clients. We started out with Dapper, but usb and sound were important to have on the thin clients, so I updated to Edgy basically following the tutorial at [http://developer.novell.com/wiki/ind...eKow_on_Ubuntu](http://developer.novell.com/wiki/ind...eKow_on_Ubuntu)
Most of the time the thin clients boot up and sound and usb sticks work fine. But quite regularly the system just locks up. Nothing new can boot up and sometimes the thin clients that are on lock up as well (sometimes not). Sometimes it happens when someone is logging out and the log out gets stuck half way with just the twirling icon. Other times it seems we lock up when the intenet connection to our school goes down.

What's really nasty is that if I go to the server and happen to be logged in, I can't sudo anything. I can't run the Student Control panel, or anything else that requires root privileges. I can't even log out of the server or shut it down. I have to push the reset button on the server to get it to restart.

Even after restarting the server, it still doesn't work at times unless I turn the power off to the whole building so as to make sure all the thin clients have been shut down. (not something I like to do). That usually works, but it didn't once, so I thought it might be a conflict with someones windows laptop on the network. I did find one with an IP address a bit off, but even after correcting that, I still get the problem.

It seems to occur quite regularly at certain transitional times in the day (early in the morning when people are just arriving, when classes are changing, and of course in the middle of my computer class.

For a while we though it might be hardware conflicts with some of the old junker boxes we have hooked up as thin clients, because it seemed like a few of them never did boot up all the way and crashes tended to occur at the same time we tried booting them up. But we removed all of them that seemed to cause that problem, and we've turned every box on one at a time without crashing the system. So now we are back to square one.

Usually when this happens, after reboot when I log on the server as administrator, the log in takes a very long time.

I'm sure I need to give some more technical info...but don't know where to start with that. So I'll just post this and see if anyone can point me to the next thing to look at.

Needless to say, this has been going on for about three weeks and we are all getting very tired of it (especially now at report card time).

Thanks for any suggestions.
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
GeorgeBarkley
View Public Profile
Send a private message to GeorgeBarkley
Find all posts by GeorgeBarkley
Add GeorgeBarkley to Your Buddy List
Post Reply

---

