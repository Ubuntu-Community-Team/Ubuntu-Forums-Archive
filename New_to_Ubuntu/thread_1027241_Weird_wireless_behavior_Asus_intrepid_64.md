---
title: "Weird wireless behavior Asus intrepid 64"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by dnagorcka on 2009-01-01
Hello,
I've installed intrepid 64bit on an Asus machine with a P5k-E motherboard which has built in wireless. Wireless works but the signal will not go above 15% and it can take up to 30 seconds before a download will start or a page will load. 

lsusb shows this 
Bus 004 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter 

Under Windoze i get about 85% and its fast,i also tried with my notebook (intrepid 32bit) works perfectly.
I have tried the windows driver wrapper thing before but only succeeded in crashing the machine maybe someone could run me though how to do it properly.

Please help this is driving me nuts!
cheers

---

### Post by dnagorcka on 2009-01-01
bump

---

### Post by 3rdalbum on 2009-01-01
This is a known bug (has been reported to Launchpad) but as far as I know there has not been a definitive fix for it.

What you can do is install a different wireless driver, which is actually MUCH better than the kernel's Realtek wireless driver has ever been; but unfortunately doesn't support WPA.

This web site explains how to do it: [http://zenzike.blogspot.com/2008/11/wireless-woes.html]("http://zenzike.blogspot.com/2008/11/wireless-woes.html")

Unfortunately you'll be stuck with the less secure WEP encryption, but you will get good speeds and excellent range, as well as improved reliability. Save a copy of the page, because if you download an updated kernel from the Update Manager it will reverse your changes.

---

### Post by dnagorcka on 2009-01-01
Thanks for the link will try tomorrow, im using WEP anyway. 
thanks again

---

### Post by dnagorcka on 2009-01-01
I've installed the old driver the reception is now much better although it jumps around a bit it seems to stay between 60 and 80%. Still can take a little while before it'll start down loading though don't know whats going on there.
Hopefully this gets fixed soon anyway works better than it did.
thanks

---

### Post by noblerabbit on 2009-05-06
is there any fix to this yet??

im using jaunty on the p5k-e wireless built in.

reverting to WEP is not an option as the other people in the house use this and they would not want a less secure encryption.

my wireless is TERRIBLE. like previously mentioned i get 10-15% signal (had over 50% in vista) and it regulalry cuts out, and forgets the key. so when im watching a film it pops up its disconnected and the password prompt pops up and i have to stop the movie and re enter it. and even then sometimes it doest connect, just tries to, and then asks for WPA again... :(

it seems to cut out more often when im downloading something. therefore, just browsing for short periods of time is ok, but i get disconnected during IM conversations, and it takes ages to download stuff.

so now im paying for a 20mb connection that i hardly get any use out of :'( ;_;

---

### Post by Scunnered on 2009-05-06
I dont know exactly what my Atheros AR242x802.11 a/b/g is as a wifi card. What I can say is that having updated to Jaunty my connection is running at full steam ahead.  The connection was immediately made and it has not dropped off since I updated.

Like you I have an Asus system mine being a X51L so it might be worth your while investigating the Atheros AR242 for your needs

Hope this assists

---

