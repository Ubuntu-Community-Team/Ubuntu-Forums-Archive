---
title: "Reading an email header"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by suomalainen on 2011-01-30
Ubunteros,

Could anyone explain to me under what circumstances an email can arrive and be listed in email header as "Received: from unknown"????

I hope the attached pic helps.

Regards,

Suomalainen

---

### Post by CharlesA on 2011-01-30
Probably has to do with the mail server doing a reverse DNS look up.

See [here]("http://www.google.com/#hl=en&sugexp=ldymls&xhr=t&q=received+from+unknown&cp=14&pf=p&sclient=psy&aq=0l&aqi=&aql=&oq=recieved+from+u&pbx=1&fp=2684ce1871ebad80").

---

### Post by suomalainen on 2011-01-30
CharlesA,

Thank you for the feedback and link!

Here is why I asked the question.

I have a friend physically in Russia that through his gmail account sent me an email. When I went to:

[http://www.iptrackeronline.com/header.php](http://www.iptrackeronline.com/header.php)

and pasted in the header it showed, or lead you to believe that the email was sent from within the United States. I thought that to be odd.

I then sent myself an email from my gmail account to another different domain and followed the same process as above. In my case, the system was able to correctly identify that I was in Finland.

I don't know if you can add further light to this but thought to add it.

Thanks again for your support.

Suomalainen

---

### Post by CharlesA on 2011-01-30
Not sure why it would do that unless it's going off the ip address of the mail server and that ip address is located inside the US.

---

### Post by suomalainen on 2011-01-30
That's how it's coming across. The analysis is showing it coming from Google.

---

