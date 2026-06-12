---
title: "wireless problem"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by Pf123 on 2006-08-21
Hi, I'm new to ubuntu, but not new to linux wireles problems.
Yesterday,(and ahwile before) I was running Knoppix, installedon harddrive, and I never used it due to the fact of no internet.  But I've been bored, and deciding to once again burden myself with wireless linux related problems :p

This is an older laptop, a Compaq presario 1279, with ubuntu 6.06 installed on harddrive.

Seems like same problem I had with knoppix, my router doesnt assign an ip.  I'm not all that great at linux yet either.
Well, in knoppix, from what i gathered it was a dhcp problem, seeing as my 2WIRE router uses dchp, and when i do a dchp thing with knoppix, it fails.
Having yet being able to find out how to do dchp with ubuntu, im only guessing its the same problem.

Ill put a little bit of if config, and iwconfig, from what I think is valuable information, if you need more just ask me (because I cannot copy paste, because im on another computer :S)

Well, some quick specs:
Compaq Presario 1279
Ubuntu 6.06 harddrive install
2WIRE Gateway
SMC Wireless card (not built in)
Problem:
Internet doesnt work, probably dchp related.


iwconfig (what i think gives you a clue or two):

eth0 IEEE 802.11b  ESSIDE:"2WIRE258" Nickname:"Prism I"
     Mode:managed  Frequency:2.437 GHz  Access Point: 00:14:95:74:A6:61
.....then it just goes on

ifconfig (what i think gives you a clue or two):

....some stuff before
lo    
   inet addr:127.0.0.1  mask:255.0.0.0
...and it goes on



ok, so if you need more stuff on iwconfig or ifconfig, tell me what is needed for you to help me get this to work

From what I understand, it finds the router (iwconfig shows name and an access point), but no ip is assigned to it, except for 127.0.0.1 which is local host(looking at ifconfig, at the lo part)

So it seems same problem as knoppix, but im happy i switched to ubuntu, it starts alot faster :p

Thanks in advance :wink:
edit:  Also, wireless works in Windows, but I no longer have windows, so I dont believe its a problem with the card or the computer.

---

### Post by meng on 2006-08-21
This is what I try with my laptop:

