---
title: "Wireless internet on ubuntu 7.04"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by xvedejas on 2007-08-16
Hello, I am running Ubuntu 7.04 64-bit, but cannot connect to the internet. Ubuntu recognizes my wireless card and sees my wireless network, but when attempting to connect to the network it fails.

My wireless card is a Linksys model number WMP54G.

Thanks for the help.

---

### Post by xvedejas on 2007-08-16
Help anyone? Sorry for the double post, but it seems nobody has seen this.

---

### Post by Desiree on 2007-08-20
I'm having the same problem.  Was given the option of 3 WEPs (different options than I have with my connection on windows) and to put in the password, but neither worked.  Very new to Ubuntu.  I can see the signal there, just can't connect to it and there doesn't seem to be much pointing me to help or other options that I may be missing.  

Any words of advice out there?  Should we be looking elsewhere for this information?  New to the Forums also.

Thanks.

:)

Update:
As embarassing as it is, I was using a network key that included a couple typos!  I was told that's what the tech services rep read out as being the number, but when I double checked I found a couple mistakes.  I'm now up and running.  So far, Ubuntu is looking very promising!

---

### Post by bmartin on 2007-08-20
What is the output of **sudo iwlist scanning**?

---

### Post by netron on 2007-08-20
i get the same thing - but with a realtek rtl-8185 chipset ( Gateway laptop)
network manager can see my neighbours networks and mine.  but trying to connect using a WEP hex key doesnt work.

scanning with iwlist gives me "No scan results"

---

### Post by bmartin on 2007-08-20
**sudo iwlist scanning** should return some results if your network manager is detecting them (if you omit sudo, all bets are off). Try using the [wicd]("http://blakecmartin.googlepages.com/wicd.html") program to connect; it fixes the problem for a lot of people who can't otherwise get a connection.

---

### Post by netron on 2007-08-20
weirdest thing ever - i just rebooted and i'm now on the network.  (after trying everything all night)

must be a bug in network manager. maybe it managed to click on the right sequence of things to get darn thing going.

---

### Post by beachreader on 2007-08-20
fiesty wireless connection is unpredictable. setting up the connection with the ubuntu menu is hit and miss....wep number, network password, open key, shared key.  what nonesense not one of these phases is defined anywhere. and once you figure out the codes you have to try  getting the connection several times then bring up windows xp hard drive make sure there is a connection and your not going crazy. who ever design the wireless connection menu did a poor job ....it took me over an hour to get it to work . Then I went out of town and the hotel wireline would not work with ubuntu but it work right away with windows. never had this problem with ubuntu 6.06....if not broke why try fix it... is there a clear step by step process because the quickie in ubuntu documents does not work . it's all fantasy...

---

