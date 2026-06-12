---
title: "Another one struggling with ndiswrapper ..."
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by AdrianB on 2006-12-14
I have a NetGear WG111 v2 USB wireless adapter, but not alas the one that  Ubuntu 6.10 recognises automatically.

I have followed the SourceForge instructions without success, then re-installed Ubuntu and tried the instructions in the Community Ubuntu Documentation.  

This command worked for me:
   "ndiswrapper -i [path]/netwg111.inf"
I checked it with "ndiswrapper -l" and it confirmed that the driver was installed in ndiswrapper. So far so good.

The command "modprobe ndiswrapper" produced an error, which was captured in /var/log/syslog. Here are the relevant lines of the log:

Dec 14 21:04:12 Galadrix kernel: [17182027.752000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Dec 14 21:04:12 Galadrix loadndisdriver: loadndisdriver: main(638): version 1.7 doesn't match driver version 1.8 
Dec 14 21:04:12 Galadrix kernel: [17182027.756000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
Dec 14 21:04:12 Galadrix kernel: [17182027.756000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed

[The smiley in the error message is an artefact of the forum software. The number should read 638 in parentheses, for what that's worth.]

I know what version 1.8 is - it refers to ndiswrapper-utils version 1.8_0ubuntu2. To what does version 1.7 refer? I'm flummoxed. ](*,) 

Informed comment in simple language will be very much appreciated.

---

### Post by padre999 on 2006-12-14
Maybe this helps: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

Says someting about Ndis 1.8. 

I guess in the error message it says "you installed 1.7, but I need 1.8":roll:

---

### Post by AdrianB on 2006-12-15
Thank you padre999. I've bookmarked that site for future reference, and I'll work through it when I have time. In the meantime, if anyone can explain the 1.7 / 1.8 message that I pasted into my original posting, then please do.

---

