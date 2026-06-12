---
title: "PPPoE Issue With Non-Standard Settings Required by ISP"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by TAfricanski on 2007-02-07
Hi. I posted [this]("http://ubuntuforums.org/showthread.php?t=351686") in the Absolute Beginner Talk but nothing offered there was of work so I was adviced to post it in this section, too.

My ISP requiers me to set the following lines in the /etc/ppp/pppoe.conf file:

ACNAME=Day1-PPPoE

SERVICENAME=home-unl


I tried to find the above mentioned file after configuring PPPoE in the way explained in the support page of Ubuntu, but the file does not seem to exist.
I know the answer probably is 'RTFM', but nothing there seems to work. I've been trying for more than a month now...

Under XP I create a new PPP broadband connection using the 'Create new connection' wizard, then right-click the connection, open properties and change the Service name in the General page to 'home-unl'. I connect to the ISP via a LAN, plugged into my Eth1, over which a PPPoE connection is established.
That's all I know about my connection.

Please, help me go online with my Ubuntu!

The thread in the Absolute Beginner Talk: [http://ubuntuforums.org/showthread.php?t=351686]("http://ubuntuforums.org/showthread.php?t=351686")

---

### Post by TAfricanski on 2007-02-08
Help :)

---

### Post by xbadger on 2007-02-12
if u have a pppoe connection try:
"sudo pppoeconf" and fallow the steps
should work ;)

---

### Post by mips on 2007-02-12
Do you have to use PPPoE ?

What networking modem/router do you have and who is the ISP/telco ?

---

### Post by TAfricanski on 2007-02-12
There were no options such as ACNAME or SERVICENAME to be set there. I need a solution beyound sudo pppoeconf...

---

### Post by TAfricanski on 2007-02-12
I do not have a modem or router, my eth0 i directly connected to the LAN/MAN of my ISP. THe name won't help you - Networx Bulgaria.
Over the LAN is established a PPPoE connection directly with Networx servers.

Yes, I have to use PPPoE, as the ISP is currently migrating all its clients from VPN tunneling through the MAN to PPPoE. Even if they let me use VPN, I don't think it will be easier to configure.
So let's say I have no choice and PPPoE is inevitable ;)

---

### Post by mips on 2007-02-13
Have you tried searching for the file ? 

**locate pppoe.conf**

Something seems wrong with your pppoe setup. You  should have a pppoe.conf in /etc/ppp/.

Which guide did you follow, this one [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)  ?

Maybe try to reinstall pppoe.

---

### Post by TAfricanski on 2007-02-13
No, there is no such file on my HD. It is used by another PPPoE client or something like that, I am not very sure. The default PPPoE client that comes with Ubuntu keeps its settings in /etc/ppp/peers/dsl-provider , but neither of the strings ACNAME and SERVICENAME is available there. I tried by just adding them in the beginning and in the end of the file, but I got an error message saying something similar to the "Bad command or filname" error in DOS.
I was advised by Stemp to add the following line in the beginning of dsl-provider:
```
pty "/usr/sbin/pppoe -I eth0 -T 80 -S service_name -C ac_name"
```
Thereafter, I got this terminal log:
```
root@user-desktop:~# pon dsl-provider
Plugin rp-pppoe.so loaded.
root@user-desktop:~# ping www.ubuntu.com
ping: unknown host www.ubuntu.com
root@user-desktop:~# plog
Feb  2 21:12:44 user-desktop pppd[5646]: Plugin rp-pppoe.so loaded.
Feb  2 21:12:44 user-desktop pppd[5648]: pppd 2.4.4 started by root, uid 0
Feb  2 21:12:44 user-desktop pppd[5648]: PPP session is 1224
Feb  2 21:12:44 user-desktop pppd[5648]: Using interface ppp0
Feb  2 21:12:44 user-desktop pppd[5648]: Connect: ppp0 <--> eth1
Feb  2 21:12:44 user-desktop pppd[5648]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Feb  2 21:12:44 user-desktop pppd[5648]: CHAP authentication failed: 8^TM-\M-7pbM-oM-7^F
Feb  2 21:12:44 user-desktop pppd[5648]: CHAP authentication failed
Feb  2 21:12:44 user-desktop pppd[5648]: Connection terminated.
root@user-desktop:~#
```
I was then told to check whether my username and password were correct in the /etc/ppp/pap-secrets file. Well, they were! It looked like this:
```
# LIC: GPL
# Edit this file and place it in /etc/ppp/pap-secrets

#User			#Server		#Password	#IP
tafricanski088	*		correct_password	*

# Replace bxxxxx@sympatico.ca with your Sympatico user-ID
# Replace my_password with your Sympatico password

# For Magma, use xxyyzz@magma.ca

"tafricanski088" * "correct_password"
```
Stemp said his file pap-secrets had nothing in common with mine, he doubted I had created it through sudo pppoeconf, but I said I had, so he gave me the contents of his file:
```
#
# /etc/ppp/pap-secrets
#
# This is a pap-secrets file to be used with the AUTO_PPP function of
# mgetty. mgetty-0.99 is preconfigured to startup pppd with the login option
# which will cause pppd to consult /etc/passwd (and /etc/shadow in turn)
# after a user has passed this file. Don't be disturbed therefore by the fact
# that this file defines logins with any password for users. /etc/passwd
# (again, /etc/shadow, too) will catch passwd mismatches.
#
# This file should block ALL users that should not be able to do AUTO_PPP.
# AUTO_PPP bypasses the usual login program so it's necessary to list all
# system userids with regular passwords here.
#
# ATTENTION: The definitions here can allow users to login without a
# password if you don't use the login option of pppd! The mgetty Debian
# package already provides this option; make sure you don't change that.

# INBOUND connections

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#       *       password



"euxxxxxxxx@tele2.fr" * "xxxxxxxx"
```
I substituted my pap-secrets with his, wrote my username and password where I was supposed to and then:
```
root@user-desktop:~# pon dsl-provider
Plugin rp-pppoe.so loaded.
root@user-desktop:~# ping www.ubuntu.com
ping: unknown host www.ubuntu.com
root@user-desktop:~# plog
Feb  2 23:03:44 user-desktop pppd[4870]: CHAP authentication failed: 8M-TM-[M-7p"M-oM-7^F
Feb  2 23:03:44 user-desktop pppd[4870]: CHAP authentication failed
Feb  2 23:03:44 user-desktop pppd[4870]: Connection terminated.
Feb  2 23:03:48 user-desktop pppd[3456]: PPP session is 954
Feb  2 23:03:48 user-desktop pppd[3456]: Using interface ppp0
Feb  2 23:03:48 user-desktop pppd[3456]: Connect: ppp0 <--> eth1
Feb  2 23:03:48 user-desktop pppd[3456]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Feb  2 23:03:51 user-desktop pppd[3456]: CHAP authentication failed: 8^TM-\M-7pbM-oM-7^F
Feb  2 23:03:51 user-desktop pppd[3456]: CHAP authentication failed
Feb  2 23:03:51 user-desktop pppd[3456]: Connection terminated.
root@user-desktop:~#
```
Stemp could do nothing for me anymore...

