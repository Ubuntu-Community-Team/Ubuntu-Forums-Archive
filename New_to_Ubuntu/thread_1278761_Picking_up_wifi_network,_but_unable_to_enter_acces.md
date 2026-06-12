---
title: "Picking up wifi network, but unable to enter access codes"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by C4BL3 on 2009-09-29
I've been trying connect to my new wifi connection, but for some reason it's just not working. The computer is detecting the network and everything, but after I put in the password it won't let me press 'connect'. This is very strange as I have connected to many other networks with no trouble and my roomate's PC has no issues. 

Any advice?

---

### Post by C4BL3 on 2009-09-30
My computer is a Dell inspiron e1405, and I've been reseaching for help and trying everything - no luck :(

---

### Post by starcannon on 2009-09-30
Need more input:

[LIST]
[*]What router?
[*]What security mechanism is it set to? WPA, WEP, WPA2, LEAP, PEAP?
[*]What wifi chipset is in your computer.
[*]Anything else you can think of that may be useful.
[/LIST]
GL

---

### Post by Peter09 on 2009-09-30
This often happens if the key that you have entered does not meet the requirement, in terms of length, for the encryption involved.

---

### Post by C4BL3 on 2009-09-30
Alright, here are my best efforts:

Router is D-link, model DIR-615

Security is WEP 

And well, I don't know how to find my chipset... 

What else would help?

---

### Post by mirado on 2009-09-30
Improper wifi driver?
My Dell M1730's wifi had some troubles after a faulty microsoft/dell update was released 
Turned out to be a corrupt driver update

---

### Post by starcannon on 2009-09-30
The first and likely easiest thing to try, is to switch your security to WPA or WPA2, its better than WEP and these days often more compatible.

If that does not work, come on back and we'll work out what to do next.

GL

---

### Post by C4BL3 on 2009-09-30
Oh, and about the key length - I entered the full 26 character encryption, and it actually won't let me enter any more characters. 

The strange thing is that when I enter an incorrect key of the same length, it actually allows me to click "connect", even though it doesn't allow me to do that when the correct key is entered. I'm so confused!

---

### Post by Marky Mark on 2009-09-30
> **Peter09 said:**
> This often happens if the key that you have entered does not meet the requirement, in terms of length, for the encryption involved.

Just a basic suggestion, try tapping in a few more characters, watch to see if the connect button becomes available.  Different encryption standards require a different number of characters.

Good luck

Beat me to it, sorry.

---

### Post by Marky Mark on 2009-09-30
> **C4BL3 said:**
> Oh, and about the key length - I entered the full 26 character encryption, and it actually won't let me enter any more characters. 

The strange thing is that when I enter an incorrect key of the same length, it actually allows me to click "connect", even though it doesn't allow me to do that when the correct key is entered. I'm so confused!

Does that incorrect key contain different types of characters?  Like upper/lower case and numbers?

---

### Post by C4BL3 on 2009-09-30
> **starcannon said:**
> The first and likely easiest thing to try, is to switch your security to WPA or WPA2, its better than WEP and these days often more compatible.

If that does not work, come on back and we'll work out what to do next.

GL
Alright, next I'll try switching to WPA or WPA2 - though I have to wait until tomorrow because the router is my landlord's and he's sleeping! 

Thanks a bunch guys

---

### Post by C4BL3 on 2009-09-30
> **Marky Mark said:**
> Does that incorrect key contain different types of characters?  Like upper/lower case and numbers?
No - both keys are composed of simple numbers and lower-case letters. The main difference seems to be that the incorrect key that my compy accepts has more numbers, less letters, and is in a totally different pattern than the 'correct' key

---

### Post by Peter09 on 2009-09-30
mmm - maybe your key is hexadecimal 0-9 and A-F (a-f), those would be the only valid letters and numbers that you could use in the key.

---

### Post by C4BL3 on 2009-10-13
Hm.... maybe that's it? the access code is all hexadecimal except that there's one 'h' in it, and I'm not sure why. It doesn't seem to be a problem with all my roommates who use windows, but I guess Ubuntu won't let it fly.

How do I fix this? do I need to make my landlords get a new code?

---

### Post by Peter09 on 2009-10-13
Normally a WPA key is an alphanumeric phrase such as

> this is a keyphrase

when that key is entered the software converts it to a HEX string - which is what you see displayed in the keybox. 

I suspect you are entering the HEX string into the box that will convert it to the Hex key. (Its being converted again). That is why is not working.

What does your landlord tell you the key is - a HEX string or the alphanumeric phrase.

---

### Post by 3rdalbum on 2009-10-13
Is it a 26-character WEP key, or a 26-character WEP password? Keys are hexidecimal, and there's no H in hex.

---

### Post by C4BL3 on 2009-10-16
Finally! Turns out the key I was given by my landlord must have been wrong - I replaced the 'h' with all available options until it finally worked. Sorry for the stupid problem, and thanks a bunch for the help!

---

