---
title: "Evolution Error"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by eliza60 on 2009-10-14
Hi,
Have just received my new Dell Mini 10 with Ubuntu.
Have tried to set up my email account using Evolution but keep getting the following error message : 

"Error while performing operation.
Could not connect to 25: invalid argument."

I have always been a Windows person using Incredimail (dont't know if this has anything to do with it!) I am using the same settings as I always have.

Does anyone have any suggestions?
Also tried to use Thunderbird but that just says:

"there are no new messages on the server"

I know that there are new messages though!

Can't work out what I'm doing wrong as I've never had problems with emails before!

---

### Post by dvlchd3 on 2009-10-15
It sounds like something isn't configured properly.  As I'm not sure who hosts your email server, I can't give any complete instructions.

If you use a generic free email service (Gmail, Yahoo, Hotmail, etc) these services usually have instructions on how to configure your email client.  Make sure they are set exactly.  I know that with Gmail, you have to enable SSL encryption to authenticate yourself when sending and receiving messages.  Other email hosts have different requirements depending on their security consciousness, configurations, etc.

---

### Post by Razmear on 2009-10-15
Does your ISP block port 25 for mail? 
Bellsouth does that so you have to use an alternate port to get mail from a non-Bellsouth server. Port 587 works as an alternate for many ISPs, your mileage might vary tho. 
You should be able to switch it in the account settings. 

eb

---

### Post by wojox on 2009-10-15
What email service are you trying to connect to?

---

### Post by eliza60 on 2009-10-15
Well, I'm in Australia and my host email server is Bigpond. For incredimail I use ports 110 and 25 and have no problems! Does using Ubuntu instead of Windows make any difference?

Thanks for your replies but I still get the same error message on Evolution after trying your suggestions. Might contact Bigpond and see what they can suggest!

---

### Post by eliza60 on 2009-10-15
Thanks again for your suggestions but in the end I searched through Bigpond and decided to change my password then started from scratch and both Evolution and Thunderbird work!
Now to decide which one is best!!:KS

---

