---
title: "Neil the newbies wireless woes - stuck at passphrase"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Neil_The_Newbie on 2008-02-20
Please help!

I have just purchased a laptop and have set it up as a dualboot with Vista and the latest version of Ubuntu. I have booted it with Ubuntu for the first time but cannot get the wifi to work. It can see my router and other wireless networks. I am stuck at the passphrase bit. My laptop spec is here:
[http://www.comet.co.uk/cometbrowse/product.do?sku=435848&tab=specification#spec](http://www.comet.co.uk/cometbrowse/product.do?sku=435848&tab=specification#spec)

In device manager the wifi card is shown as Intel Pro/Wireless 3945ABG Network Connection

My router is a BT British Telecom wifi router (the white box type – i'm from the UK). On the router page it says:

New stations are allowed automatically
WEP Key Length:   64 bit
WEP Encryption Key: 3b845f97e4

So...When I boot up Ubuntu and i click on the 2computers it shows a number of wireless networks (including mine). I select my wireless network and it comes up with the wireless key required. Despite several attempts i cannot get it to work. I'm a bit of a newbie on the technical side of things! What should i be doing?

---

### Post by dca on 2008-02-20
On your router, does it offer to have the key in one of four or so areas?  1, 2, 3, or 4?  If so, make sure it's in 1.  Also, try switching (if possible) on your router from a WEP Hex key to an 64bit ASCII WEP and see if by doing this the laptop connects that way...

---

### Post by Neil_The_Newbie on 2008-02-20
Sorry - i'm a total beginner on this. This is the screen i have:

---

### Post by unoodles on 2008-02-20
I had that problem once so I entered my password using WPA passphrase and it worked perfectly

---

### Post by Neil_The_Newbie on 2008-02-20
the choices i have are
WEP 128-bit Passphrase
WEP 64/128-bit Hex
WEP 64/128 Bit ASCII
Leap

but ive tried entering 3b845f97e4 as the key but it doesnt work and after a while it takes me back to the same screen.

---

### Post by Neil_The_Newbie on 2008-02-20
yep... i'm stumped! anyone any ideas?

---

### Post by nixscripter on 2008-02-20
The first thing I noticed is that the key is not 64 bits, is it? If it's in hex, 64 bits = 8 bytes = 16 hex characters.

There are 10 in that string. Perhaps your router is stupidly refusing to set the key to that, or even stupider, the key is being padded invisibly with zeroes at one end or another. That would make it incorrectly guess at the key if Ubuntu does something different.

---

### Post by Neil_The_Newbie on 2008-02-21
still stumped!! should wifi be this hard?

---

### Post by dca on 2008-02-21
Where it says WEP encryption key on that image you ahowed us, does it allow add'l entries after the passkey.  More to the point can it go an add'l six characters?

---

### Post by Dennis on 2008-02-21
If you disable the encryption (for a VERY short time) can you connect?

---

### Post by Neil_The_Newbie on 2008-02-21
No it doesnt. on my other pc that is hard wired to my router I get the message

'Vaildation failed for (WEP key)
Valid key lengths are (5 ASCII) and (10 HEX) for 64 BIT, 13 (ASCII) and 26 (HEX) for 128 BIT encryption.

Please connect and try again.'

---

### Post by Neil_The_Newbie on 2008-02-21
if i disable encryption it still doesnt connect

---

### Post by dca on 2008-02-21
After you disable encryption in router does it restart itself?  After it restarts itsellf you can still see the Access Point in your list of available wireless networks?

---

### Post by Neil_The_Newbie on 2008-02-21
yes i can still see it available. i have searched the net for a solution to this but can't seem to get anywhere.

---

### Post by Neil_The_Newbie on 2008-02-21
still no joy. free router anyone? :)

---

### Post by Neil_The_Newbie on 2008-02-21
](*,)

---

### Post by Neil_The_Newbie on 2008-02-22
well if the bt homehub doesn't work can anyone recommend a router that will?

"We listen to what our customers tell us they need and we're developing innovative new solutions as part of our dedication to delivering excellent service."
Matt Bross
BT Group chief technology officer

:confused:

---

### Post by keith7 on 2008-03-03
I am getting exactly the same problem. I think it must be to do with the key index which I will change and post again.

---

