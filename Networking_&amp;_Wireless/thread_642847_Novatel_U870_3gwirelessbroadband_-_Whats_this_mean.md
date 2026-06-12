---
title: "Novatel U870 3gwirelessbroadband - Whats this mean apart from its not working?"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by M00_cow on 2007-12-17
Hey,

Im just new to Ubuntu so im not so great at understanding the occasional walloftext terminal spams at me when the occasional error arises. I used to use windows, and i've moved over to linux for obvious reasons (its windows) hehe :P. Ive gone through the howto on the novatel site on how to install/connected/make this thing work and i think im very close. i get to the stage where you type...

sudo pppd file /etc/ppp/hsdpa_options

which in noob terms for me attempts to connect to the 3 network (establish connection)
while this is all happening i do hav another terminal open which gives me connection spam as to wats happening in terms of connections using the following command

sudo tail -f /var/log/messages

getting this far, i use the command to connect and the spam starts. here it is. 

Dec 17 20:10:52 m00 pppd[8837]: pppd 2.4.4 started by root, uid 0
Dec 17 20:10:53 m00 chat[8839]: abort on (BUSY)
Dec 17 20:10:53 m00 chat[8839]: abort on (NO CARRIER)
Dec 17 20:10:53 m00 chat[8839]: send (at^M)
Dec 17 20:10:53 m00 chat[8839]: expect (OK)
Dec 17 20:10:53 m00 chat[8839]: at^M^M
Dec 17 20:10:53 m00 chat[8839]: OK
Dec 17 20:10:53 m00 chat[8839]:  -- got it 
Dec 17 20:10:53 m00 chat[8839]: send (atd *99#^M)
Dec 17 20:10:53 m00 chat[8839]: expect (CONNECT)
Dec 17 20:10:53 m00 chat[8839]: ^M
Dec 17 20:10:53 m00 chat[8839]: atd *99#^M^M
Dec 17 20:10:53 m00 chat[8839]: CONNECT
Dec 17 20:10:53 m00 chat[8839]:  -- got it 
Dec 17 20:10:53 m00 chat[8839]: send (\d)
Dec 17 20:10:54 m00 pppd[8837]: Serial connection established.
Dec 17 20:10:54 m00 pppd[8837]: Using interface ppp0
Dec 17 20:10:54 m00 pppd[8837]: Connect: ppp0 <--> /dev/ttyUSB0
Dec 17 20:10:55 m00 pppd[8837]: CHAP authentication succeeded
Dec 17 20:10:55 m00 pppd[8837]: CHAP authentication succeeded
Dec 17 20:10:55 m00 kernel: [ 3233.628000] PPP BSD Compression module registered
Dec 17 20:10:55 m00 kernel: [ 3233.716000] PPP Deflate Compression module registered
Dec 17 20:10:57 m00 pppd[8837]: Hangup (SIGHUP)
Dec 17 20:10:57 m00 pppd[8837]: Modem hangup
Dec 17 20:10:57 m00 pppd[8837]: Connection terminated.
Dec 17 20:10:58 m00 pppd[8837]: Exit.

thats the part in which im wondering whats happening so i can locate the error and fix it. when i see that all i read is "Connection terminated" and i cry.

Thanks for the help

m00

---

