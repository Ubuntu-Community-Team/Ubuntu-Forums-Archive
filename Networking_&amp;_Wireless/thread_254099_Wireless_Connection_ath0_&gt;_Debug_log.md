---
title: "Wireless Connection ath0 &gt; Debug log?"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by gmillikan on 2006-09-09
ath0 with Atheros AR5212 802.11abg NIC shows as active and is enabled and is even picking up the correct network name (ESSID) however, it is not able to connect. How can I view debugging information/log?

I know I'm entering correct key type (plain ASCII) and WEP key because this is a dual boot machine with Windows XP Pro and the wireless is working just fine on the Windows side.

Your thoughts? (madwifi module 2.6.15.11-3 is loaded)

[http://www.t1shopper.com/](http://www.t1shopper.com/)

---

### Post by wieman01 on 2006-09-09
Can you try Hexadecimal rather than plain Ascii? Would that make a difference? If not, we have to try something else...

---

### Post by tturrisi on 2006-09-09
Don't use plain text, use hex.  If no joy put a hypen after every 4th digit:
abcd-efgh-ij

---

### Post by gmillikan on 2006-09-16
The wireless access point is set to use a "64-bit" "shared key" and I tried a hexadecimal key ("4217661300") instead of an ASCII key - no luck.  Then I tried the hyphen trick ("4217-6613-00") but no success.  Then I set the access point to "Open System" with no encryption and deleted the key out of Ubuntu and it connects and works great!  Of course I cannot run my AP wide open.  So I flipped the AP to "Open System/Shared Key" and choose a 64-bit key and entered it into Ubuntu as "4217-6613-00" and it works!  So it seems that Ubuntu is very sensitive to the access point's radio mode.  Now, to get WPA-PSK working... :-)

---

### Post by wieman01 on 2006-09-16
WPA... There is a solution for WPA1 for Atheros:

[http://www.ubuntuforums.org/showthread.php?t=225290&page=11]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11")

WPA2 will be slightly different, you can try this but if you need help, we can guide you through it. 

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Try the first link and see how it goes.

---

### Post by gmillikan on 2006-10-01
I'm so happy it working now scared to try anything else.  Once there's a GUI for doing TKIP then I'll give it another try.  Doing stuff command line in text files seems dicey to me but then I'm a Windows junkie...  ;-)

Thank you all for your help on this.  I'm very impressed with Ubuntu.

---

