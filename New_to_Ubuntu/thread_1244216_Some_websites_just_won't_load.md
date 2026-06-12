---
title: "Some websites just won't load"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Wisey on 2009-08-19
My internet is behaving really weird, some websites, especially, but not limited to internet forums, just don't load properly. I get a looking up "soandso.com" on my status bar in firefox, and then it displays "Page Load Error", "Address Not Found :
Firefox can't find the server at soandso.com". The weird thing is, while these websites won't load, others load perfectly fine, and my torrents run flawlessly.

However, some websites which don't load at one time, load up at another time. For example, I couldn't access ubuntuforums all afternoon, but now it is opening fine. Some websites won't have this problem at all, such as facebook, while others seem to have this problem of not loading at random times.  I also experienced problems with update manager, and downloading stuff with synaptic, again, these don't seem to be permanent. 


Some websites which have this problem:
UbuntuForums.org
Arsenal-Mania.com
Answers.Yahoo.com

Some websites which don't have this problem:
Facebook.com
Google Mail
Google.com
I also play chess and go at FICS and KGS, I don't have any problem accessing these servers.

I dual boot with Windows XP, I seem to have the same problem over there as well.

I ignored it for a while, but not it is becoming really irritating, I can't seem to access half the internet. I search for something on google, and when I open websites one by one, I can't seem to open many of them. I didn't have this problem a month back, this seems to be a recent development. Please help. :(

---

### Post by Penguin Guy on 2009-08-19
If you have this problem with both operating systems it sounds like it could possibly be something as simple as a loose cable somewhere. Give all your internet cables a good shove to make sure they're in securely and see if the problem persists.

---

### Post by philinux on 2009-08-19
Is this a wired or wireless setup?

---

### Post by Wisey on 2009-08-19
Wired. 

And I checked all the cables, doesn't work.

---

### Post by superprash2003 on 2009-08-19
try using opendns servers - 208.67.222.222 and 208.67.220.220

---

### Post by Wisey on 2009-08-19
> **superprash2003 said:**
> try using opendns servers - 208.67.222.222 and 208.67.220.220
Thank you for the tip, it is working for now, but I really can't be sure because sometimes all the sites do manage to work. I will try it out for a day and see if everything is back to normal.

I am not exactly sure what was supposed to be done, but I went to System>Administration>Network, unlocked, and then added the DNS servers in the DNS tab.
Was this what I was supposed to do? 
If this works out, are there any consequences for adding those extra DNS servers?

---

### Post by superprash2003 on 2009-08-24
no consequences :)

---

### Post by sandyd on 2009-08-24
your settings will be lost on reboot if you do ti that way.

to keep them, follow instructions below. 
```

sudo cp /etc/resolv.conf /etc/resolv.conf.auto
gksudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
sudo ifdown eth0 && sudo ifup eth0

```
don't copy and paste. theirs instructions in the middle.

---

### Post by mnoyes on 2009-09-05
I have been having the same problem with a couple of websites:
nytimes.com
ila1588.org

I use open dns and have disabled IPV6. I have tried a variety of solutions, cleared the cache in firefox, disabled suspect add-ons, removed and reinstalled flash and firefox. Problem still persists.

All was fine after I upgraded to Jaunty, but about a month or two later, the problem started...:confused:

---

