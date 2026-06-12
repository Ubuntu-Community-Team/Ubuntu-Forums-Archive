---
title: "Broadcom wifi in laptop keeps dropping out"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by ELD on 2014-06-06
So I have a new laptop for work with Ubuntu on and I had to install the Broadcom drivers to even get the wireless to show up, the problem however is it drops out a lot for no apparent reason.

What's my best course of action?

---

### Post by varunendra on 2014-06-07
> **ELD said:**
> What's my best course of action?

..post the report of 'wireless_script' : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by ELD on 2014-06-07
That gives me a blank file on each run :(

---

### Post by varunendra on 2014-06-07
I've heard that many times now, although each time the users come back with a success report.. not sure if it's a user mistake or a script bug.

May I see the terminal output please? Plus the output of (from the same terminal) -
```
ls -l wireless*
```

---

### Post by ELD on 2014-06-07
I did it exactly as you asked, here's the output:
liam@liam-Lenovo-G500 ~ $ ls -l wireless*
-rw-r--r-- 1 liam liam     1 Jun  7 17:00 wireless-info.txt
-rwxr-xr-x 1 liam liam 15521 Jun  7 17:00 wireless_script

---

### Post by Hadaka on 2014-06-07
hi, please open a terminal ctrl/alt/t and do..
```
cat wireless-info.txt
```
*If there is any data in that file...COPY and
paste here.
thanks.

---

### Post by ELD on 2014-06-07
Nothing like I said the file is empty.

---

### Post by ELD on 2014-06-07
FYI i just ran it again and terminal shows this error:
sed: -e expression #1, char 311: unknown command: `V'

But the script still claims it goes though regardless which I guess is the issue.

---

### Post by varunendra on 2014-06-07
Maybe a resulting character is confusing the script. Please try the regular one, linked to "Wireless Script" link in my signature.

---

### Post by ELD on 2014-06-07
One the linked worked: [http://pastebin.com/8rbTs0XT](http://pastebin.com/8rbTs0XT)

---

### Post by varunendra on 2014-06-07
Quick post before retiring to bed for the night - Please change the encryption type in the router to pure WPA2 with AES (CCMP). Currently it is using WPA/WPA2 mixed mode which can increase the problem if not the problem itself. Reboot the router after saving the change.

---

### Post by ELD on 2014-06-09
That made no difference it still sadly keeps dropping out :(

---

### Post by varunendra on 2014-06-11
Can we see a fresh report with the changes applied please?

**PS:**
I may not be able to help further on this due to lack of time. If anyone watching the thread has any ideas, please jump in!

**PPS:**
If you remove the hyphen (-) from the AP name (SSID) in the router, let's say replace it with underscore (_), does the script that I suggested earlier work? Just trying to sort out its bug.

---

### Post by ELD on 2014-06-16
I cannot change the ssid as it's not my router i'm using right now i'm afraid.

Here's a fresh script output: [http://pastebin.com/ZN2cWd6t](http://pastebin.com/ZN2cWd6t)

Wireless still drops out a lot.

---

### Post by varunendra on 2014-06-17
The current AP which the report shows in use is again using WPA/WPA2 mixed mode with TKIP. Like I said before, it adds to the problem if not a problem itself. Unless you have some Jurassic-age device that can't support WPA2 and really needs WPA(1), it is highly recommended to use WPA2-PSK with AES (CCMP), regardless of whether it seems to help or not.

Additionally, try explicitly defining your country code for RegDomain settings. That is, adding the country code to /etc/default/crda file. A one liner for doing that -
```
sudo sed -i '/^REG.*=$/ s/.*/&**[COLOR="#0000CD"]GB[/COLOR]**/' /etc/default/crda
```
..assuming you are in England (country code 'GB'). If not, change the country code accordingly, refer to this table : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

The change will be effective after a reboot.

---

### Post by ELD on 2014-06-19
Using that command so far seems to have fixed it without changing the router settings, any idea why that might have fixed it setting the country code? :S

---

### Post by varunendra on 2014-06-20
> **ELD said:**
> Using that command so far seems to have fixed it without changing the router settings, any idea why that might have fixed it setting the country code? :S

That command tells the system to use wifi frequency settings compatible to those allowed in Britain. The Regulatory Domain settings for 'GB' are -
```
country GB:
	(2402.000 - 2482.000 @ 40.000), (N/A, 20.00)
	(5170.000 - 5250.000 @ 40.000), (N/A, 20.00)
	(5250.000 - 5330.000 @ 40.000), (N/A, 20.00), DFS
	(5490.000 - 5710.000 @ 40.000), (N/A, 27.00), DFS
```

..while the earlier (defaulted to '00') settings were -
```
country 00:
	(2402.000 - 2472.000 @ 40.000), (3.00, 20.00)
	(2457.000 - 2482.000 @ 20.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
	(2474.000 - 2494.000 @ 20.000), (3.00, 20.00), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170.000 - 5250.000 @ 40.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
	(5735.000 - 5835.000 @ 40.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
```
..so I can only guess that maybe your router is using a frequency setting that keeps falling out of the ranges/limitations enforced by the defaulted (00) settings. Fixing the regdomain setting to 'GB' matched it with the router's frequency range.

I suggest you test the connection for a couple of days, and if it proves to be stable, please mark the thread as [SOLVED].

---

