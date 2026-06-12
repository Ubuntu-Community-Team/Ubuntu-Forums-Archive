---
title: "Can't connect to wireless network"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by clpo13 on 2007-05-05
Okay, I'm having an interesting wireless problem. I'm on a Dell E1505 using a Dell 1390 wireless running 7.04 Feisty Fawn. I know the problems this particular wireless card has been having, but I ran through the tutorials [here]("http://ubuntuforums.org/showthread.php?t=399913") and [here]("https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29") to make sure everything's running. I know the second tutorial was probably redundant, but I wanted to be sure I had all the right drivers installed.

Now, the wireless card is working and it does see my home network. However, when I click on the network to connect, it works for a little while and then goes back to not being connected. What could be the problem? The card is obviously working since it sees the network, but why won't it connect to it? (Note: I can access the internet when I plug in an ethernet cable; the problem is just with the wireless.)

---

### Post by Candace on 2007-05-05
I may have been having the same problem as you are having (my wifi light was on, but no connection when I unplugged the ethernet cable), and what I did is here:

[http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

and now my wireless works like a charm. I haven't encrypted it yet though (that is my next goal). Good luck, I hope this helps you. :)

---

### Post by clpo13 on 2007-05-05
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/bugs/85468](https://launchpad.net/bugs/85468) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I actually fixed it myself after coming across a bug report about a problem like this. I linked it to the post, and I'll post the solution for anyone else who comes across this:

In the terminal, type:

```
sudo iwconfig ethX essid x mode managed
```

replacing ethX with your wireless interface. After I did this, my wireless worked perfectly. Apparently, there's some bug in ndiswrapper that's causing a lot of grief.

---

### Post by Candace on 2007-05-05
Nice going! That seems like a much simpler solution than the one I found.

---

