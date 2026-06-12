---
title: "WEP key convertion differences"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by studentsupport on 2008-10-10
Hello,
I got a question regarding converting ASCII to WEP key.
The first way is simply converting ASCII to HEX:
UBUNTU - 75:62:75:6E:74:75
Another is making of a 64 bit WEP key of any length of ASCII expression:
UBUNTU - E69959C009
reference: [http://www.wepkey.com/](http://www.wepkey.com/)

The question itself: why there is several ways of converting ASCII to WEP? Could anyone explain the second way of conversion and if it is one-way or E69959C009 key could be recursively converted to UBUNTU?
Thank you

P.S. Sorry for double-post, did not know which forum was the right to post.

---

### Post by andrewc6l on 2008-10-10
The second way is just a way of generating a 64-bit WEP key from an arbitrary string. I'd guess that's mostly because when you ask someone to come up with 8 random bytes, they're likely to do something less secure, like using ASCII characters :-)

If you use ASCII characters, then attackers only have to look in the range 40-7F instead of 00-FF, which means a search space of 64^8 instead of 256^8.

Using a generator will typically apply a cryptographic function to the text. These functions are usually not something that can be reversed. However, if you want to be very sure, don't use an online generator - instead, go to a command line and type:

md5sum
<enter your secret password here>
CTRL-D

Then take the first 8 bytes from the output as your WEP key.

---

