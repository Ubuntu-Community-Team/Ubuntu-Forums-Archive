---
title: "Can't disconnect pppd properly."
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by Andrew Utnubu on 2008-07-15
Hi! I'm working on a program module, that connects/disconnects etc. via Siemens MC35i GPRS Modem.
The problem is, that my disconnect chat looks not that pretty for pppd to close the connection properly. It didn't bother me much (sudo killall -9 pppd), until this moment, when i have to add some more functionality, like getting signal strenght (AT+CSQ).

After terminating connection this way, i simply:
 cat /dev/ttyUSB0
 echo AT+CSQ > /dev/ttyUSB0
and it seems like there's some kind of sh!t in his (MC35) brain after that termination, so he can't think as fast as it was before. So after few seconds, MC responses with an error.
If i repeat the operation (AT+CSQ) after few minutes, sometimes i get lucky and MC tells me the truth about signal strength or what ever.

Here's what i'm getting in terminal when i'm trying to disconnect:

lowcut@lowcut-laptop:~$ sudo pppd disconnect gprs-disconnect-chat
Password:
~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } }#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~lowcut@lowcut-laptop:~$

Btw, only now, when i pasted this in forum window, i get the picture of repeated message (}#}$&#65533;'}%}&D<&#65533;&#65533;}'}"}(}"&#65533;*~~&#65533;}#&#65533;!}!}!} }8}"}&} } } } ), but still i don't know what is this supposed to mean. 

So here's a disconnect chat:
> 
#
# chatscript to tidy up a GPRS phone when we are done with it.
#
# $Id: gprs-disconnect-chat,v 1.2 2001/12/17 17:29:27 tjd21 Exp $

# Boilerplate
#
	ABORT		BUSY
	ABORT		ERROR
	ABORT		'NO DIALTONE'
	TIMEOUT		30

# Get some attention
	''		'+++\c'
	SAY		" + sending break" 

# Hang up data connection
#
	''		'ATH'
	SAY		"\n + dropping data connection"

# Disconnect from GPRS
	OK		'AT+CGATT=0'
	SAY		"\n + disconnecting from GPRS"
	OK		'\c'
	SAY		"\n + disconnected."

#
# chatscript to tidy up a GPRS phone when we are done with it.
#
# $Id: gprs-disconnect-chat,v 1.2 2001/12/17 17:29:27 tjd21 Exp $

# Boilerplate
#
	ABORT		BUSY
	ABORT		ERROR
	ABORT		'NO DIALTONE'
	TIMEOUT		30

# Get some attention
	''		'+++\c'
	SAY		" + sending break" 

# Hang up data connection
#
	''		'ATH'
	SAY		"\n + dropping data connection"

# Disconnect from GPRS
	OK		'AT+CGATT=0'
	SAY		"\n + disconnecting from GPRS"
	OK		'\c'
	SAY		"\n + disconnected."



I think the problem is not in the script, but somewhere in property files.    

Can anyone help me with that?

Thx in advance.

---

### Post by Andrew Utnubu on 2008-07-16
No ideas? At all? =(

---

