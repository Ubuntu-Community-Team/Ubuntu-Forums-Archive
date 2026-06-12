---
title: "wpa key"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by mbzn on 2009-06-23
Quick question, How can i see the wpa-key i am using or would it work if i re-enter the hashed key on another computer?
Please help as i am about to format my computer and would like internet when i'm done...

---

### Post by LowSky on 2009-06-23
you need the password, the number generated code is not the same, its there to act as a place holder, sorry no way to see it... i guess your stealling Wifi, huh?

it is also against the policy of the forums to hlep with that type of behavior.

Best thing to do if your not stealing and own the router is to reset your password to something you can remember

---

### Post by paul_be on 2009-06-23
Also make sure you don't need to download third party wireless drivers after you format.  You may consider Ethernet (wired) connection while installing your new OS:)

---

### Post by mbzn on 2009-06-23
believe me, if i stole it i would have the code written down somewhere... i actualy pay for it but the person that knows the password is currently not reachable... is there any way of backing up the wireless setting for restore after the install?

I can fully understand that you cant give the tutorial for wpa cracking on the forum. but there has to be a "legal" way of me getting the internet back after a fresh install...

Thanx

---

### Post by KIAaze on 2009-06-23
> **mbzn said:**
> Quick question, How can i see the wpa-key i am using or would it work if i re-enter the hashed key on another computer?
Please help as i am about to format my computer and would like internet when i'm done...

I think the SSID and the hashed key (what you get when you check the "show key" checkbox) is enough.
But I'm not 100% sure and can't test it right now, not being on my Ubuntu laptop.

Try booting from the live CD and accessing the wireless network using only the SSID and hashed password. Of course, you'll need a wireless card that works out of the box for that. :/
Another solution would be doing a frugal install of puppy linux for example. If you really want to be sure you can access the network after reformatting, you must be able to access it before from a system without the password stored.

cf also:
[http://ubuntuforums.org/showthread.php?t=558612](http://ubuntuforums.org/showthread.php?t=558612)
[http://www.xs4all.nl/~rjoris/wpapsk.html](http://www.xs4all.nl/~rjoris/wpapsk.html)

If you can, backup all your home directory (or are WPA settings stored for all users?), at least all hidden files.

---

### Post by RD1 on 2009-06-23
Right click your current wireless connection indicator in the notification area. Select "Edit Connections". In the "Network Connections" window, select the "Wireless" tab. Select your wireless connection and click the "Edit" button. Select the "Wireless Security" tab. Check the "Show Password" box. Copy and Paste the wireless key into a text file and print it. Store printed key is a safe place. :D

---

### Post by mbzn on 2009-06-23
thanks for all the info... my xml files are all in hex and converting back don't work so it is encrypted somehow... so that might have worked back in the days... 

thanx for trying anyway.

Something that seems to "may work" is if i keep my /home partition, witch i plan to do... but i want to be sure. (i am installing ubuntu 9.04 over my current install of 9.04) i'm just converting to ultimate edition again as i like the skins and stuff that comes with it..

I will try booting the live cd, how can i mount my current /home to the live cd boot?

---

### Post by mbzn on 2009-06-23
> **RD1 said:**
> Right click your current wireless connection indicator in the notification area. Select "Edit Connections". In the "Network Connections" window, select the "Wireless" tab. Select your wireless connection and click the "Edit" button. Select the "Wireless Security" tab. Check the "Show Password" box. Copy and Paste the wireless key into a text file and print it. Store printed key is a safe place. :D

the way i understand it is that if you take your SSID and add your passphrase together and hash that, then only you get the hex key that is displayed. am i correct, sure hope i'm wrong cuz that will make things easy--er...

Thanx

---

### Post by KIAaze on 2009-06-23
> **mbzn said:**
> 
I will try booting the live cd, how can i mount my current /home to the live cd boot?

Just click on "Places" and then on the partition you want to mount.
It should then put an icon on the Desktop and open nautilus with contents of the partition.

If you want to reinstall using the existing home partition, just:
-choose manual partitioning during the install process
-set the home partition to be mounted as "/home"
-don't format the home partition

I couldn't find a tutorial for this, but it's pretty easy and as long as you don't format the home partition during install, you're safe.

Here's how to move /home:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You could probably use the above information to somehow change the home of the Live CD to your home partition, but I don't think that's necessary.

---

### Post by RD1 on 2009-06-23
I guess I'm confused. :( I've been using the same 26 character passphrase for years. Through countless OS reinstalls, I've never had to decrypt it to re-enter in a new wireless connection.

---

### Post by mbzn on 2009-06-23
ok, sorry RD1, you were right. i put in the hex phrase i have copy/pasted and it worked fine. it confuses me too though cuz it doesn't relate to the real pass-phrase at all. but it works and that is what counts.... thanx for all your help and opinions. hope this will answer lots of future questions, and solve some problems for other users in the same boat....

Thanx again to you all

---

### Post by RD1 on 2009-06-23
:D Glad you got it worked out.

---

### Post by 3rdalbum on 2009-06-23
> **mbzn said:**
> it confuses me too though cuz it doesn't relate to the real pass-phrase at all. but it works and that is what counts.... 

It confuses a lot of people, but you're wrong about one thing. The key does relate to the passphrase.

The passphrase is [hashed]("http://en.wikipedia.org/wiki/Cryptographic_hash_function") in order to generate the key. Encryption algorithms require a key that is a specified length (for instance, 16 characters) and won't work with something that is longer or shorter.

There's two ways to create a key of a 16 character length. Let's say your passphrase is "ilovemum". You could pad out the password to 16 characters:

ilovemum00000000

But this doesn't really help security, and if your password was more than 16 characters you'd need to truncate it which is less secure.

The other way to make a 16 character key from a password is by hashing the password to create a seemingly-random string of hexidecimal characters. Much more difficult to guess and much more difficult to crack than "ilovemum". And it's still as secure, or more secure, if you have a password that exceeds 16 characters.

---

