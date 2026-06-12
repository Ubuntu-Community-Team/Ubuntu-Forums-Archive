---
title: "Wireless network always asking to unlock keyring"
date: 2015-09-01
forum: Networking &amp; Wireless
---

### Post by cogset on 2015-09-01
I've deleted the old "default" (as in: my own home network)  wi-fi connection on my laptop and added a new one, with a new WPA password: now everytime I try to connect I'm asked to unlock the default keyring password, and as a matter of fact I can see that the WPA password is now stored in this keyring.
But this never happened with the previous connection, I just used to click the network name in the nm applet cascade menu and it would connect.

I'm almost sure that all parameters (password aside) are the same between these two connections, any ideas on why this is happening?

How did I manage to skip this authentication step with my previous connection?

Is it maybe advisable to leave things as they are now ?

---

### Post by matt_symes on 2015-09-01
Hi

Is your keyring password the same as your login password ?

They need to be the same so that the keyring can be unlocked when you login.

That can cause this issue (or a at least that's what happened to me in the past).

Kind regards

---

### Post by cogset on 2015-09-02
Thanks for your reply, after reading it and goggling around a bit  looks like this issue (if it actually* is* an issue, and not intended behavior) is indeed related to the default keyring or login keyring (I'm not sure they are the same thing) .

Turns out I don't even have a default/login keyring, maybe because I added seahorse after installing Lubuntu (it's not part of the default installation as far as I understand), therefore for some reason when adding this new wi-fi connection a new keyring containing the wpa secret had been automatically created.
Which didn't happen when I set up the former wi-fi connection, maybe because at that time seahorse wasn't installed yet, I'm not sure.

Trying to set everything as it was before, I've deleted both the new wi-fi connection and this keyring, and then re-added the connection making it available to all users whilst also checking "automatically connect to this network when available" , and once again I can connect/disconnect without a password.

Now for the inevitable question: is this OK ? Is this somewhat less secure than leaving that option above ("automatically connect to this network when available")  unchecked, let the network manager create a default keyring and store the password in it, and finally being prompted for unlocking the keyring every time ?

Thinking of it, if the network manager can now connect automatically to this network, its wpa password (which I've entered  at the time this new connection had been added) must be stored somewhere, regardless of appearing in seahorse or not: where is it actually stored now ?

---

### Post by matt_symes on 2015-09-02
Hi


> **cogset said:**
> Thanks for your reply, after reading it and goggling around a bit  looks like this issue (if it actually* is* an issue, and not intended behavior) is indeed related to the default keyring or login keyring (I'm not sure they are the same thing) .

Turns out I don't even have a default/login keyring, maybe because I added seahorse after installing Lubuntu (it's not part of the default installation as far as I understand), so when adding this new connection a new keyring containing the wpa secret had been created.

That sounds like the issue that i had.

> I've then deleted both the new connection and this keyring, and re-added the new connection making it available to all users and also checking "automatically connect to this network when available" , and once again I can connect/disconnect without a password.

Now for the inevitable question: is this OK ? Is this somewhat less secure than leaving that option above unchecked, let the network manager create a default keyring and store the password in it, and finally being prompted for unlocking the keyring every time ?

I suspect that depends on how secure your login (seahorse) password is :) It's what i do and as long as no one has access to the machine and your passwords are strong enough then you should be fine.

If you're really worried than you would be using/considering full disc encryption anyway.

> Thinking of it, if the network manager can now connect automatically to this network, its wpa password (which I've typed once at the time this new connection had been added) must be stored somewhere, regardless of appearing in seahorse or not: where is it actually stored now ?

They are stored in files in the directory ```
/etc/NetworkManager/system-connections
```

They are read/writable only by root.

Kind regards

---

### Post by Dennis N on 2015-09-02
I've had this problem several years ago, and found a solution that worked in this thread (there are several solutions suggested):

[http://ubuntuforums.org/showthread.php?t=1690460](http://ubuntuforums.org/showthread.php?t=1690460)

My log book says that the one that worked for me was the simple one in post #9.

---

### Post by cogset on 2015-09-02
Thanks to both of you, looking at that  thread looks like I may have just done what is suggested there in post #9 . It surely is the quickest way to get out of this situation and it was set up like that before adding this new connection -yet it isn't probably the safest option, I reckon.

  Probably what suggested here in the same thread > What you want is all your keys to be under the Login folder. Either move or delete all the keys until only the keys under login are left and only Login folder is left.  Then your login password will automagically unlock you keyring when you logon. would be the best option, that way the wpa password will be stored encrypted in the login keyring and automatically accessed when needed, as opposed to having it  stored unencrypted  or being prompted to type the keyring password every time.

---

### Post by fortworthtechs on 2015-09-03
Check for the content of your key ring in **menu ->System -> Preference -> passwords and Encryption keys**. Here you will find your password in clear text, after you unlocked your key ring. Right click an **element -> properties -> passwords -> show password.**

---

### Post by cogset on 2015-09-03
Are you maybe suggesting that storing the password in the keyring it's somehow even less secure than not using the keyring and let instead the network manager store it in /etc/NetworkManager/system-connections ?

---

### Post by matt_symes on 2015-09-03
Hi

> **cogset said:**
> Are you maybe suggesting that storing the password in the keyring it's somehow even less secure than not using the keyring and let instead the network manager store it in /etc/NetworkManager/system-connections ?

Was this addressed to me ?

If so then no, i was not implying that :)

Kind regards

---

### Post by cogset on 2015-09-03
> Was this addressed to me ?


Hi, no -I was actually replying to fortworthtechs above, sorry for the misunderstanding. 
I shall remember to quote at least a few lines of the message I'm replying to ;)

---

