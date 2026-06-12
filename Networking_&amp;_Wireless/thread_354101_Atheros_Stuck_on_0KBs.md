---
title: "Atheros Stuck on 0KB/s"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-02-05
Hey I Posted earlier about this very same subject but it is no where to be found on the forums???/

Was I censored??? Hopefully not



Any way My access point Worked for an hour and a half but now????? although it broadcasts and clients can connect when i check the information about it 

[SIZE="6"]Normal Mode[/SIZE]

ath0      IEEE 802.11b  ESSID:"Accesspoint"  
          Mode:Managed  Frequency:2.484 GHz  Access Point: Not-Associated   
      **    Bit Rate:0 kb/s**   Tx-Power:31 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:BF71-5772-DADA-8A3E-7AFF-A5C2-6B   Security mode:restricted
          Power Management:off
          Link Quality=0/94  Signal level=-91 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ppp0      no wireless extensions.

[SIZE="6"]Master Mode[/SIZE]
 IEEE 802.11g  ESSID:"Accesspoint"  
         ** Mode:Master ** Frequency:2.412 GHz  Access Point: 00:13:F7:1F:C4:E9   
         ** Bit Rate:0 kb/s  ** Tx-Power:31 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:BF71-5772-DADA-8A3E-7AFF-A5C2-6B   Security mode:restricted

Please please please somebody help

It's not as straightforward as you might think and I would like to make a very detailed howto out of this experience

Cheers in Advance

---

### Post by tturrisi on 2007-02-05
> It's not as straightforward as you might think and I would like to make a very detailed howto out of this experience
agreed!
What the heck are you asking anyway?

---

### Post by andytof47 on 2007-02-05
Hmm Seems My Atheros cards is stuck on 0kb/s

I am wondering how do I get it back up to transmit at 54kb/s

I have tried different commands in different modes but as the opening post shows

No matter wether itis in managed mode or in master it ain't sending any data

I think it is is only sending transmission beacons???? This is because When in master mode i can still connect ....It just doesn't do anything thats all....


Cheers in advance

---

### Post by tturrisi on 2007-02-05
How do you know you can connect?
Can you then use the connection, e.g. web browser, email, etc?

---

### Post by andytof47 on 2007-02-05
boot up windows on my laptop and scan for a network

then select "Myaccess"


It connects fine 

Tells me it recieves 2 packets 


Open firefox or thunderbird and nothing

open cmd ping [www.google.com](www.google.com) or 203.2.124.164 (my isp dns server usually responds to ping)

Signal is apparently excellent

Just stuck at 0KB/s

Cheers for the fast rep[ly too:)

---

