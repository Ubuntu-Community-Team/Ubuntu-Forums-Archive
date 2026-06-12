---
title: "[SOLVED] Wireless Tools"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-05-04
Hi,
Is there software available for:

[LIST=1]
[*]A wireless key view - so that you can find your wireless WEP key
[*]A wireless key generator - to generate new wireless keys.
[/LIST]

Are there commands that can do the above?

Thanks.

---

### Post by Paris Heng on 2008-05-04
> **Rytron said:**
> Hi,
Is there software available for:

[LIST=1]
[*]A wireless key view - so that you can find your wireless WEP key
[*]A wireless key generator - to generate new wireless keys.
[/LIST]

Are there commands that can do the above?

Thanks.

Hi, you want to find your own wireless key or other people wireless key? If your, just see in your configuration file. 

For generating the WEP key, this is the Browser based generator,

[http://www.andrewscompanies.com/tools/wep.asp]("http://www.andrewscompanies.com/tools/wep.asp")

---

### Post by Rytron on 2008-05-04
> **Paris Heng said:**
> Hi, you want to find your own wireless key or other people wireless key? If your, just see in your configuration file. 

For generating the WEP key, this is the Browser based generator,

[http://www.andrewscompanies.com/tools/wep.asp]("http://www.andrewscompanies.com/tools/wep.asp")

Just my wireless key. That web site link is awesome. Just curious about the section:

[B]Custom WEP Key	  	 

Custom Phrase 	

Character Count.[/B]

What does the above section mean?

Thanks.

---

### Post by spd106 on 2008-05-04
The custom section allows you to generate a key based on a phase of your choice rather than create a random key. This makes it less secure, but easier to remember.

Just type in a phase and it will tell you the hex version. It also reminds you of the number of characters that are allowed (5/13/16/29). If you don't use one of them then the key won't work properly. 

Most of the time you can only use 5 or 13. Most commodity hardware won't support key depths greater than 128-bit, particularly as they weren't part of the original WEP spec. i.e. you're relying on proprietary extensions.

---

