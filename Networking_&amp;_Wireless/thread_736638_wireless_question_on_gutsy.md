---
title: "wireless question on gutsy"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by kaboom on 2008-03-26
Im trying to connect to a home network on gutsy.  The wireless adapter is a linksys compact wireless-g usb adapter and the machine is a compac evo N620c 

My system seems to be picking up my wireless adapter, when i enter in the terminal 
$ sudo iwlist scanning
it shows all of my network information under wlan0

when i put the info in (its ascII) network manager nothing happens and still no internet connection.  i've done it via terminal on feisty but those commands dont seem to be exactly right in gutsy.   

could someone tell me what i'm doing wrong in network manager;  or just give me a quick list of code to do it in the terminal.

thanks for looking

also- when i was searching on this topic i saw a lot of mention of ndiswrapper.  would that be relevant even though my system already finds the network in with the scanning command?

---

### Post by which_chick on 2008-03-26
If your wireless is showing up in iwlist, you're probably OK as far as drivers.  Ndiswrapper is a tool that lets you use Windows drivers on your linux system -- it's for when there isn't any linux driver or the one available doesn't work with your hardware.  I'd wait on that to see if we can get things running without it first.

For command-line instructions to set up wireless, there's an excellent and usually-successful set of directions here:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

