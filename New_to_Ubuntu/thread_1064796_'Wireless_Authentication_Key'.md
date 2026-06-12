---
title: "'Wireless Authentication Key?'"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by jmedoro on 2009-02-09
Just installed Ubuntu 8.10 to dual boot with Windows XP...i'm trying to connect to my wireless network, and i'm being asked for a 'wireless authentication key.' 

The only thing i ever remember doing with Windows is using my username and password. It seems to recogize my username already (it tells me i need this key to log in to the particular username), but i dont see where i would enter my password.

Sound familiar? I have no idea what it needs and where to get it...

---

### Post by JustANewb on 2009-02-09
I think this is just your password for your account.  To my knowledge, Intrepid Ibex stores your wireless keys in your keyring and requires a password to open your keyring.  The password is just the password you use to login and is only asked for if your computer is set to auto-login.

To stop this, go to Applications -> Accessories -> Passwords and Encryption Keys.  Edit -> Preferences then in the box, highlight the login one and Change Unlock Password.  Type in your old password and leave the new one blank...

Let me know if this works for you.

---

### Post by jmedoro on 2009-02-09
thanks, I will try.

I tried plugging in my normal password, but this field seems to require a long alpha-numerical key (the 'connect' button remains grayed out until i type in a password of about 20 characters, much longer than the password i made for myself).

also, it is giving me some sort of password by default, which is shown as black bullets (as it is whenever you want a password you are typing to be hidden). 

there is a 'show password' button which shows this default password behind the bullets, and it looks like a long serial number.

I'm just providing details in case this further clarifies anything.

---

### Post by Doug11 on 2009-02-09
This is probably the password for your network. If you have an open network, which is not really recommended, there should be a small dropdown list with this option. You would enter your SSID, which is your network name IE, "John's Network" and whoever wishes to connect to "John's network" will have to enter this key or password before connection is permitted. Hope this clears things up a little. Only if this is not your keyring password as mentioned above.

---

### Post by jmedoro on 2009-02-09
i did the following in Windows XP:

i disabled my wireless so as to sign back in, to see if it asks me for a wireless key. To do this, I clicked 'use windows to manage WiFi' on my Intel ProSet Wireless manager. (the alternative option is to use 'Use Intel ProSet Wireless to manage WiFi).

i tried getting back online, and a window popped up saying 'This network requires a network key, also known as a WEP or WPA key.'

when i typed in the password that my roommate and I (the only ones on the network) use, it says:

'the network password needs to be 40 bits or 104 bits depending on your network configuration. this can be entered as 5 or 13 ascii characters or 10 or 26 hexadecimal characters.'

i do not know this key, so i set it back to 'use proset to manage wifi,' selected my profile name, and was signed back in.
----------------------------------

so i guess this key is the same one i am being asked for when going through linux. i only went in through Windows to make sure the same thing is happening, so as to rule it out as purely a linux issue. bottom line is i think the key is different from any password i have, and that is what i am confused about.

please help me clear this up, my Apple using roommate keeps laughing as i drag mout the ethernet cable to i can come here and ask questions (thinking he is a badass for having a Mac and not using Windows), and i want to eventually put him in his place.

---

### Post by newbee70 on 2009-02-09
> **jmedoro said:**
> thanks, I will try.

I tried plugging in my normal password, but this field seems to require a long alpha-numerical key (the 'connect' button remains grayed out until i type in a password of about 20 characters, much longer than the password i made for myself).

also, it is giving me some sort of password by default, which is shown as black bullets (as it is whenever you want a password you are typing to be hidden). 

there is a 'show password' button which shows this default password behind the bullets, and it looks like a long serial number.

I'm just providing details in case this further clarifies anything.


Sounds like when your router was set-up you used a pass-phrase for either a wep or wpa security key,enter your router pass phrase and it should accept it.

---

