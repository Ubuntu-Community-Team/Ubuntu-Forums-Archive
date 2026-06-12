---
title: "new to Ubuntu, having trouble connecting to wireless"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by gwyn15 on 2009-07-23
Hi there. I just bought a new laptop after my 7 year old mac crapped out on me. Having not enough funds to replace it with another Mac, I bought an EEEPC .... and was under the impression that they came pre-installed with linux. I don't know if I bought the wrong model or not, but it came with XP on it, and I really just hate microsoft. I had a look for prospective operating systems, and came up with Wubi ... a version of Ubuntu which runs dually with the system already installed. Now the night I bought it, I was on the internet through XP and had no problems connecting to the network via my new computer, but I can't figure out how to activate the connection between my newly installed Wubi and my wireless router.
Although i'm not a techi, I do know a bit about computers, and spent quite a bit of time on forums trying to figure out what to do... and I have given up a little bit. Here's what tests I have done so far:

code: iwconfig
results:
 lo no wireless extensions.

etho no wireless extensions.

pano no wireless extensions.

not sure what that means... does it just mean that i'm not connected, or is it trying to tell me that it doesn't register my router at all?
Could this be a driver issue?

under the network icon between battery and sound, the option "wired network" is not selected. I can select VPN Connections, and then Configure VPN. When I do this, it brings up several options, all with the possibility of "adding" them 
wired
wireless
mobile broadband
VPN
 and DSL

If I click on these, it takes me through a series of questions determining my service provider, and the name I want to call it. Don't think this is what I want.

If I go under System, administrator, network tools
there are two things under IP information
IPv4 - 127.0.0.1    2550.0.0
and
IPv6 ::1    128     

I can hilight these, but cannot seem to select them.

I have also tried a few commands in the "terminal" ... but don't know what the answers mean.

Any help would be appriciated, seeing as I'm going to have to go through all this again in the fall when I go to get wireless at my university. And I know that nobody there will know how to set it up for me.

Thanks again
Gwyn15

---

### Post by shifty_powers on 2009-07-23
you would be much better checking out eeebuntu (google it).

it is ubuntu repackaged for the eee machines.

---

### Post by c0mput3r_n3rD on 2009-07-23
You need to install the driver for the wireless.  This could be done by installing the Windows Wireless Drivers program from add/remove and then installing the .inf file of the driver.  Other than that you can ndiswrapper (which you can find many tuorials on).

Hope that helps.

---

### Post by gwyn15 on 2009-07-23
Thanks for the advice. I have uninstalled Wubi, and am currently installing EEEbuntu.
Should work great.
(seems better for me, the description was "set up out of the box" which means no configuring/fiddling/other messing about with things I don't understand.)
I'll let you know how it goes.

---

