---
title: "Mobile Broadband disconnects - using GMail"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by kylea on 2011-04-14
I have an issue when using Gmail and I attached files over a certain size, The upload will commence and then go approx 30% thru and then it stalls. My Mobile Broadband disconnects although all the lights are still on so it looks like its still connected. 

I have to physically remove the USB Dongle and wait a short time, then re-insert and then wait and then reconnect.

The Mobile Broadband Modem is a Sierra Wireless connected to 'Telstra Telstra (Next G) 1'

I have attached a snippet from the syslog showing the successful connection.

I'll now force the errors and capture the log entries

OS is Ubuntu 10.04 64Bit

2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

---

### Post by phd7 on 2011-04-14
same here. I was going to post the same question. I have a sierra 302 wireless dongle. I was highly impressed when I plugged it in first and a little box popped up asking simply for my pin. No other crap whatsoever.Unfortunately the network drops after about 40-60 mins which is a pain in the *** if I am in the middle of uploading something or playing a game and the PIN box pops up again. Is there any setting I can change in order to stay connected?

This problem does not occur on Windows , by the way.

---

### Post by gandaran on 2011-04-14
check which DNS the connection is using, your internet provider DNS or some other.

---

### Post by kylea on 2011-04-14
> **gandaran said:**
> check which DNS the connection is using, your internet provider DNS or some other.

Why, could the DNS provider have same sort of upload limit?

Also I do not get prompted to enter the PIN Again - it just stops responding

More Information, I can drop huge files into DropBox and nothing goes wrong. It only seems to happen when I am using GMail to send a large file

---

### Post by Mark Phelps on 2011-04-15
Don't mean to be discouraging, but I recently signed up for Verizon Mobile Broadband and find that disconnects are quite frequent. In my case, while web surfing, I suddenly get an error indicating that a site can not be found.

This usually means I've lost the DNS server, but when I check this, I can still PING it.

My solution as been to pull out the USB-attached modem, wait 30 seconds, and reinsert it.  After a minute or two, the flashing light on the modem changes to green and Internet access is back.

Sorry, but I've been round and round with Verizon on this, and this appears to be typical of Mobile Broadband service -- it's generally unreliable and subject to disconnects.  And, to make matters worse, I'm using 4G service -- and that's supposed to be better than 3G.

---

### Post by phd7 on 2011-04-15
As I mentioned, this doesnt happen in Windows for me. 
It would not be a DNS issue as it is not a case of a site being looked up but a total network disconnection, normally while uploading a file of even listening to a radio station online, in the background, while doing something else.

For me, the box for the PIN pops up requesting the PIN be reentered, but it connects again automatically anyway, possibly because I have entered the PIN in the edit connections/mobile broadband box.

This isnt much use though when an upload is interrupted and cancelled.

Is there a config file somewhere I could check?

Before using this dongle I used my phone as a modem (tethered) and got an uninterrupted broadband connection.

---

### Post by kylea on 2011-04-15
There is no way its a DNS issue - my business partner sitting next to me uses Windows 7 and the exact same modem to Telstra - we bought the two modems at the same time - and he has no issues at all.

Its some kind of buffer overflow - and it seems to only affect GMAIL file attachments, not Dropbox etc.

I'll try it on the PC zI am using now - its not my normal machine - this is my 11.04 test box.

---

### Post by gandaran on 2011-04-16
> **kylea said:**
> There is no way its a DNS issue - my business partner sitting next to me uses Windows 7 and the exact same modem to Telstra - we bought the two modems at the same time - and he has no issues at all.

Its some kind of buffer overflow - and it seems to only affect GMAIL file attachments, not Dropbox etc.

I'll try it on the PC zI am using now - its not my normal machine - this is my 11.04 test box.
it can be a DNS issue especially in ubuntu 10.04, in 10.04 mobile broadband doesn't always fetch the internet provider DNS with some 3g modems but instead uses a system assigned one like 4.4.4.2 which doesn't always work well, check in network manager which one is in use.

---

### Post by kylea on 2011-04-16
> **gandaran said:**
> it can be a DNS issue especially in ubuntu 10.04, in 10.04 mobile broadband doesn't always fetch the internet provider DNS with some 3g modems but instead uses a system assigned one like 4.4.4.2 which doesn't always work well, check in network manager which one is in use.

Ok so maybe a DNS issue with 10.04 - *but not with the actual DNS provider* - will check that - as my tests in 11.04 are ok

---

### Post by kylea on 2011-04-16
> **kylea said:**
> Ok so maybe a DNS issue with 10.04 - *but not with the actual DNS provider* - will check that - as my tests in 11.04 are ok

I tested 10.04 (I am at home) - and it worked ok with a 4mb file)

I'll leave the Wireless Broadband running exclusive for a few hours and see it it loses it. As this is the usual pattern at work.

---

### Post by kylea on 2011-04-16
> **kylea said:**
> I tested 10.04 (I am at home) - and it worked ok with a 4mb file)

I'll leave the Wireless Broadband running exclusive for a few hours and see it it loses it. As this is the usual pattern at work.

Ok - it just happened - tried to load a 750KB file and it stalled

---

