---
title: "voipdiscount and linphone"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by 29732 on 2010-07-30
how do i set linphone up on voipdiscount's settings??

---

### Post by 29732 on 2010-07-30
AGH....
i clicked solved instead of subscribe ](*,)](*,)](*,)](*,)

---

### Post by gorski on 2010-10-12
```
http://www.voipdiscount.com/en/sipp.html
```

> Software configuration

General
    SIP port : 5060
    Registrar : sip.voipdiscount.com
    Proxy server : sip.voipdiscount.com
    Outbound proxy server : leave empty
    Account name : your VoipDiscount username
    Password : your VoipDiscount password
    Display name/number : your VoipDiscount username or voipnumber
    Stunserver (option) : stun.voipdiscount.com

In Win now, so gonna test tomorrow...
[SIZE=4][B]
[SIZE=3]Here are the Poivy settings:[/SIZE][/B][/SIZE]
> [B]Software configuration
General 
SIP port : 5060   
Registrar : sip.poivy.com
Proxy server : sip.poivy.com
Outbound proxy server : leave empty
Account name : your PoivY username
Password : your PoivY password
Display name/number : your PoivY username or voipnumber
Stunserver (option) : stun.poivy.com[/B]


---

### Post by stephan2503 on 2010-10-21
Hey, 
have the same problem: absolute newbie to sip and want to use voipdiscount with linphone. didn't find any usable docs yet.

thanks
stephan

---

### Post by mr_hangman on 2010-12-01
This setting seems to work for me.

Go to Linphone > Preferences > Manage SIP Accounts > Proxy accounts > Add

Your SIP identity: sip:*username*@sip.voipdiscount.com
SIP Proxy address: sip:sip.voipdiscount.com
and check 'Register at startup'

Leave other options as default.

If you're behind a NAT you may want to try adding
stun.voipdiscount.com
in
Linphone > Preferences > Network settings > NAT and Firewall > Behind NAT / Firewall (use stun to resolve)

However, it still fails to connect sometimes and I can't figure out why.

---

### Post by gorski on 2010-12-15
Thanx!

Interesting how Fring in my HTC smartphone works simply and easily...

Only 3 parameters and it all functions really well...

They should all sit up, listen and learn...

It's also Linux...

SIP option.

;)

---

### Post by heliboy on 2010-12-22
Not a voipdiscount-specific comment, but hopefully not too far afield:
 
Seems like linphone actually does not support STUN (at least that's what is stated on the developers' maillist at [www.linphone.org]("http://www.linphone.org")).  If that's the case, I don't know why the option to use STUN would be offered in linphone's Preferences, but so be it.  If I do the voice echo test at ekiga (sip:[EMAIL="500@ekiga.net"]500@ekiga.net[/EMAIL]) with a STUN server specified in Preferences, a conection is established, the voice introduction from Ekiga is audible, but my voice is not returned.  If the IP address of the WAN side of my router is entered in Preferences, the ekiga voice test works normally.  Similarly, calling 800 numbers through ekiga does not work with the STUN option set but does work with the WAN IP address option set.  This would seem to be a serious limitation of linphone for those who might need to use it while traveling, but I don't know enough about this yet to be sure.  Or maybe this is a problem at ekiga.  Any suggestions or similar experiences?

---

### Post by mjabirk on 2012-02-17
Thank you.

---

### Post by overdrank on 2012-02-17
Back to sleep thread. Thread closed

---

