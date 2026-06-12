---
title: "Dial up connection PAP flaky"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by Peter Ker on 2007-08-02
I have an LT modem. Can dial-in (through the terminal) , Get to the point oif ID and password accepted. 

After starting pppd I get a warning c"could not modify /etc/pop/pap-secrets. Permission denied. PAP may be flaky. same message for CHAP..

After that I have a lot of pppd messages with numbers. But cannot connect to Evolution or Firefox.

There is a comment: cannot set information on serial port.  Furthermore the Local IP address, remote IP address, primary IP address, secondary IP address none are the same as my real IP provider's primary address is:206.235.86.11, and secondary address is 206.235.86.12

Hope someone can understand it and help me. I am new to Linux and Ubuntu, but like to learn it.

Peter

see attachment for  WVDIAL  dialog

---

### Post by Bartender on 2007-08-04
Dial-up can be very confusing until you are pretty comfortable with doing things in Linux.  Unfortunately, most of us trying to get dial-up working are new to Linux.
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=480717") and see if the directions for getting the pap and chap flaky messages to go away don't work for you.
Another thing - I'm not good at reading dialer logs, but when it says "Starting PPP immediately" that tells me that stupid mode is "on".  
Try turning stupid mode "off" and see what you get in the log. 
It appears that you were connected for 3 minutes then disconnected.  I'm not sure what that means exactly - whether you were actually connected to your ISP and they kicked you off or what -  but have seen similar messages when stupid mode was on.
I also noticed you're dialing a number with the area code.  Is that what you meant to do?  Your ISP is a long distance call for you?

---

