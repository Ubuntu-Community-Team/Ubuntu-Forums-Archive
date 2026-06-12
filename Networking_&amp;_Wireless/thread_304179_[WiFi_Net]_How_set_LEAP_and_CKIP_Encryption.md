---
title: "[WiFi Net] How set LEAP and CKIP Encryption"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by lukesky on 2006-11-21
I've a Notebook with Intel Centrino and 2200BG card.
Under Windows I have to download the Intel ProSet software to access on my university Wifi Net.

I must set LEAP protocol and CKIP encryption (Cisco TKIP) with IEEE 802.1x authentication.

Now I want set the accesso to this net under Ubuntu, how can I do?

I try with Network-Manager and WPA Supplicant but don't work.

Can you help me?

Thanks.

PS: I annex a picture with my network setting under windows.

---

### Post by lukesky on 2006-11-22
up

---

### Post by wieman01 on 2006-11-23
Please try this thread & give your feedback.

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

LEAP is described in there, but is untested. TKIP (WEP) encryption and IEEE 802.1x authentication.

---

### Post by lukesky on 2006-11-25
I will try but I don't think that work because the encryption is CKIP (from Cisco System) and is different from TKIP.

With TKIP under Windows don't work......

---

### Post by cnlohfin3109 on 2006-12-21
i have the same setup, honestly ive only had success with xsupplicant on ubuntu 5.04...  wpasupplicant never works and the newer version of xsupplicant crashes on me

---

### Post by pedor on 2007-03-27
I wonder the same !

any solution?

---

### Post by lukesky on 2007-05-07
there is anyone that have solved the problem????

Is possbile with the new Feisty Network Manager configure a connection with CKIP???

---

### Post by triwave on 2008-05-21
Yes, I have same issue. For all the combinations I have tried it does not seem to work. I am 95% sure I have a valid interfaces file and commands but I just keep timing out without a DHCP offer from the bs.  At this point I'm also assuming the problem is TKIP is being used and I really need CKIP which must be different in some ways.

BTW - I am experimenting by disabling the NM applet, and setting the interfaces file to control things manually. 

Is CKIP supported in some manner ?  Would sure love to know how, I assume with Cisco's great presence in the corporate world it would be a fairly common request... otherwise kinds of relegates my ubuntu machine to a desktop instead of a laptop :(

---

