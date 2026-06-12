---
title: "Ethernet Connection Issue"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by what-is-a-computer? on 2011-02-26
I have a wired ethernet connection, "auto eth6."  It's plugged into a router, and right now it is set on "Automatic (DHCP).  I want to set the "method" to "manual" under the IPv4 Settings under Sys/Pref/Network Connections.  I want a static IP address.  

The green checkmark is grayed out and I cannot change it.  Why?  Help, please.

Thank you.

---

### Post by seawolf167 on 2011-02-26
See if there is an "unlock" button or image of a key in that window (usually in the lower-right). You'll need to click that and enter your password before you can change those settings.

Just in case you want to do it via command line/config file editing, [here]("http://www.jonathanmoeller.com/screed/?p=1669") is a how-to link for that.

---

### Post by what-is-a-computer? on 2011-02-26
thank you so much.   I'll try that on Monday at work.

---

### Post by what-is-a-computer? on 2011-02-28
No, there is no unlock button. 

It makes me put the password in when I attempt to change the VPN connections.  Once I put in a password, then I can edit the auto eth6.  Then I click on pciv (something or other) and I go go "manual."

It is there, the green checkmark, until I change the DHCP (or whatever those letters are) to "manual."  I put in the address and the netmask.  the checkmark will not go to green.  It's grayed out.    So I cannot apply the change.

Any ideas?

---

### Post by seawolf167 on 2011-02-28
See if you can do it manually by editing the config files per the link I posted above. Its pretty easy, you just enter the info in the file then save & restart networking

---

### Post by what-is-a-computer? on 2011-02-28
This has been resolved.  The only reason I'm going to own up to my error and post this is because there may be someone out there as clueless as I am (probably not) with computers who's in the same boat I'm in:  A sinking vessel.

When I went to the IPv4 settings and clicked on "manual," I then clicked on the first square which is "address."  I filled in the static IP address.  I then clicked on the word "netmask" and then "add."  It opened up a square underneath the first address and that's where I typed in "255.255.255.0."

I finally figured out it went to the side, not underneath; that you just click to the right of the address you just filled in.  Do not click on the word "netmask."  It's in the empty space to the right.    Once I put the "255" to the right side of the address,  it filled in the gateway automatically and then up popped the green checkmark so that I could apply it.

Thank you for trying to help me, seawolf.    I'm a lost cause.  I usually figure it out, though, by just pushing buttons and trying and trying.  Not a good place to be.  

Now you know why I'm "what-is-a-computer?"

---