sudo iwconfig eth0 essid 2WIRE (looks like you've already done this)
sudo iwconfig eth0 key [enter key here] (I guess you did this too)
sudo ifconfig eth0 up
sudo dhclient eth0
ping google.com

It's hard to tell from your post what you've already tried.

---

### Post by Pf123 on 2006-08-21
> **meng said:**
> This is what I try with my laptop:

sudo iwconfig eth0 essid 2WIRE (looks like you've already done this)
sudo iwconfig eth0 key [enter key here] (I guess you did this too)
sudo ifconfig eth0 up
sudo dhclient eth0
ping google.com

It's hard to tell from your post what you've already tried.

I'll try that, thank you.  I had used the network thing under adminitrative.
Will report back in a few minutes

Edit1:  Tried to do the key thing, got an error, trying to put the password is as hex now.
Edit2:  Nope, failed aswell.
Got this error for both:
"Error for wireless request "Set Encode" (8B2A): "
but on the ascii, after the above error I got this:
"SET failed on device eth0 ; Operation not supported."
and on the hex one, this I got after the "Error for wireless...":
"invalid argument "%37%36%32%31%31%37%31%37%33%38".

is %36 correct hex? I used:
[http://centricle.com/tools/ascii-hex/](http://centricle.com/tools/ascii-hex/)

---

### Post by meng on 2006-08-21
To enter an ASCII key this is the syntax:
sudo iwconfig eth0 key s:[enter ASCII key]

---

### Post by Pf123 on 2006-08-24
when trying to enter the key, i get this:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Operation not supported.


have any other ideas?:-k

---

### Post by NetworkGuy on 2006-08-24
pf123,

Can you post the results of ```
iwconfig
```

Thanks.

---

### Post by Pf123 on 2006-08-24
```
lo    no wireless extensions.

sit0    no wireless extensions.

eth0    IEEE 802.11b  ESSIDE:"2WIRE258"  Nickname:"Prism I"
        Mode:Managed  Frequency:2.437 Ghz    Access Point:  00:14:95:74:A6:61
        Bit Rate:11 Mb/s    Sensitivity:1/3
        Retry min limit:8    RTS thr:off    Fragment thr:off
        Power Management:off
        Link Quality=92=92   Signal level=45/153    Noise level=107/153
        Rx invalid nwid:0    Rx invalid crypt:280    Rx invalid frag:0
        Tx excessive retries:0    Invalid misc:0    Missed beacon:0

```

signal is 45/153? what does that mean, its right next to the router :neutral:

---

### Post by NetworkGuy on 2006-08-24
it looks like ETH0 is associated with your access point/router.  
Do you have any WEP/WPA set on it?  Maybe that needs to be redone again

When you do a ```
ifconfig
``` do you see ETH0?

---

### Post by Pf123 on 2006-08-24
> **NetworkGuy said:**
> it looks like ETH0 is associated with your access point/router.  
Do you have any WEP/WPA set on it?  Maybe that needs to be redone again

When you do a ```
ifconfig
``` do you see ETH0?

yes i see an eth0 on it, and it does have a password, but it should be entered correctly
I have to go for a bit later, ill read this when i get back

---

### Post by NetworkGuy on 2006-08-24
I reread your previous posts, try entering your WEP key without the % in front of each set of hex numbers

---

### Post by Pf123 on 2006-08-24
> **NetworkGuy said:**
> I reread your previous posts, try entering your WEP key without the % in front of each set of hex numbers

Error for wireless request "Set Encode" (8B2A) :
SET failed on device eth0 ; Operation not supported.

same thnig as usual, but doing it in ASCII doesnt work either

---

### Post by Pf123 on 2006-08-26
I hate to double post on a forum, especially when im new to it, but I needed to bump this topic :cry:

---

### Post by rjdohnert on 2006-08-26
Have you just tried using the GNOME Networking utility under Administration, believe it or not when my WEP key wasnt going through manually I did it with the utility and havent had any problems.

---

### Post by Pf123 on 2006-08-26
> **rjdohnert said:**
> Have you just tried using the GNOME Networking utility under Administration, believe it or not when my WEP key wasnt going through manually I did it with the utility and havent had any problems.

That was the first thing I tried, the activating part would take a long time, but it would finish, but no internet :-k

---

### Post by Pf123 on 2006-08-26
bump again :-\"

---

### Post by NetworkGuy on 2006-08-26
I know it's a step backwards, but did you try your setup without WEP on your router?

It at least allows you to use your machine while the community and you search for the answer

---

### Post by NetworkGuy on 2006-08-26
I have read in some postings that SMC is extremely hard to get working in any distro of Linux.

---

### Post by Pf123 on 2006-08-26
> **NetworkGuy said:**
> I know it's a step backwards, but did you try your setup without WEP on your router?

It at least allows you to use your machine while the community and you search for the answer

Well, I'm not in much of a rush, I just want to have internet on that laptop, but I mean I have another laptop (running windows) and a desktop (also windows) that works good with internet.

And I'm just using the default key of the router, which is the serial number of the router :p.  I'll turn off the WEP and see if that works, thanks network guy.

It WORKS! Thanks networkguy, for now ill just have no encryption, dont think anyone here will want to use my connection anyways (noone near my home really).
So i guess that solves the problem for SMC card users, dont use WEP :p

---

### Post by NetworkGuy on 2006-08-26
Let us know that that works.

---

### Post by Pf123 on 2006-08-26
> **NetworkGuy said:**
> Let us know that that works.


posting this from my ubuntu laptop, it works

thanks alot NetworkGuy :)

---

### Post by NetworkGuy on 2006-08-26
Now you can enjoy surfing on your new Ubuntu loaded laptop :)  while trying to figure out how to get WEP working for your SMC card. ](*,) 

Or get a different WiFi card ;) 

Ok, that's my limit for Smilies in a posting.

---

