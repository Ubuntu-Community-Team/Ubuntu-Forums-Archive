---
title: "[SOLVED] Trouble with HTTPS and Windows Live Messenger on XP clients"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by gilly54 on 2007-11-18
Well I'm quite new to Linux (just installed it yesterday, now the PC dual boots XP and Ubuntu) and after hours of Ubuntu forum surfing and learning bash from scratch, I'm starting to figure things out, one of them is Internet Connection Sharing. Basically my ISP uses PPPoE which comes in the form of a cable into a network card on the now-Linux PC, theres another network card which connects the PC to the home network. 
I managed to get the PC to share the internet connection with the whole house (Vista installed). Everyone can view normal HTTP webpages fine but Windows Live Messenger doesn't seem to be connecting and HTTPS secure pages aren't opening. When I boot up Windows XP on the PC and start the (shared) internet connection, everyone is able to sign onto Messenger and open HTTPS pages. Could Ubuntu be blocking Live Messenger and HTTPS traffic somehow? They both open fine on Ubuntu (replacing Windows Live Messenger with Pidgin of course...)

Edit: I used this guide here to set up the connection sharing:
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)
Heres a network diagram which might help too:
[IMG]http://img233.imageshack.us/img233/5269/64848758ia6.jpg[/IMG]

---

### Post by Blutack on 2007-11-18
Are you using firestarter?
(BTW, thankyou for your clear post)

---

### Post by gilly54 on 2007-11-18
Well I do have it installed as I was following another guide that suggested Firestarter, but that didn't work out too well...But not using it currently, it's completely off.

---

### Post by Blutack on 2007-11-18
Hmm...
could you try running

wget -v [https://www.facebook.com/](https://www.facebook.com/)

in a terminal for me please (on one the non-connecting ubuntu PC's) and post the output.  
I can't figure out what your laptops are running so if they are XP/Vista my apologies.
If it kicks out an error about ssl certificates that is ok, for example here is mine

wget -v [https://www.facebook.com/](https://www.facebook.com/)
--15:56:59--  [https://www.facebook.com/](https://www.facebook.com/)
           => `index.html'
Resolving [www.facebook.com](www.facebook.com)... 69.63.176.12
Connecting to www.facebook.com|69.63.176.12|:443... connected.
ERROR: Certificate verification error for [www.facebook.com:](www.facebook.com:) unable to get local issuer certificate
To connect to [www.facebook.com](www.facebook.com) insecurely, use `--no-check-certificate'.
Unable to establish SSL connection.

(Sorry for using facebook, I needed a https site off the top of my head.)

---

### Post by gilly54 on 2007-11-18
wget -v [https://www.facebook.com](https://www.facebook.com)
--18:03:25--  [https://www.facebook.com/](https://www.facebook.com/)
           => `index.html'
Resolving [www.facebook.com](www.facebook.com)... 204.15.20.80
Connecting to www.facebook.com|204.15.20.80|:443... connected.
ERROR: Certificate verification error for [www.facebook.com:](www.facebook.com:) unable to get local issuer certificate
To connect to [www.facebook.com](www.facebook.com) insecurely, use `--no-check-certificate'.
Unable to establish SSL connection.
That was what I got...

And the guide that I used in my first post was HTTPS BTW...It opens fine on the Linux machine but not on the Windows machines I'm sharing the Internet connection with...

---

### Post by Blutack on 2007-11-18
Right, sorry I meant could you try it on one of the machines that is failing to connect.  I suspect your problem lies in firewalling.  Firestarter does weird things to connections even when not in use.  Could you try removing it?

---

### Post by gilly54 on 2007-11-18
Simple as that...Thank you so much for your help, it's working fine now, you rock!
Just one more question, whenever I restart the Linux machine, I have to go through the first 3-4 steps of this guide so that Internet sharing works again:
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)
Is there a way this can be done automatically at startup, through the use of a script of some sorts?

---

### Post by Blutack on 2007-11-18
Easy peasy,

> 
#!/bin/bash
my command
my next command...etc etc
end



Set it executable and test it.  Be aware you do not need the sudo - when the system boots, the startup scripts are executed as root.  To test it, 
reboot, become root:
sudo su
and then ./routingup.sh
check your connections, if all is well add it to the startup sequence.  You might want to make sure that it runs after your /etc/init.d/networking script if any of the stuff conflicts.
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by Blutack on 2007-11-18
And yeh, firestarter can be a bitch.  You are lucky :)
In breezy, installing and removing firestarter left your routing table so screwed up you had no internet connection.  Never trust a program that forces you to reinstall.

---

### Post by gilly54 on 2007-11-18
Alrightey, thanks again!

---

