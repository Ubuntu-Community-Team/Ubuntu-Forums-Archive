---
title: "Wireless not accepting WEP key."
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by billdotson on 2008-06-19
I have gotten Ubuntu 8.04 to see my Broadcom wireless (Dell Inspiron 1521) with the help of this site: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc")

I did the permanent workaround for the Hardy bug as well.

However, every time I try to connect to the wireless internet and enter the WEP key it does not accept it.  I know that this key is correct as I looked at it in my router page at the internal address 192.168.1.254.  Could anyone please provide some assistance.

---

### Post by lisati on 2008-06-19
I was caught out a couple of times while I used WEP by entering the key as 64-bit ASCII when I should have used HEX, or ocasionally mixing up 64 bit & 128 bit.......

Just a thought.

---

### Post by Fingel on 2008-06-19
This might sound strange but I had the same problem. I converted the password to hex and then used the option to enter the pass as hex, and it worked. Try this site:
[http://www.dolcevie.com/js/converter.html](http://www.dolcevie.com/js/converter.html)

---

### Post by billdotson on 2008-06-19
I tried those things and they did not work.  However, I tried just entering the 26 character (128 bit) passphrase and it looked like it had connected to the wireless network as it was showing the connection bars but I still could not ping any addresses or access my router page.  About every 30-60 seconds it would ask me for the passphrase again so I am thinking that it just wouldn't keep it remembered.  That being the case I tried to do a manual connection and enter the SSID, the passphrase, the security type for the connection and set the wireless connection to Automatic (DCHP).  That didn't appear to do anything as the connection bars did not show up at all then.  This is a shame, I was trying to fix my mom's computer from her mess of an OS installation of Vista and then the wireless isn't going to work properly without a fair amount of troubleshooting.

---

### Post by billdotson on 2008-06-27
No response?

---

### Post by chili555 on 2008-06-27
Does your router use the Authentication Type 'Shared Key' or "Open?' Did you select correctly when you entered your 26-character hex key?

---

### Post by billdotson on 2008-06-28
Open 26 character passphrase.  I entered it correctly.

---

### Post by chili555 on 2008-06-29
> it would ask me for the passphrase again Are you entering this in 'WEP Passphrase' or 'WEP 128-bit Hexadecimal?' I never have any luck with passphrase and connect easily with Hex.

---

### Post by billdotson on 2008-06-30
I am certain that I have tried the HEX, ASCII and normal passphrase.  The laptop's power actually ruptured or something so it is unusable at the moment.  I am pretty sure that I tried the 26 character passphrase in all three types of input, then tried the passphrase when it was converted to HEX, and tried it when converted to ASCII.  Surprisingly enough, the computer had no issues using wireless in Vista.

---

### Post by chili555 on 2008-06-30
> Open 26 character10 or 26 characters is Hex. 5 or 13 is ASCII. Don't even ask me about 'passphrase;' first of all, as far as I know, every manufacturer has a different algorithm to convert a password to a key. Second, from *man iwconfig:*>  key/enc[ryption]
              Used to manipulate encryption or scrambling  keys  and  security mode. To  set  the  current  encryption key, just enter the key in hex digits as XXXX-XXXX-XXXX-XXXX or XXXXXXXX.  To set a  key  other than  the  current  key,  prepend  or  append [index] to the key itself (this won’t change which is the active key). You can also enter  the  key  as  an  ASCII  string  by  using the s: prefix. **Passphrase is currently not supported.**I don't understand what, where or why Network Manager is doing with 'passphrase.'

---

### Post by billdotson on 2008-06-30
This doesn't sound good.

---

### Post by Mackintire on 2008-07-03
This is the fix for your problem when you have the Intel 3945  you should be able to adapt it to your broadcom card.


1. sudo modprobe -r iwl3945
2. create a file named iwl3945 in /etc/modprobe.d
3. in that file enter the following entries
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
4. sudo modprobe iwl3945
5. sudo ifconfig wlan0 up 

I think that editing the file again and deleting the "options iwl3945 disable_hw_scan=1" line should do the trick. Maybe someone else can confirm this. You will have to run 
Quote:modprobe iwl3945 

again, after you do the changes.

---

### Post by chili555 on 2008-07-03
> **Mackintire said:**
> This is the fix for your problem when you have the Intel 3945  you should be able to adapt it to your broadcom card.


1. sudo modprobe -r iwl3945
2. create a file named iwl3945 in /etc/modprobe.d
3. in that file enter the following entries
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
4. sudo modprobe iwl3945
5. sudo ifconfig wlan0 up 

I think that editing the file again and deleting the "options iwl3945 disable_hw_scan=1" line should do the trick. Maybe someone else can confirm this. You will have to run 
Quote:modprobe iwl3945 

again, after you do the changes.Does ndiswrapper permit disabling hardware scan? *modinfo ndiswrapper* doesn't look like it. I will be shocked if he can adapt this to his ndiswrapper driven Broadcom.

---

