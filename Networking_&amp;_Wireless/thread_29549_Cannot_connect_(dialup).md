---
title: "Cannot connect (dialup)"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by fivre on 2005-04-24
I want to stop using Win98 so much, but ubuntu has one little problem. It won't connect to the internet. 

Now, In have a modem that it recognizes. It even starts making the connection noise. It gets almost completely through the connect process and then... Dies. The connection just no longer exists. It doesn't even make noise on the line  ](*,).

If anyone knows why this happens I would be much overjoyed. 
It may or may not be related, but I can't seem to connect through modem lights (although it does display the blinking yellow "connecting" light), only the "activate" button in Network Connections.

---

### Post by az on 2005-04-24
Try this:  Open a terminal and do
sudo tail -f /var/log/messages

and in another terminal do 
sudo pppconfig
enter all your connection information.  Name the connection provider.  Save before you quit.

do
sudo pon

and post the output of the first terminal as it tries to connect.  You will see the status and the error codes there.

---

### Post by fivre on 2005-04-26
> Apr 26 00:25:22 localhost pppd[4251]: pppd 2.4.2 started by root, uid 0
Apr 26 00:25:23 localhost chat[4252]: abort on (BUSY)
Apr 26 00:25:23 localhost chat[4252]: abort on (NO CARRIER)
Apr 26 00:25:23 localhost chat[4252]: abort on (VOICE)
Apr 26 00:25:23 localhost chat[4252]: abort on (NO DIALTONE)
Apr 26 00:25:23 localhost chat[4252]: abort on (NO DIAL TONE)
Apr 26 00:25:23 localhost chat[4252]: abort on (NO ANSWER)
Apr 26 00:25:23 localhost chat[4252]: abort on (DELAYED)
Apr 26 00:25:23 localhost chat[4252]: send (ATZ^M)
Apr 26 00:25:23 localhost chat[4252]: expect (OK)
Apr 26 00:25:23 localhost chat[4252]: ATZ^M^M
Apr 26 00:25:23 localhost chat[4252]: OK
Apr 26 00:25:23 localhost chat[4252]:  -- got it
Apr 26 00:25:23 localhost chat[4252]: send (ATDT5283658^M)
Apr 26 00:25:23 localhost chat[4252]: expect (CONNECT)
Apr 26 00:25:23 localhost chat[4252]: ^M
Apr 26 00:25:46 localhost chat[4252]: ATDT5283658^M^M
Apr 26 00:25:46 localhost chat[4252]: CONNECT
Apr 26 00:25:46 localhost chat[4252]:  -- got it
Apr 26 00:25:46 localhost chat[4252]: send (\d)
Apr 26 00:25:47 localhost pppd[4251]: Serial connection established.
Apr 26 00:25:47 localhost pppd[4251]: Using interface ppp0
Apr 26 00:25:47 localhost pppd[4251]: Connect: ppp0 <--> /dev/ttyS0
Apr 26 00:25:48 localhost pppd[4251]: Connection terminated.
Apr 26 00:25:49 localhost pppd[4251]: Hangup (SIGHUP)
Apr 26 00:25:49 localhost pppd[4251]: Exit.


So... It's connecting but it's suiciding right after? How nice of it.

---

### Post by fivre on 2005-04-29
Well, there appears to have been some sort of problem with my ISP (AT&T Worldnet). Now that I (might) have sorted that, I'm getting a > CHAP authentication failed: Authentication Failed(Network id is non-digit or no @ sign) message.

What do you do to correct this?

---

### Post by Professor X on 2005-04-29
Does  the file /etc/ppp/chap-secrets contain you username/password in the form

```
user@worldnet.att.net * "password" *
``` ?

---

### Post by fivre on 2005-04-30
Not exactly (there were quotes around the username and the password did not have the second asterisk.)

Changing it got the same error though.

---

### Post by Professor X on 2005-04-30
I found [this](http://www.wurd.com/instcon_linux.php) tutorial for you.  Good luck.

---

### Post by fivre on 2005-04-30
Unfortunately, I already found that.

It's a bit old too. Haven't been able to get it (or any others) to work.
Mostly I'd like to figure out what to do with the error at the moment.

---

### Post by The_Living_Linux on 2005-05-16
Hi,
I installed ubuntu 4.10 on my laptop just recently and I was trying to setup my dialup. Results : ](*,)  again and again and again.....
I spent a good deal of time going through this forum and listed below are some of the things I tried but didnt work

1)I tried configuring the dialup through Computer >System Configuration> Networking......but the wizard doesnt recognize my modem...????

2)Wvdial, displays a msg saying "cannot open /dev/modem : no such file or directory"

3)Ran the scanmodem utility and generated the Modem Data.txt file...didnt know what to do then??

I am helplessly lost,what do i do to get my dialup working?

lspci says :
0000:00:if. 6 Modem : Intel Corp. 82801DB (ICH4) AC'97 Modem Controller (rev 03)


Thanx in advance !!

---

### Post by jodef on 2005-05-16
[QUOTE=fivre]Unfortunately, I already found that.

It's a bit old too. Haven't been able to get it (or any others) to work.
Mostly I'd like to figure out what to do with the error at the moment.[/QUOTE]
Try this 

/etc/ppp/options contains the auth option. Simply put a # comment in front and try again.

---

