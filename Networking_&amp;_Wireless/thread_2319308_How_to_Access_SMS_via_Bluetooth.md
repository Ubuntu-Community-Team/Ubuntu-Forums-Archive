---
title: "How to Access SMS via Bluetooth"
date: 2016-04-02
forum: Networking &amp; Wireless
---

### Post by ctrl-alt-del2 on 2016-04-02
Hello. New here, but was stuck on a problem and probably doing a lot wrong. I have an LG running android 4.1+ and was trying to access the SMS via bluetooth. 

I made sure to create a node by executing:
mknod -m 666 /dev/rfcomm0 c 216 0

paired with the phone
bluez-simple-agent hci0 <bluetooth addr>

bound the node to the phone's sms channel
rfcomm connect 0 <bluetooth addr> <sms profile channel>

I get two prompts on the phone, one to pair, then another to share sms with the computer

I am now stuck, because I was trying to use minicom on rfcomm0, it seems to open, but nothing there. I'm realizing that it probably will only work with DUN profile. I see python scripts in other forums, but I am not sure if they would work. Does anybody have experience in this?

---

### Post by QIII on 2016-04-02
It would probably be very helpful if you would let us know which release of Ubuntu you are using and give us the hardware specs of your computer.

---

### Post by ctrl-alt-del2 on 2016-04-02
yes, Ubuntu 14.04LTS running on a Acer Aspire E15 ([http://www.laptopmag.com/reviews/laptops/acer-aspire-e15-touch](http://www.laptopmag.com/reviews/laptops/acer-aspire-e15-touch))

I have read some places that this can be done via scripting, but not sure.

---

