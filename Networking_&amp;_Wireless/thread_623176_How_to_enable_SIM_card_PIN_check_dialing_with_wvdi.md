---
title: "How to enable SIM card PIN check dialing with wvdial using Huawei e220?"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by LadZh on 2007-11-25
Dear fellow Ubuntunians,

How to enable SIM card PIN check dialing with wvdial using Huawei e220?
Having PIN on the SIM card is kind of protection in case something unvorseen happens...
In short - it's nice to have your SIM card PIN protected. 

I've tried: 

1.          wvdial pin hsdpa                            - where pin is just a word pin written as it is
2.          wvdial "my pin code" hsdpa        -   where "my pin code" is the PIN code I have on my SIM card
3.          adding
                                  a.            [Dialer pin]
                                                 SIM PIN = "my pin code"

                                  b.            [Dialer "my pin code"]
                                                 SIM PIN = "my pin code"      

                                  c.            [Dialer pin]
                                                 PIN = "my pin code"

                                  d.            [Dialer "my pin code"]
                                                 PIN = "my pin code"      

                into my   wvdial.conf

all without success. 

What do I do wrong?

Did anybody do it already?

---

