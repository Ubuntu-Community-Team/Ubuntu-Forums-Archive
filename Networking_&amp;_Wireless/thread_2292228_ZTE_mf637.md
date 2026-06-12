---
title: "ZTE mf637"
date: 2015-08-26
forum: Networking &amp; Wireless
---

### Post by john448 on 2015-08-26
Hi,
newbie on the forum and dealing with usb-serial things, I tried to unsimlock a ZTE MF637.
I use cutecom with /dev/ttyUSB2 to deal with the dongle and I do get answers from it.
I just don't find anyway to send the nck to the dongle.
Other websites said ```
AT+ZNCK="nck-code"
``` but I get "ERROR" and then I cannot get good result from standard command 
If I use ```
AT+CLCK="PN",0,"nck-code"
``` it gives a known error (41 which is "CME ERROR: 41   Network personalization PUK required"  )


 ```
plugged in then I did a ATE1 after the first error that poped up
ERROR

 

 OK
 

 +CPMS: "ME",0,100,"ME",0,100,"ME",0,100
 

 OK
 AT+GCAP
 

 +GCAP: +CGSM,+FCLASS,+DS
 

 OK
 AT+GCAP
 

 +GCAP: +CGSM,+FCLASS,+DS
 

 OK
 AT+GCAP
 +GCAP: +CGSM,+FCLASS,+DS
 

 OK
 AT+CPIN?
 

 +CPIN: READY
 

 OK
 AT+CLCK="PN",2
 

 +CLCK: 0
 

 OK
 AT+CLCK="PN",2
 

 +CLCK: 0
 

 OK
 AT+ZNCK?
 

 +ZNCK: 5
 

 OK
 AT+ZNCK="12345678"
 

 ERROR
 AT+ZNCK=123456789012
 

 ERROR
 AT+CLCK="PN",0,"12345678"
 

 +CME ERROR: 41
 AT+ZNCK?
 

 ERROR
  AT+CPIN?

 

 +CPIN: PH-NET PUK
 

 OK

```



Any lead would be welcome!
thanks in advance

---

