---
title: "connecting using conxant modem"
date: 2004-12-05
forum: Networking &amp; Wireless
---

### Post by keemo on 2004-12-05
Hi all,

I've just installed ubuntu on m HP ze4281, and eerything is wonderfull. And eing a newbie, it was a great opportunity to learn how to install drivers for my conexant 56K modem. But this is as far as I can go...

I ran 'pon' and I can get a dialtone, which indicates to me that the modem and its drivers are working (unless I'm wrong!!)

I've setup a new connection through 'Networking' and when I activate it it dials and I hear it tryng to connect, but then nothing happens...i don't get any sort of error/success message, so I have no clue as how to how to troubleshoot that....

any suggestions?

---

### Post by az on 2004-12-05
Sudo pppconfig
enter your info
save
sudo pon
tail -f /var/log/messages
try the internet if it looks like it is working.

Add modem lights (applet) to your panel and edit the properties.

Post the /var/log/messages if it did not work.

---

### Post by keemo on 2004-12-06
thanks azz

I tried what you suggested, but all I got is a dialtone....it didn't seem like it was dialing at all. How do I get it to dial the connection that I created using pppconfig???

I should probably mention that once I started the lapto again, I had to run hsfconfig as ubuntu did not even find a dial tone.

heres my /var/log/messages after sudo pon
Dec  6 19:32:58 localhost chat[6197]: abort on (VOICE)
Dec  6 19:32:58 localhost chat[6197]: abort on (NO DIALTONE)
Dec  6 19:32:58 localhost chat[6197]: send (ATZW2^M)
Dec  6 19:32:58 localhost chat[6197]: expect (OK)
Dec  6 19:32:58 localhost chat[6197]: ATZW2^M^M
Dec  6 19:32:58 localhost chat[6197]: OK
Dec  6 19:32:58 localhost chat[6197]:  -- got it
Dec  6 19:32:58 localhost chat[6197]: send (ATDT<put^M)
Dec  6 19:32:58 localhost chat[6197]: expect (phone)
Dec  6 19:32:58 localhost chat[6197]: ^M
Dec  6 19:33:19 localhost chat[6197]: ATDT<put^M^M
Dec  6 19:33:19 localhost chat[6197]: BUSY
Dec  6 19:33:19 localhost chat[6197]:  -- failed
Dec  6 19:33:19 localhost chat[6197]: Failed (BUSY)

I may be wrong, but that to me looks like its getting a busy signal...now I should tell you that there was a dial tone for a few seconds, and then a busy signal.

one more question...at home I use my LAN to connect to the internet so i have my laptop setup there. I need my dialup connection when I'm out. When using the dialup account, do I need to remove the gateway and DNS settings for the network? 

Thanks for you help.

---

### Post by az on 2004-12-06
Pon makes you connect to the connection named provider that you set up with pppconfig.  If you named it something else, like "VIF" then you need to do pon VIF

Make sure you are set up properly because you do not seem to be dialing a number (in your logs)


As for the lan gateway stuff, I dunno.  Perhaps pppd takes care of that?

---

### Post by keemo on 2004-12-06
Thanks azz, I'll try that again when I get home. It seems so obvious now that I had to include the name of the connection  #-o 

does ubuntu (or any other linux distro for that matter) load the modem drivers during boot time? or do I have to edit a file to get them to load at boot? If so, which file and how should I edit it?

I appreciate your help and patience with me.  :smile:

---

### Post by keemo on 2004-12-07
its working now!
thanks for your help azz, but I strill have one little issue...everytime I restart the laptop I need to run hsfconfig again to load the drivers...is there a way to get them to load on boot time?

---

