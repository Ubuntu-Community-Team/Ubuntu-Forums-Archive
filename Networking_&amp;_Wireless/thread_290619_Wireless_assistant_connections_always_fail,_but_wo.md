---
title: "Wireless assistant connections always fail, but work fine"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by kkinder on 2006-11-01
Whenver I use Wireless Assistant, a handy KDE program that now ships with Kubunty Edgy, to configure a wifi connection, as soon as I hit "connect" it says "Connection Failed". It doesn't even seem to wait for the dhcp timeout.

In its output, I see promising things, like it printing out the correct gateway to use.

Then, if I manually run "ifup eth1" on the connection, it works fine, so it's at least properly configuring the ESSID and whatnot.

Has anyone noticed that? Or does anyone have any tips?

---

### Post by Skardal on 2006-11-08
Same problem here.

I hope there will be a solution to this soon!

It's quite annoying to always have to do all the steps...

---

### Post by Paul_M on 2006-11-11
I am having a similar problem, after upgrading to Edgy and running Wireless Assistant to reconfigure my laptop to connect to my wireless network, it will  attempt to connect but fail whereas with Dapper the same tool worked fine and connected my laptop to the wireless network straight away

hope someone has a bug fix for this soon as it is annoying

My card is a Ralink RT2500 based card in case that may help

---

### Post by Skardal on 2006-11-29
I've switched to a new manager. Works great!

Take a look [here]("http://ubuntuforums.org/showthread.php?t=299462&highlight=wireless+manager")

---

### Post by Paul_M on 2006-12-10
seems I can now connect using wireless assistant now without having to go through the terminal, there must have been an update at some point to rectify it which does help me as I do take my laptop some places with me, also good for those long train rides where I can get online too, not having to fiddle about in terminal to get a connection is a relief :)

---

