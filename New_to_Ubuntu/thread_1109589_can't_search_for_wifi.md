---
title: "can't search for wifi"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by jadu on 2009-03-28
Hello,

I have been experiencing what seems to be a common problem with my wifi. But I can't figure out from looking at previous posts how to deal with it. My internet actually just now started working again, but I have several questions still. I'll describe what I have first:

First, my internet icon from my task bar disappeared (which seems to happen to other people posting a lot).
Then it came back, but with problems.

Until a moment ago, I had the icon with the two computers and the orange triangle with exlamation point. This just changed to two computers with a red "do not enter" sign in front. When I click, it says

"Please contact your system administrator to resolve the following problem: Could not find information to interface with ´wlan0:avahi´in /proc/net/dev "

I also have the icon with the two computers (network settings?). When I click on wireless connection, it shows:
network name: (my server)
password type: wpa personal 
network password: something long, I don't know where it came from.
configuration: automatic configuration (dhcp)
Ip address, subnet mask, and gateway address are blank

When I right click and choose "enable wireless networks", it shows me a list of networks on the left, but old networks, not ones that are in range now. It also includes the one I currently use:
name: (name of network)
bssids: 00:1B:9E:DC:C6:27

security: wpa personal
password: something long, not the the password that I know.

my questions are:

- what does that error message above mean?
- what can I do to see the wireless networks in range, so I can use wireless when I go other places?
- when I click on "enable wireless networks", it asks me to "allow application access to keyring". should I just choose "always allow"?

any ideas would be appreciated!

(I am a beginner with Ubuntu and not much for computers in general, I don't understand any of the information I transcribed above, wlan, wpa, subnet mask, bassids etc...)

---

### Post by computerfreak on 2009-03-28
have you tried restarting your computer?

---

### Post by jadu on 2009-03-28
yes, I did just now, but the situation is the same.

---

### Post by jadu on 2009-03-30
Does anyone else have an idea on this? thanks

---

### Post by computerfreak on 2009-03-30
maybe you could use a different wireles client for your wifi

---

### Post by Mark Phelps on 2009-03-30
> **jadu said:**
> 
When I right click and choose "enable wireless networks", it shows me a list of networks on the left, but old networks, not ones that are in range now. It also includes the one I currently use:

It remembers networks you have connected with in the past.

> 
security: wpa personal
password: something long, not the the password that I know.

- what does that error message above mean?

Is this YOUR router/access point you are going through to get to the Net? Or is it someone elses (school's, office's, store's)?  Because if it's the latter, this implies that the device adminstrator has changed the password.

> 
- what can I do to see the wireless networks in range, so I can use wireless when I go other places?

You usually don't have to do anything other than right-click on the network icon to see a list of networks within range.

> 
- when I click on "enable wireless networks", it asks me to "allow application access to keyring". should I just choose "always allow"?

Yes, the keyring stores keys and the app is attempting to get the key for the network you selected.

---

### Post by jadu on 2009-03-30
Hi, thanks for the responses.

About using a different wireless client, I'm afraid I don't know what that means! I looked up "wireless client" on internet and found that it's something like the antena in the computer that receives the internet signal from the wireless, is that right? how would I change it?

> Is this YOUR router/access point you are going through to get to the Net? Or is it someone elses (school's, office's, store's)? Because if it's the latter, this implies that the device adminstrator has changed the password.

 yes, this is my router, the password hasn't been changed.


> Yes, the keyring stores keys and the app is attempting to get the key for the network you selected. 

 thanks for clearing that up!

> You usually don't have to do anything other than right-click on the network icon to see a list of networks within range.


that doesn't work though. Actually I'm not clear which is the "network icon", whether the two computers with the "do not enter" sign in front, or the two computers. the first one gives me "properties-help-about-remove from panel" when I right click. The second gives me "enable networking" (checked), "edit wireless networks", and "about". I explained in the previous posts what happens when I chose "edit wireless networks". 

But any idea how I can see the list of networks in range?

thanks

---

### Post by Cheesehead on 2009-03-30
You can get the current list of networks from the terminal with the following command - it will return what the wireless driver claims is in range. HOWEVER, some drivers also include the old information (that's why Network Manager also gives old info on some systems - it gets the list from the same place this command does).

Replace 'eth1' with the name of your interface. (eth1, ath0, etc.)
```
sudo iwlist eth1 scan
```

---

### Post by Mark Phelps on 2009-03-31
On one laptop, I never did get Network Manager to work properly for wireless, even after I did the NDISWrapper install.

My solution (which worked well for a lot of other folks) was to remove Network Manager and replace it with WiCD.  After that, I had no more wireless problems.

If you go to the Networking subforum and search on WiCD, you will find posts that walk you through how to do that.

Good Luck.

---

### Post by jadu on 2009-03-31
I installed Wicd, just with the directions on this site
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

and it seems to be working great!! thanks so much!!

---

