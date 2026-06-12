---
title: "Fujitsu Siemens C 1020, ASUS WL 107g wireless Lan Card"
date: 2014-10-13
forum: Networking &amp; Wireless
---

### Post by urbain3 on 2014-10-13
Hi guys,

Let me introduce myself:  I'm urbain, and I live in Belgium.

I'm making my first steps into the linux world.

Why ?  Well, I have an old Fujitsu Siemens C 1020 lifebook running on windows XP, and I wanted to try it out on linux.

System specs: Pentium 4, 2 Gigs Ram, 25 Gb HD.

I have also an ASUS WL 107g wireless Lan Card Adaptor, that worked fine on XP.

But here's the story:

I installed Lighthouse puppy linux latest version, PCLinuxOS latest version, and now Lubuntu 14.x with all the updates.

They all 'see' the ASUS card, but something strange happens:  when I connect to the Internet, exactly after 30 seconds Lubuntu 'hangs' _with the Scroll lock light and the Caps lock light both blinking simultaneous_.  I have to remove the ASUS and reboot, and then the system works OK, until I plug in the card.... and then it happens again exactly after 30 secs...

Lighthouse and PCLinuxOS do exactly the same !

I've read some threads about wifi problems with this kind of card, that uses the RT2560 chipset....

For my first steps into the linux world, this sucks![B]:mad:

[/B]I really would appreciate the help of the professionals on the forum
Thx.

---

### Post by davit2 on 2014-10-13
hi, 
try it
$  sudo apt-get install b43-fwcutter firmware-b43-installer

---

### Post by urbain3 on 2014-10-13
Can you give me some more info please ?

Is this a command that I have to type in the command box ?

---

### Post by Vladlenin5000 on 2014-10-13
> **urbain3 said:**
> Can you give me some more info please ?

Is this a command that I have to type in the command box ?

Exactly :p

---

### Post by Hadaka on 2014-10-13
@davit2,,,,Why would ?
```
sudo apt-get install  firmware-b43-installer
```
have anything to do with a Realtec RT2560 wireless card?
b43 is a broadcom card.
a quick search shows me RT2560 uses the rt2500pci driver.
To verify your card please do
```
lspci -nn | grep 0200
```
or perhaps run and post the wireless script.

---

### Post by Vladlenin5000 on 2014-10-13
Post #5 is entirely correct and I'm sorry I didn't checked before which chipset the Asus card has. It should be the RT2560, from **Ralink** (now Mediatek), not Realtek or "Realtec" :lolflag:... It doesn't really matter anyway.
RT2560 is natively supported since many years ago and this > They all 'see' the ASUS card just confirmed it.
Now, carefully reading again your OP, I suspect you have an hardware problem. Such card is very old so don't expect miracles. You said it **worked** in XP... So, how long ago that was? The card might have become defective meanwhile.

Anyway, just in case, please follow the suggestions of the previous post. Running the wireless_script particularly might give us a clue about what's happening.

---

### Post by urbain3 on 2014-10-14
> You said it **worked** in XP... So, how long ago that was? The card might have become defective meanwhile.

Probably not, because I ran it on the XP harddisk yesterday, and it works like hell.

I've done some reading, and apparantly the RT2560 has some driver issues under linux, but nobody has come with a solution yet.

Other wifi cards with the same chipset show similar problems on all kinds of portable pc's... so what I'm looking for is a sort of driver patch, but the latest driver I found is already 8 years old and doesn't do the job.

Would a more recent wifi usb thing do the job, then I could buy a new one.... or on the other hand return to windows....;)

---

### Post by Vladlenin5000 on 2014-10-14
There are many USB WiFi that work perfectly OOTB. I recently suggested one based on Realtek 8191SU and in the same thread other user also suggested 8188CUS which is now working great after a recent kernel update. Many Ralink based ones (now Mediatek) are also plug&play, many Atheros based likewise and almost all Intel based usually work.

---

