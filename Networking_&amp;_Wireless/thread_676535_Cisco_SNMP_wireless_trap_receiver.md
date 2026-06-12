---
title: "Cisco SNMP wireless trap receiver"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-01-23
Hi, all.  I'm setting up a project for class and I'd like your advice.  I have to set up a Cisco 3500 series switch for SNMP so when any number of items fail it sends a trap (or notification) to a specified address to alert the administrator that there is a problem.  I'd like my trap receiver to also send an email and a text message to my cell to notify me of the trap.  A similar winblows program would be Air Messenger.  Do you have any suggestions?  It's due Feb 4th so help me out asap.  Thanks!

---

### Post by PilotJLR on 2008-01-23
Check out:
- Open NMS
- Nagios
- HP Systems Insight Manager (basic functionality is free).

I use HP SIM at work, and Nagios for a small-office network.

---

### Post by MaindotC on 2008-01-24
Thanks for the quick reply!  I'll try and test them on Friday and let you know how they work out :)

---

### Post by MaindotC on 2008-02-07
Hey Pilot.  Just thought I'd let you know that I didn't get to take the open source angle on this project.  I'm still having trouble using minicom to just connect to the console port and configure so that I can enable SNMP.  *sigh* so anyway, I did it using hyperterm in winblows and I used the trap receiver from bttsoftware.co.uk.  I used Nagios before, just haven't used it for email and sms alerts so hopefully I can revisit that later.  Thanks again for your suggestions.

---

### Post by MaindotC on 2008-02-29
Anyone finding this thread that needs help, please PM me no matter how far past the original post date.  I'd like to get a nice howto but I'm soooo lazy...

---

### Post by jetole on 2008-07-18
Yeah you do sound lazy. Anyways, SNMP traps on nagios are not only simple and efficient but Nagios provides the ability to monitor lots of other services, perform parent and dependency based calculations and can handle e-mail or SMS although I simply combine the two, i.e. My SMS is [email]phone-number@txt.att.net[/email] and I use more for other people in my office. Additionally, to gather traps on most any service on Linux, you need to configure snmptrapd.

See this site for SMS over e-mail for all carriers in the US: [http://en.wikipedia.org/wiki/SMS_gateways#Carrier_Provided_Email_or_Web_to_SMS_gateways](http://en.wikipedia.org/wiki/SMS_gateways#Carrier_Provided_Email_or_Web_to_SMS_gateways)

---