shareMenaPeace suggested that I ran sudo ppoeconf again with the default settings and no password and entering the pass manually in the pap-secrets, but this lead to nothing new.

That's the whole 'ticket' concerning my issue. ;)

Back to the point. Yes, this is the guide I followed, there was nothing hard about it, configuring pppoe meant just following on screen instructions, but it just did not ask about ACNAME and SERVICENAME!!! :(
I am not really sure what to reinstall pppoe means. A couple of times I tried to compile rp-pppoe which does use these settings, but I got an error concerning the configure file (or something similar), so this was of no help.

---

### Post by mips on 2007-02-13
Are you using the full userid, [email]userid@domainname.net[/email] or whatever ?

---

### Post by mips on 2007-02-13
> **TAfricanski said:**
> 
I am not really sure what to reinstall pppoe means. 

```
sudo apt-cdrom add
sudo apt-get install pppoeconf
dpkg -s pppoeconf
```

---

### Post by TAfricanski on 2007-02-13
I use the same username that I use to connect under windows. There is no reason that it is different.

---

### Post by TAfricanski on 2007-02-14
Reinstalling PPPoE did not help. It said I had the most recent version so it hadn't changed anything.

---

### Post by mips on 2007-02-14
Maybe remove it first and do a clean of the files then install it again.

pppoeconf should create a pppoe.conf file.

I don't use pppoe at all but this is the way I understand it to work.

---

### Post by saiman on 2007-02-15
I had a similar problem recently with my internet provider. Suddenly they added a service name in the authentication. This is how I solved it.

1. Install build-essential (if you don't have it already)
2. Download latest rp-pppoe [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)
3. Untar somewhere, run ./go  -- this will compile and install the software, after that a configuration dialogue will start. Fill in all information asked.
4. open /etc/ppp/pppoe.conf and add the needed info (namely acname and servicename)
5. run pppoe-connect

Should work fine.
Pozdravi, 

Simeon

---

### Post by TAfricanski on 2007-02-19
Heh, I did not receive e-mail notification for your answer! :( I saw it just seconds ago.
Well, I performed steps 2 and 3 and that's where I got the error. I don't know how to check whether build-essential is installed, neither do I know how to install it anyway.

Pozdravi,

Teodor ;)

---

### Post by mips on 2007-02-19
To install from the ubuntu cd,

```
 sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by TAfricanski on 2007-02-19
Yes, I was able to do it myself in a strange gui-way. I am either experiencing a bug or the bug is in my head, but I couldn't find out how to run synaptic from the menu. Furthermore, the program that is supposed to be used to show or hide different options in the menus just doesn't seem to put ticks where I want it to and does not work. Sometimes it does, but not when I really need something. I don't know why.
However, I copied the code for from this program and run it in terminal and then I was able to install build-essential. Then I compiled rp-pppoe, set all the settings, edin the pppoe.conf file and wrote pppoe-start... And it did not work :):):)
It timed out. From a debug command such as pppoe-status or so I read that a PID file was inaccessible. Well, yes, such file does not exist on my system.

Why don't it just work?!?!?!?!?!

---

### Post by mapuo on 2007-03-06
So I had the same issues with my ISP. The ISP wants  SERVICENAME (ACNAME is not obligatory). After some reading here and there I have successfully managed to get the connection working :)
I had to install a package from the Universe repository. The package name is: "pppoe". But for that I was lucky because I used unknown WiFi connection in the neighbor. 
Next was the edit of the /etc/ppp/peers/dsl-provider. Mine looks like this now:
```
# Minimalistic default options file for DSL/PPPoE connections
pty "/usr/sbin/pppoe -I eth1 -S ctc"
noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
user "mapuo"
```

Just make sure this line "plugin rp-pppoe.so eth1" to be commented or deleted. It is not needed as it seems.

Good luck and I hope I helped :)

---

