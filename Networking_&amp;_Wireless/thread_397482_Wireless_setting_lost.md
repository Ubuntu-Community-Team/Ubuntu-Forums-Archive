---
title: "Wireless setting lost"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by siya_kh1983 on 2007-03-30
Hi. I used ver 6.06 but I install 6.10 and have a butifull problem.
I wanna set my Wireless Ip and when I set it , it's not saved :confused:  . 
I could connect to internet with ubuntu 6.06 through this Card. but now I can't becuase when I set IP and click on Ok (I think Ok button) then when I open this config window again , it's reset and no ip set..
What can I do??
by the way, My noteBook have all things to connect and all of them are installed by defualt in Ubuntu and there isn't any problem with drivers becuase the Ubuntu have the drivers...

Please send reply to help me...
thanks

---

### Post by Floppyjoe on 2007-03-30
> **siya_kh1983 said:**
> Hi. I used ver 6.06 but I install 6.10 and have a butifull problem.
I wanna set my Wireless Ip and when I set it , it's not saved :confused:  . 
I could connect to internet with ubuntu 6.06 through this Card. but now I can't becuase when I set IP and click on Ok (I think Ok button) then when I open this config window again , it's reset and no ip set..
What can I do??
by the way, My noteBook have all things to connect and all of them are installed by defualt in Ubuntu and there isn't any problem with drivers becuase the Ubuntu have the drivers...

Please send reply to help me...
thanks
Are you setting your Wireless IP in etc/network/interfaces?
If you use:```
sudo gedit /etc/network/interfaces
```
from the terminal you should be able to permanently set your IP.

---

### Post by siya_kh1983 on 2007-03-30
no, I just find out why, I couldn't set any ip, I set and the ubuntu never tell me any Error, I never set any name for my wirelessNet, so this is my problem and thanx so much for re to me...
thanx

---

