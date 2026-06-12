---
title: "Ubuntu + SmartLink modem = me going mad"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by haora on 2005-12-06
Ok, so this is the story....

I've installed Ubuntu 5.10 and I want to know if I can use my winmodem..., I allready run the "scanModem" app, and it says I have a "SmartLink" modem..., I downloaded all the files I need and installed them...(I think...)..

Now, when I run "wvdial" I get a "No DIAL TONE" message ...

How can I fix this???

Any suggestions???

Thanks in advance!!!

---

### Post by teaker1s on 2005-12-06
not specific but if it's non broadband make sure any message services are not altering dial tone to indicate a message
eg uk 1571 shortens and increases dial tone and modems can't see it

---

### Post by haora on 2005-12-06
> 
not specific but if it's non broadband make sure any message services are not altering dial tone to indicate a message
eg uk 1571 shortens and increases dial tone and modems can't see it

MMmmhhh..., I'm not sure what "uk 1571" is, but I don't think anything is altering the dial tone...,  and even if there was, I don't know how to check for that..., any other ideas???

---

### Post by towsonu2003 on 2005-12-06
[QUOTE=haora]Ok, so this is the story....

I've installed Ubuntu 5.10 and I want to know if I can use my winmodem..., I allready run the "scanModem" app, and it says I have a "SmartLink" modem..., I downloaded all the files I need and installed them...(I think...)..

Now, when I run "wvdial" I get a "No DIAL TONE" message ...

How can I fix this???

Any suggestions???
[/QUOTE]
a few suggestions: 
what exactly did you do to configure modem? 
can you see the modem in system>administration>network(ing?)?
did you configure wvdial first? (sudo wvdialconf /etc/wvdial.conf -and after that, open /etc/wvdial.conf and put in your ISP info etc where provided-)
are you running wvdial with 'sudo wvdial'? (answer should be: yes)
when configuring wvdial, did wvdial tell you that it actually saw the modem (best way to know modem is configured)? 

and a frustrating suggestion: make sure the phone line is connected to the modem & there's dial tone ok.

and a final one: is it working under windows (if dual booting, without physically moving anything -computer, stuff attached to it, phone etc-, reboot to windows and try dialing --- I once found my phone line (the cable going from phone jack to the the modem) was faulty) ?

---

### Post by haora on 2005-12-06
> what exactly did you do to configure modem?
I installed the .debs I don't remember the names right now...

> can you see the modem in system>administration>network(ing?)?
Yeap, but it says it's not active (I think..., I'm not in home right now)


> did you configure wvdial first? (sudo wvdialconf /etc/wvdial.conf -and after that, open /etc/wvdial.conf and put in your ISP info etc where provided-)
Yeap, wvdialconf ..., it recongnized the modem and added the proper commands to the wvdia.conf

> are you running wvdial with 'sudo wvdial'? (answer should be: yes)[quote]
yes

[quote]when configuring wvdial, did wvdial tell you that it actually saw the modem (best way to know modem is configured)?[quote]
Yeap

[quote]and a frustrating suggestion: make sure the phone line is connected to the modem & there's dial tone ok.
Yeah, the first thing I checked, but still, the modem does work in Windows..., so that wasn't going to be the problem..., I'm dual booting with the same machine.... so

Anything else??? :confused:

---

### Post by mips on 2005-12-06
One more idea. I have noticed that not all modems know what region they are in anf they dont recognise the dial-tone and just responds with a 'no dial-tone' error. If theit is a setting to disable 'wait for dial-tone' then select it and see what happens.

---

### Post by towsonu2003 on 2005-12-06
you could also try asking this to the mailing list at [http://linmodems.org/](http://linmodems.org/) (very helpful people)

---

### Post by haora on 2005-12-06
[QUOTE=mips]One more idea. I have noticed that not all modems know what region they are in anf they dont recognise the dial-tone and just responds with a 'no dial-tone' error. If theit is a setting to disable 'wait for dial-tone' then select it and see what happens.[/QUOTE]
I'm looking at the man page for "wvdial.conf" and I don't see anything like that..., but maybe I should check the location at the "sl-modem-deamon" (I think that's the name...) configuration file...

And "towsonu2003", I'll try the that mailing list too, thanks for the advice...

Anyone else has any ideas???

Thanks!!!

---

### Post by squidward2006 on 2005-12-12
Jeffry Dahlmer confessed to local authorities that he had spent the 6 months preceeding the infamous killings trying to configure his SmartLink modem to make a connection from Ubuntu....Well, maybe not really, but I can certainly see how that might have been a prominent factor.
I have spent the last two weeks trying to establish a connection with my SmartLink modem first under RedHat 8.0 then under a current Ububtu distro, all to no avail. If anyone has managed to make this work please let me know
(the voices arent providing any usefull advice, lol)

---

### Post by jml on 2005-12-12
quote:   "can you see the modem in system>administration>network(ing?)?
Yeap, but it says it's not active (I think..., I'm not in home right now)"

just one more question, the fact that you can see the modem listed in the networking application means that you must have successfully loaded the appropriate drivers.  You also note that it lists the modem as being not active.  Have you tried to activate the connection yet?  Its not at all intuitive, but getting any network hardware working is a two step process.  First install hardware and drivers, then configure the device.

Once you go to:  System--> Administration--> Network, highlight the modem, then click on the properties and fill in any appropriate blanks, click  on ok.  Make sure that the modem is still highlighted and then click on the activate button.  It may take several minutes to complete, but eventually you should see a message that the device hase been activated.  Click ok to close all boxes and hopefully you will have a fully functioning modem.

Joe

---

### Post by funkydan2 on 2005-12-12
[QUOTE=haora]but maybe I should check the location at the "sl-modem-deamon" (I think that's the name...) configuration file...[/QUOTE]

You can set the "country" that you're in in the sl-modem-daemon config file.  It's /etc/defaults/sl-modem-daemon (or something very similar).  Also, running "sudo dpkg-reconfigure sl-modem-daemon" gives you an ncursors dialog to set the country code a few other sl details.

(not that my modem works either, but hopefully this points you in the right direction.)

---

### Post by haora on 2005-12-15
[QUOTE=funkydan2]You can set the "country" that you're in in the sl-modem-daemon config file.  It's /etc/defaults/sl-modem-daemon (or something very similar).  Also, running "sudo dpkg-reconfigure sl-modem-daemon" gives you an ncursors dialog to set the country code a few other sl details.

(not that my modem works either, but hopefully this points you in the right direction.)[/QUOTE]
Nop it didn't but I'll try what Joe said and I'll let you know....

---

